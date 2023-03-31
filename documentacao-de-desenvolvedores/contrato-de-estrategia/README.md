---
description: Tradução feita a partir da atualização de fevereiro de 2023
---

# Contrato de Estratégia

[Contratos de Estratégia](https://github.com/beefyfinance/beefy-contracts/tree/master/contracts/BIFI/strategies) são o principal impulsionador do modelo de investimento da Beefy, que facilita a autocomposição das tokens de farm recompensadas. O processo da Beefy tem três etapas fundamentais: (1) depósito das tokens nas farms relevantes; (2) coleta de recompensas; e (3) troca de recompensas por mais tokens de depósito e reinvestimento dos lucros.

Cada contrato de estratégia depende, em última instância, de um [contrato-de-cofre.md](../contrato-de-cofre.md "mention") para o capital que eles utilizam, e não têm nenhuma interação direta com usuários comuns. Os contratos de cofre e estratégia são mantidos separados para isolar quaisquer riscos na estratégia dos depósitos dos usuários.

## Dependências

Todas as estratégias da Beefy dependem de uma série de dependências e interfaces que são importadas para o contrato de estratégia na implantação. As principais dependências, que permitem que a estratégia herde uma gama de funcionalidades, são:

* o [contrato-stratfeemanager.md](contrato-stratfeemanager.md "mention") e;
* o [contrato-gasfeethrottler.md](contrato-gasfeethrottler.md "mention").

## Interfaces

As principais interfaces que permitem que a estratégia interaja com contratos de terceiros são:

* **a interface de contrato do roteador** - que permite trocas entre as diferentes tokens envolvidas no processo de autocomposição (por exemplo, IUniswapRouterETH.sol);
* **a interface do contrato de pool de liquidez** - que é a pool subjacente ao qual nossos cofres fornecem liquidez e que as farms são construídas sobre (por exemplo, IUniswapV2Pair.sol) e;
* **a interface de contrato chef** - a farm que está emitindo recompensas por fornecer liquidez (por exemplo, IMiniChefV2.sol).

## Funções View

### balanceOf() / balanceOfWant()

Verifica a quantidade da token de farm subjacente (ou "want") armazenada na estratégia. Devolve a quantidade específica de tokens.

```solidity
function balanceOf() public view returns (uint256) {
    return balanceOfWant() + balanceOfPool();
}

function balanceOfWant() public view returns (uint256) {
    return IERC20(want).balanceOf(address(this));
}
```

### balanceOfPool()

Verifica a quantidade de tokens de farm subjacente (ou "want") armazenada no contrato chef. Devolve a quantidade específica de tokens.

```solidity
function balanceOfPool() public view returns (uint256) {
    (uint256 _amount, ) = IMiniChefV2(chef).userInfo(poolId, address(this));
    return _amount;
}
```

### rewardsAvailable()

Verifica a quantidade de recompensas pendentes detidas pelo contrato do chef capaz de ser reivindicada pelo contrato estratégico. Devolve a quantidade específica de tokens.

```solidity
function rewardsAvailable() public view returns (uint256) {
    return IMiniChefV2(chef).pendingSushi(poolId, address(this));
}
```

### callReward()

A maioria das estratégias inclui uma função _callReward()_, que é usada para determinar a quantidade de tokens de recompensa "nativas" disponível para o chamador da _harvest()_.

```solidity
function callReward() external view returns (uint256) {
    uint256 pendingReward;
    address rewarder = IMiniChefV2(chef).rewarder(poolId);
    if (rewarder != address(0)) {
        pendingReward = IRewarder(rewarder).pendingToken(poolId, address(this));
    }
    uint256 outputBal = rewardsAvailable();
    uint256 nativeOut;
    if (reward == native) {
        nativeOut = pendingReward;
    } else if (pendingReward > 0) {
        uint256 poolLength = params.rewardToNative.path.length;
        uint256 amount = pendingReward;
        for (uint i; i < poolLength;) {
            bytes memory data = abi.encode(routes.rewardToNative[i], amount);
            amount = IBentoPool(params.rewardToNative.path[i].pool).getAmountOut(data);
            unchecked { ++i; }
        }
        nativeOut = amount;
    }
    if (outputBal > 0) {
        bytes memory data = abi.encode(output, outputBal);
        nativeOut += IBentoPool(params.outputToNative.path[0].pool).getAmountOut(data);
    }
    IFeeConfig.FeeCategory memory fees = getFees();
    return nativeOut * fees.total / DIVISOR * fees.call / DIVISOR;
}
```

## Funções Write

### deposit()

Deposita o token de farm subjacente (ou "want") na farm por meio do contrato chef conectado. Primeiro verifica se a estratégia contém alguma token de farm subjacente (ou "want") antes de depositar todo o saldo no contrato chef.

```solidity
function deposit() public whenNotPaused {
    uint256 wantBal = IERC20(want).balanceOf(address(this));
    if (wantBal > 0) {
        IMiniChefV2(chef).deposit(poolId, wantBal, address(this));
        emit Deposit(balanceOf());
    }
}
```

### withdraw()

Função externa chamada pelo cofre para facilitar as retiradas do usuário. Primeiro verifica se o saldo da token de farm subjacente (ou "want") é suficiente para atender à solicitação, e depois retira essa quantia do contrato chef, antes de transferir de volta para o contrato do cofre.

```solidity
function withdraw(uint256 _amount) external {
    require(msg.sender == vault, "!vault");
    uint256 wantBal = IERC20(want).balanceOf(address(this));
    if (wantBal < _amount) {
        IMiniChefV2(chef).withdraw(poolId, _amount.sub(wantBal), address(this));
        wantBal = IERC20(want).balanceOf(address(this));
    }
    if (wantBal > _amount) {
        wantBal = _amount;
    }
    if (tx.origin != owner() && !paused()) {
        uint256 withdrawalFeeAmount = wantBal * withdrawalFee / WITHDRAWAL_MAX;
        wantBal = wantBal - withdrawalFeeAmount;
    }
    IERC20(want).safeTransfer(vault, wantBal);
    emit Withdraw(balanceOf());
}
```

### harvest()

Harvest invoca a composição do cofre para todos os usuários. Especificamente, isso coleta do contrato chef, cobra as taxas da coleta e então deposita as recompensas coletadas de volta na farm para alcançar o efeito de autocomposição.

Esta função é completamente descentralizada, o que significa que qualquer pessoa pode chamar a função e pode ganhar uma recompensa entre 0,05 - 0,5% do rendimento total. Isto pode ser chamado por qualquer um dos três métodos, detalhados abaixo.

```solidity
// @dev Default harvest() method.
function harvest() external virtual gasThrottle {
    _harvest(tx.origin);
}

// @dev Alternative harvest() method, where caller receives a fee.
function harvest(address callFeeRecipient) external virtual {
    _harvest(callFeeRecipient);
}

// @dev Alternative harvest() method, where manager calls without gas throttling.
function managerHarvest() external onlyManager {
    _harvest(tx.origin);
}

// @dev Underlying internal _harvest() function, used by all 3 public methods.
function _harvest(address callFeeRecipient) internal whenNotPaused {
    IMiniChefV2(chef).harvest(poolId, address(this));
    uint256 outputBal = IERC20(output).balanceOf(address(this));
    uint256 rewardBal = IERC20(reward).balanceOf(address(this));
    if (outputBal > 0 || rewardBal > 0) {
        chargeFees(callFeeRecipient);
        addLiquidity();
        uint256 wantHarvested = balanceOfWant();
        deposit();
        lastHarvest = block.timestamp;
        emit StratHarvest(msg.sender, wantHarvested, balanceOf());
    }
}
```

### chargeFees()

Método interno para cobrar taxas em cada [#harvest](./#harvest "mention") chamada, trocando a token nativa na estratégia pela token de saída através do contrato roteador. O contrato então calcula a saída para o destinatário das diferentes taxas e transfere as tokens de saída de acordo com a alocação. Os destinatários são o chamador da coleta, o estrategista que implantou o contrato e a tesouraria da Beefy.

```solidity
function chargeFees(address callFeeRecipient) internal {
    IFeeConfig.FeeCategory memory fees = getFees();
    uint256 rewardBal = IERC20(reward).balanceOf(address(this));
    if (rewardBal > 0 && reward != native) {
        ITridentRouter.ExactInputParams memory _rewardToNative = params.rewardToNative;
        _rewardToNative.amountIn = rewardBal;
        ITridentRouter(unirouter).exactInputWithNativeToken(_rewardToNative);
    }
    uint256 outputBal = IERC20(output).balanceOf(address(this));
    if (outputBal > 0) {
        ITridentRouter.ExactInputParams memory _outputToNative = params.outputToNative;
        _outputToNative.amountIn = outputBal;
        ITridentRouter(unirouter).exactInputWithNativeToken(_outputToNative);
    }
    uint256 nativeBal = IERC20(native).balanceOf(address(this)) * fees.total / DIVISOR;
    uint256 callFeeAmount = nativeBal * fees.call / DIVISOR;
    IERC20(native).safeTransfer(callFeeRecipient, callFeeAmount);
    uint256 beefyFeeAmount = nativeBal * fees.beefy / DIVISOR;
    IERC20(native).safeTransfer(beefyFeeRecipient, beefyFeeAmount);
    uint256 strategistFeeAmount = nativeBal * fees.strategist / DIVISOR;
    IERC20(native).safeTransfer(strategist, strategistFeeAmount);
    emit ChargedFees(callFeeAmount, beefyFeeAmount, strategistFeeAmount);
}
```

### addLiquidity()

Método interno para adicionar liquidez na pool subjacente para a farm como parte da função [#harvest](./#harvest "mention"). Troca a token de saída para as tokens subjacentes da farm, e depois adiciona ambas à pool de liquidez para obter a token de depósito subjacente da farm (ou "want"). O restante da chamada de _harvest()_ deposita então essas tokens na farm.

```solidity
function addLiquidity() internal {
    uint256 nativeHalf = IERC20(native).balanceOf(address(this)) / 2;
    if (lpToken0 != native) {
        ITridentRouter.ExactInputParams memory _nativeToLp0 = params.nativeToLp0;
        _nativeToLp0.amountIn = nativeHalf;
        ITridentRouter(unirouter).exactInputWithNativeToken(_nativeToLp0);
    }
    if (lpToken1 != native) {
        ITridentRouter.ExactInputParams memory _nativeToLp1 = params.nativeToLp1;
        _nativeToLp1.amountIn = nativeHalf;
        ITridentRouter(unirouter).exactInputWithNativeToken(_nativeToLp1);
    }
    ITridentRouter.TokenInput[] memory tokens = new ITridentRouter.TokenInput[](2);
    uint256 lp0Bal = IERC20(lpToken0).balanceOf(address(this));
    uint256 lp1Bal = IERC20(lpToken1).balanceOf(address(this));
    tokens[0] = ITridentRouter.TokenInput(lpToken0, true, lp0Bal);
    tokens[1] = ITridentRouter.TokenInput(lpToken1, true, lp1Bal);
    bytes memory data = abi.encode(address(this));
    ITridentRouter(unirouter).addLiquidity(tokens, want, 1, data);
}
```

### setHarvestOnDeposit()

A maioria dos cofres Beefy fazem a coleta no depósito ([#o-que-e-coleta-no-deposito](../../produtos/vaults.md#o-que-e-coleta-no-deposito "mention")). Isto significa que, antes dos fundos do usuário entrarem na estratégia, o rendimento em todo o cofre é colhido e reinvestido. Isto impede que novos depositantes roubem o rendimento dos depositantes existentes. Como resultado, qualquer cofre que é definido para colheita em depósito é capaz de remover completamente a taxa de retirada.

_harvestOnDeposit_ é uma variável booleana que é definida como verdadeira quando o cofre está coletando em depósito. Isto é alternado pela função _setHarvestOnDeposit()_, definida abaixo:

```solidity
bool public harvestOnDeposit;

function setHarvestOnDeposit(bool _harvestOnDeposit) external onlyManager {
    harvestOnDeposit = _harvestOnDeposit;
    if (harvestOnDeposit) {
        setWithdrawalFee(0);
    } else {
        setWithdrawalFee(10);
    }
}
```

### beforeDeposit()

Função externa utilizada para facilitar as coletas em depósito, se ativa. Verifica primeiro se a coleta em depósito está ativa e se o chamador é o cofre, antes da coleta.

```solidity
function beforeDeposit() external override {
    if (harvestOnDeposit) {
        require(msg.sender == vault, "!vault");
        _harvest(tx.origin);
    }
}
```

### panic()

A Beefy não toca diretamente em nenhum dos fundos de usuário mantidos no protocolo. Durante períodos de incerteza ou atualizações na farm subjacente, a Beefy pode retirar todos os fundos dos contratos de terceiros e mantê-los em segurança na estratégia usando a função _panic()_. Ao "entrar em pânico" na estratégia, os usuários permanecem capazes de retirar seus fundos do cofre sem qualquer atraso ou exposição a riscos de terceiros. Esta função também remove todas as licenças tanto para o UniRouter quanto para o contrato da farm subjacente, para garantir que nenhum fundo possa ser retirado por esses contratos.

```solidity
function panic() public onlyManager {
    pause();
    IMiniChefV2(chef).emergencyWithdraw(poolId, address(this));
}
```

### pause() / unpause()

Todas as estratégias da Beefy são pausáveis, o que significa que a funcionalidade pode ser interrompida durante as operações normais da estratégia pelo gerente de estratégia. Isto é herdado através do [StratManager.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Common/StratManager.sol), e depende do contrato abstrato padrão [Pausable.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/security/Pausable.sol). Esta função também remove todas as permissões tanto para o UniRouter quanto para o contrato da farm subjacente, para garantir que nenhum fundo possa ser retirado por esses contratos.

```solidity
function pause() public onlyManager {
    _pause();
    _removeAllowances();
}
```

Ao contrário, as estratégias também podem ser despausadas, revertendo as ações na função de pausa.

```solidity
function unpause() external onlyManager {
    _unpause();
    _giveAllowances();
    deposit();
}
```

As funções afetadas pela pausa na maioria dos contratos de estratégia são [#deposit](./#deposit "mention"), [#withdraw](./#withdraw "mention") e [#harvest](./#harvest "mention").

### \_giveAllowances / \_removeAllowances()

Funções internas usadas para definir e remover todas as permissões com contratos de terceiros, para controlar se os contratos de terceiros têm as permissões necessárias para retirar fundos da estratégia. Os contratos relevantes são o da token da farm subjacente/_want()_ (por exemplo, a token LP), a token de saída da estratégia (muitas vezes a mesma que a _want()_), a token nativa da rede (usada para gás) e as tokens subjacentes usados para a farm.

```solidity
function _giveAllowances() internal {
    IERC20(want).safeApprove(chef, type(uint).max);
    IERC20(output).safeApprove(unirouter, type(uint).max);
    IERC20(native).safeApprove(unirouter, type(uint).max);
    IERC20(lpToken0).safeApprove(unirouter, 0);
    IERC20(lpToken0).safeApprove(unirouter, type(uint).max);
    IERC20(lpToken1).safeApprove(unirouter, 0);
    IERC20(lpToken1).safeApprove(unirouter, type(uint).max);
}

function _removeAllowances() internal {
    IERC20(want).safeApprove(chef, 0);
    IERC20(output).safeApprove(unirouter, 0);
    IERC20(native).safeApprove(unirouter, 0);
    IERC20(lpToken0).safeApprove(unirouter, 0);
    IERC20(lpToken1).safeApprove(unirouter, 0);
}
```

### retireStrat()

Função externa utilizada como parte de uma migração de uma estratégia para outra. Isto fecha efetivamente a estratégia retirando todos os fundos e transferindo-os de volta para o cofre. Ela só pode ser acionada por uma chamada do contrato do cofre.

```solidity
function retireStrat() external {
    require(msg.sender == vault, "!vault");
    IMiniChefV2(chef).emergencyWithdraw(poolId, address(this));
    uint256 wantBal = IERC20(want).balanceOf(address(this));
    IERC20(want).transfer(vault, wantBal);
}
```

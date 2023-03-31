---
description: Tradução feita a partir da atualização de fevereiro de 2023
---

# Contrato de Cofre

O [Contrato de Cofre da Beefy](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/vaults/BeefyVaultV7.sol) é a implementação central do protocolo Beefy, que aceita e gerencia depósitos de usuários e cunhas mooTokens como prova de recebimento para facilitar os saques. Ele segue o [padrão ERC-20](https://eips.ethereum.org/EIPS/eip-20) para tokens fungíveis e transferíveis.

Além de lidar com depósitos e saques, a principal função do cofre é direcionar os fundos depositados para o [contrato-de-estrategia](contrato-de-estrategia/ "mention") de auto-reinvestimento relevante. Os contratos de cofre e estratégia são mantidos separados para isolar quaisquer riscos na estratégia dos depósitos dos usuários.

## Funções View

### want()

Devolve o endereço do token de farm subjacente (por exemplo, o token LP) usado tanto nos contratos do cofre Beefy quanto nos contratos de estratégia. Note que isto não é o mesmo que os ativos subjacentes usados para a farm.

```solidity
function want() public view returns (IERC20Upgradeable) {
    return IERC20Upgradeable(strategy.want());
}
```

### balance()

Devolve a quantidade de "want" (ou seja, a token de farm subjacente) armazenada no cofre, estratégia e fonte de rendimento como um todo.

```solidity
function balance() public view returns (uint) {
    return want().balanceOf(address(this)) + IStrategyV7(strategy).balanceOf();
}
```

### available()

Devolve a quantidade de "want" (ou seja, token de farm subjacente) armazenada apenas no cofre como um todo.

```solidity
function available() public view returns (uint256) {
    return want().balanceOf(address(this));
}
```

### totalSupply()

Retorna a quantidade total de mooTokens cunhadas como um todo, que são sempre exibidas como uma token de 18 decimais. Este é um método padrão herdado do padrão ERC-20. Veja [#o-que-sao-moedas-moo](../produtos/vaults.md#o-que-sao-moedas-moo "mention") para mais detalhes.

```solidity
function totalSupply() public view virtual override returns (uint256) {
    return _totalSupply;
}
```

### getPricePerFullShare()

Retorna o preço atual por cota do cofre (ou seja, por mooToken) como um todo denominado no "want" (ou seja, token de farm subjacente). Isto é calculado como _Preço por Cota Total =_ [#balance](contrato-de-cofre.md#balance "mention")/ [#totalsupply](contrato-de-cofre.md#totalsupply "mention").

```solidity
function getPricePerFullShare() public view returns (uint256) {
    return totalSupply() == 0 ? 1e18 : balance() * 1e18 / totalSupply();
}
```

### strategy()

Devolve o endereço atual do contrato de estratégia subjacente que o cofre está usando para gerar rendimento.

```solidity
function strategy() external view returns (address);
```

## Funções Write

### deposit()

Executa uma transferência de uma quantidade especificada ( \_amount) de "want" (ou seja, token de farm subjacente) do depositante para o cofre, e depois cunha uma quantidade proporcional de mooTokens para o depositante em troca.

```solidity
function deposit(uint _amount) public nonReentrant {
    strategy.beforeDeposit();
    uint256 _pool = balance();
    want().safeTransferFrom(msg.sender, address(this), _amount);
    earn();
    uint256 _after = balance();
    _amount = _after - _pool; // Additional check for deflationary tokens
    uint256 shares = 0;
    if (totalSupply() == 0) {
        shares = _amount;
    } else {
        shares = (_amount * totalSupply()) / _pool;
    }
    _mint(msg.sender, shares);
}
```

Além disso, há uma função auxiliar de _depositAll()_ que deposita todo o saldo de "want" da carteira do usuário no momento da transação.

### withdraw()

Executa a queima de uma quantidade especificada ( \_amount) de mooTokens do depositante e, em seguida, transfere uma quantidade proporcional de "want" (ou seja, token de farm subjacente) para o depositante em troca.

```solidity
function withdraw(uint256 _shares) public {
    uint256 r = (balance() * _shares) / totalSupply();
    _burn(msg.sender, _shares);
    uint b = want().balanceOf(address(this));
    if (b < r) {
        uint _withdraw = r - b;
        strategy.withdraw(_withdraw);
        uint _after = want().balanceOf(address(this));
        uint _diff = _after - b;
        if (_diff < _withdraw) {
            r = b + _diff;
        }
    }
    want().safeTransfer(msg.sender, r);
}
```

Similar ao [#deposit](contrato-de-cofre.md#deposit "mention"), há uma função de ajuda que _withdrawAll()_ que retira todo o saldo de mooTokens na carteira do usuário no momento da transação.

### earn()

Executa a transferência de [#available](contrato-de-cofre.md#available "mention")"want" (ou seja, token de farm subjacente) do Contrato de Cofre ao contrato de estratégia e aciona a função de _deposit()_ da estratégia para aplicar os fundos e começar a render.

```solidity
function earn() public {
    uint _bal = available();
    want().safeTransfer(address(strategy), _bal);
    strategy.deposit();
}
```

### proposeStrat()

Escreve o endereço de uma estratégia alternativa para a memória do Contrato de Cofre, em antecipação à atualização da estratégia atual para a estratégia alternativa usando [#upgradestrat](contrato-de-cofre.md#upgradestrat "mention").

```solidity
function proposeStrat(address _implementation) public onlyOwner {
    require(address(this) == IStrategyV7(_implementation).vault(), "Proposal not valid for this Vault");
    require(want() == IStrategyV7(_implementation).want(), "Different want");
    stratCandidate = StratCandidate({
        implementation: _implementation,
        proposedTime: block.timestamp
    });
    emit NewStratCandidate(_implementation);
}
```

### upgradeStrat()

Substitui o endereço da estratégia atual por uma estratégia alternativa especificada por [#proposestrat](contrato-de-cofre.md#proposestrat "mention").

```solidity
function upgradeStrat() public onlyOwner {
    require(stratCandidate.implementation != address(0), "There is no candidate");
    require(stratCandidate.proposedTime + approvalDelay < block.timestamp, "Delay has not passed");
    emit UpgradeStrat(stratCandidate.implementation);
    strategy.retireStrat();
    strategy = IStrategyV7(stratCandidate.implementation);
    stratCandidate.implementation = address(0);
    stratCandidate.proposedTime = 5000000000;
    earn();
}
```

## BeefyVaultV7.sol

O atual lançamento de nosso contrato padrão Cofre Beefy é [BeefyVaultV7.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/vaults/BeefyVaultV7.sol), que foi [lançado ](https://github.com/beefyfinance/beefy-contracts/pull/83)em agosto de 2022. O lançamento do V7 melhorou em relação à versão anterior de algumas formas importantes:

* Introduziu a possibilidade de atualização do cofre através de padrões de proxy, para facilitar atualizações e mudanças para cofres Beefy ativos sem a necessidade de depreciação e reimplantação;
* Atualizou a interface da estratégia para permitir estratégias atualizáveis e;
* Modificou todos os contratos para remover a confiança na biblioteca SafeMath, que em geral foi aposentada após a incorporação de suas características no Solidity v0.8.

Separadamente, um contrato _ERC-4646-compliant wrapper_ foi lançado para o cofre V7 em novembro de 2022, o que permite aos desenvolvedores incorporar os Cofres Beefy em seus projetos com funcionalidades e interfaces de cofre padronizadas. Veja [contrato-beefywrapper.md](outros-contratos-da-beefy/contrato-beefywrapper.md "mention") para mais informações.

---
description: Beefy wrapped SPIRIT.
---

# binSPIRIT

## Introdução

### O que é inSPIRIT?

Quando os usuários bloqueiam seus tokens SPIRIT no SpiritSwap por entre 1 semana e quatro anos, eles recebem uma quantidade proporcional de inSPIRIT. inSPIRIT é intransferível e o valor na carteira do titular diminui constantemente para 0 quando o bloqueio termina. Os detentores do inSPIRIT podem reivindicar taxas de receita de protocolo (variáveis semana a semana, mas com TAEG de até 80%) e receber um aumento de até 2,5 vezes nas fazendas. O aumento depende do saldo do inSPIRIT do usuário em comparação com todos os outros titulares e do saldo que ele apostou na fazenda em comparação com o TVL da fazenda. Você também não poderá liquidar sua posição até o final do bloqueio de tempo.

### O que é binSPIRIT?

binSPIRIT é a versão do SPIRIT embrulhada em Beefy, permitindo que os titulares ganhem taxas de protocolo SpiritSwap sem ter que bloquear seu SPIRIT. Um usuário pode cunhar o binSPIRIT 1:1 usando o SPIRIT através da interface do usuário na página do cofre do binSPIRIT, ou pode obter o binSPIRIT comprando em uma exchange. O binSPIRIT pode ser apostado no cofre do Beefy para obter mais binSPIRIT ou diretamente no pool de recompensas para receber o SPIRIT. O SPIRIT usado para cunhar binSPIRIT está bloqueado para inSPIRIT. Beefy usa este inSPIRIT para impulsionar todos os cofres Beefy SpiritSwap e votar em emissões de incentivo.

### Como o binSPIRIT mantém seu peg?

Se um usuário quiser liquidar sua posição, ele poderá negociar binSPIRIT em uma bolsa. Ao contrário do inSPIRIT, os usuários nunca ficam presos e podem sair a qualquer momento. Isso também significa que o binSPIRIT nem sempre pode ser atrelado ao SPIRIT, mas manterá um peg solto.&#x20;

Se o binSPIRIT cair, as taxas do protocolo SpiritSwap comprarão de volta mais binSPIRIT por SPIRIT e o APY do cofre Beefy aumentará. A APR para o pool de recompensas também aumentaria, permitindo que os usuários comprassem e apostassem no binSPIRIT por uma proporção muito maior das taxas do protocolo SpiritSwap do que apenas bloquear o SPIRIT.&#x20;

Se o binSPIRIT ultrapassar o peg, os arbitradores cunharão o binSPIRIT e venderão com lucro.

## Como funciona o Gauge Staker?

O contrato Gauge Staker tem duas partes notáveis: bloquear SPIRIT para cunhar binSPIRIT e passar tokens entre estratégias e medidores. Bloquear o SPIRIT no Gauge Staker permite que o contrato obtenha inSPIRIT intransferível. Todas as estratégias do SpiritSwap para medidores passarão seus depósitos, saques e recompensas de colheita através do Gauge Staker. Como todos os depósitos são provenientes do endereço do Gauge Staker, o maior aumento pode ser obtido em todos os medidores, pois o contrato também mantém o inSPIRIT concentrado.

#### Deposite SPIRIT para poder mint binSPIRIT

Um usuário pode depositar SPIRIT (quer) e o contrato confirmará o valor recebido verificando os saldos antes e depois da transferência. Se o valor recebido for diferente de zero, verifique se existe um bloqueio existente para SPIRIT, o que provavelmente ocorrerá, a menos que o bloqueio não tenha sido iniciado antes ou tenha expirado. Se o bloqueio existir, ele será estendido para os 4 anos completos se o tempo de bloqueio atual for menor que o valor total e o saldo recebido de SPIRIT for bloqueado para obter uma quantidade de 1:1 de inSPIRIT. Se nenhum bloqueio existir atualmente, crie um novo e bloqueie o saldo do SPIRIT no contrato. Finalmente, forme uma quantidade igual de binSPIRIT como o saldo recebido de SPIRIT do usuário.

```
// deposit 'want' and lock
function _deposit(address _user, uint256 _amount) internal nonReentrant whenNotPaused {
    uint256 _pool = balanceOfWant();    
    want.safeTransferFrom(msg.sender, address(this), _amount);
    uint256 _after = balanceOfWant();    
    _amount = _after.sub(_pool); // Additional check for deflationary tokens
    if (_amount > 0) {
        if (balanceOfVe() > 0) {
            increaseUnlockTime();
            veWant.increase_amount(_amount);        
        } else {            
            _createLock();
        }        
        _mint(_user, _amount);        
        emit DepositWant(balanceOfVe());    
    }
}
```

#### Vote no gauges para boost

O Beefy Keeper pode votar em incentivos de medidor usando o saldo inSPIRIT no Gauge Staker como poder de voto. Ele será usado principalmente para votar nos medidores do Beefy e de parceiros estratégicos, e pode ser governado pelo Beefy DAO para votar em vários incentivos nos medidores. A função de votação é uma simples chamada para o contrato Gauge Proxy da SpiritSwap, que registra os votos e decide a distribuição dos incentivos de medidor. O Beefy keeper pode dividir o poder de votação entre vários medidores em uma única chamada usando os arrays de parâmetros.

```
// vote on boosted farms
function vote(address[] calldata _tokenVote, uint256[] calldata _weights) external onlyManager {    
    gaugeProxy.vote(_tokenVote, _weights);    
    emit Vote(_tokenVote, _weights);
}
```

**Passe por tokens entre estratégias e medidores**

As estratégias para os cofres SpiritSwap da Beefy devem passar por seus depósitos, saques e colheitas de e para o Gauge Staker. Apenas uma estratégia na lista de permissões pode interagir com o Gauge Staker, e cada medidor recebe no máximo uma estratégia.&#x20;

Depósitos e saques passam pelo valor exato solicitado (\_amount) no token atribuído ao medidor (\_subjacente). As colheitas (claimGaugeReward()) passam apenas pela recompensa SPIRIT (querer) que é recebida pelo Gauge Staker ao reivindicar a recompensa, ignorando o saldo existente no Gauge Staker. Nenhum dos fundos é mantido no Gauge Staker, eles são sempre repassados na mesma transação.

```
// pass through a deposit to a gauge
function deposit(address _gauge, uint256 _amount) external onlyWhitelist(_gauge) {
    address _underlying = IGauge(_gauge).TOKEN();    
    IERC20Upgradeable(_underlying).safeTransferFrom(msg.sender, address(this), _amount);    
    IGauge(_gauge).deposit(_amount);
}
    
// pass through a withdrawal from a gauge
function withdraw(address _gauge, uint256 _amount) external onlyWhitelist(_gauge) {
    address _underlying = IGauge(_gauge).TOKEN();    
    IGauge(_gauge).withdraw(_amount);    
    IERC20Upgradeable(_underlying).safeTransfer(msg.sender, _amount);
}

// pass through rewards from a gauge
function claimGaugeReward(address _gauge) external onlyWhitelist(_gauge) {
    uint256 _before = balanceOfWant();
    IGauge(_gauge).getReward();
    uint256 _balance = balanceOfWant().sub(_before);
    want.safeTransfer(msg.sender, _balance);
}
```

#### Claim SpiritSwap protocol fees

A participação no inSPIRIT dá ao Gauge Staker o direito de reivindicar uma parte das taxas de protocolo do SpiritSwap, que serão distribuídas aos apostadores binSPIRIT em um pool de recompensas. As taxas de protocolo são distribuídas uma vez por semana na forma de SPIRIT e precisam ser reivindicadas no contrato de Distribuidor de Taxas. O contrato do Conjunto de Recompensas chamará a função de reivindicação por meio de ClaimVeWantReward(). Apenas a recompensa do ESPÍRITO (desejo) é imediatamente devolvida ao Conjunto de Recompensas, se houver algo disponível para reivindicar.

```
// pass through rewards from the fee distributor
function claimVeWantReward() external onlyRewardPool {    
    uint256 _before = balanceOfWant();    
    feeDistributor.claim();    
    uint256 _balance = balanceOfWant().sub(_before);    
    want.safeTransfer(msg.sender, _balance);
}
```

#### Whitelisting strategies

O Beefy Keeper pode colocar um endereço de estratégia na lista de permissões, desde que não haja uma estratégia ativa que tenha fundos implantados no mesmo medidor da nova estratégia. Uma estratégia antiga deve entrar em pânico antes que uma nova estratégia para o mesmo medidor possa ser testada, para que os fundos do usuário estejam sempre protegidos. A aprovação do token (\_want) atribuído ao medidor é redefinida e aumentada para o limite máximo de gastos pelo medidor. O medidor é mapeado para a estratégia da lista de permissões e a estratégia tem acesso permitido ao Gauge Staker para o medidor especificado.

```
// whitelists a strategy address to interact with the Gauge Staker and gives approvals
function whitelistStrategy(address _strategy) external onlyManager {    
    IERC20Upgradeable _want = IGaugeStrategy(_strategy).want();    
    address _gauge = IGaugeStrategy(_strategy).gauge();    
    require(IGauge(_gauge).balanceOf(address(this)) == 0, '!inactive');    
    _want.safeApprove(_gauge, 0);    
    _want.safeApprove(_gauge, type(uint256).max);    
    whitelistedStrategy[_gauge] = _strategy;
}
```

#### Upgrading strategies

Uma nova estratégia para um medidor com uma estratégia existente pode ser proposta uma vez que tenha sido totalmente testada. A propostaStrategy() deve ser chamada no Gauge Staker antes de upgradeStrat() no cofre para que a troca seja bem-sucedida. A nova estratégia deve ter o mesmo calibre que a estratégia anterior. upgradeStrategy() só é chamado em retireStrat() na estratégia anterior, portanto, é controlado indiretamente pelo proprietário do cofre por meio da atualização do endereço da estratégia no cofre.

```
// prepare a strategy to be retired and replaced with another
function proposeStrategy(address _oldStrategy, address _newStrategy) external onlyManager {    
    require(IGaugeStrategy(_oldStrategy).gauge() == IGaugeStrategy(_newStrategy).gauge(), '!gauge');    
    replacementStrategy[_oldStrategy] = _newStrategy;
}

// switch over whitelist from one strategy to another for a gauge
function upgradeStrategy(address _gauge) external onlyWhitelist(_gauge) {
    whitelistedStrategy[_gauge] = replacementStrategy[msg.sender];
}
```

## Contratos

* binSPIRIT/GaugeStaker: [0x44e314190D9E4cE6d4C0903459204F8E21ff940A](https://ftmscan.com/address/0x44e314190D9E4cE6d4C0903459204F8E21ff940A)
* Reward Pool: [0xFAE44b30F6F9BbD44E6B7687471dd73D71FaBDC6](https://ftmscan.com/address/0xFAE44b30F6F9BbD44E6B7687471dd73D71FaBDC6)

As funções críticas são sempre gerenciadas por meio de transações multi-sig e timelocks. Nenhum fundo é armazenado diretamente no Gauge Staker e apenas a estratégia ativa na lista de permissões pode interagir com os fundos armazenados em um medidor.

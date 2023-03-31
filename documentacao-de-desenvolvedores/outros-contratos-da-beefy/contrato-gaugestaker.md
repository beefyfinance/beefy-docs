---
description: Tradução feita a partir da atualização de junho de 2022
---

# Contrato GaugeStaker

## O que é o GaugeStaker?

O contrato GaugeStaker é o contrato inteligente central da moeda binSPIRIT, que gerencia tanto a coleta de dividendos do protocolo SpiritSwap para os dententores de inSPIRIT, quanto os impulsos de inSPIRIT para os cofres SpiritSwap da Beefy.

## Como funciona o GaugeStaker?

O GaugeStaker tem três papéis notáveis: (1) gerenciar depósitos de SPIRIT de usuários para acumular recompensas de inSPIRIT; (2) gerenciar os votos para os impulsos das pools da SpiritSwap e; (3) passar moedas entre outras estratégias da Beefy e os medidores de incentivos de pools.

Quando usuários depositam SPIRIT, o GaugeStaker vai depositar SPIRIT automaticamente na SpiritSwap para receber inSPIRIT não-transferível. Toda a SPIRIT depositada deve ser trancada (então não pode ser retirada), logo o GaugeStaker tranca todos os depósitos pelo maior período de tempo possível (atualmente, 4 anos) para receber a quantidade máxima de inSPIRIT. Recompensas dos dividendos do protocolo se acumulam constantemente junto à SPIRIT trancada e o GaugeStaker automaticamente coleta essas recompensas e as retorna para o [cofre de binSPIRIT da Beefy](https://app.beefy.finance/#/vault/beefy-binspirit) regularmente, onde elas são automaticamente redepositadas.

Detentores de inSPIRIT também têm direito de votar na governança da SpiritSwap e na distribuição de recompensas das pools impulsionadas, então o GaugeStaker gerencia a alocação desses votos.

Finalmente, detentores de inSPIRIT também recebem recompensas impulsionadas em pools selecionadas da SpiritSwap. Todos os cofres impulsionados da Beefy de pools da SpiritSwap estão configurados para passar todos os seus depósitos, retiradas e coletas de recompensas através do GaugeStaker, para receber os benefícios do impulso. Isso provê os maiores impulsos possíveis para todas as pools impulsionadas, visto que o GaugeStaker detém a concentração total da inSPIRIT acumulada da Beefy.

## Funcionalidade do GaugeStaker

O contrato GaugeStaker incorpora uma gama de diferentes funcionalidades e métodos para executar suas duas funções. Essas incluem:

### Deposite SPIRIT para cunhar binSPIRIT

Um usuário pode depositar SPIRIT (`want`) e o contrato vai confirmar a quantia que é recebida, checando o saldo antes e depois da transferência. Se a quantia recebida for diferente de zero, então o contrato checa se a há uma tranca de SPIRIT existente, que provavelmente haverá, a menos que a tranca não tenha sido iniciada antes ou foi deixada para expirar. Se a tranca existe, então ela será extendida para 4 anos se o tempo atual for menos do que a duração máxima e o saldo de SPIRIT recebido é trancado para receber uma quantia 1:1 de inSPIRIT. Se nenhuma tranca existe, o contrato cria uma nova e tranca o saldo de SPIRIT no contrato. Finalmente, é cunhada uma quantia de binSPIRIT igual ao saldo de SPIRIT recebido pelo usuário.

```solidity
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

### Vote em quais medidores impulsionar

O Beefy Keeper pode votar em medidores de incentivos usando o saldo de inSPIRIT do GaugeStaker como poder de votação. Ele é usado principalmente para votar em medidores da Beefy e de parceiros estratégicos, pode também ser governado pela Beefy DAO para votar em vários medidores de incentivos. A função de votação é um chamado simples para o contrato Gauge Proxy da SpiritSwap que grava os votos e decide a distribuição dos incentivos dos medidores. O Beefy Keeper pode dividir o poder de votação entre múltiplos medidores em um único chamado usando o os parâmetros.

```solidity
// vote on boosted farms
function vote(address[] calldata _tokenVote, uint256[] calldata _weights) external onlyManager {    
    gaugeProxy.vote(_tokenVote, _weights);    
    emit Vote(_tokenVote, _weights);
}
```

### Passagem de moedas entre estratégias e medidores

As estratégias para cofres da SpiritSwap na beefy precisam passar seus depósitos, retiradas e coletas pelo GaugeStaker. Apenas uma estratégia aprovada pode interagir com o GaugeStaker e cada medidor está assinalado a no máximo uma estratégia.

Depositam e retiradas passam a quantia exata que requerida (`_amount`) na moeda que está assinalada ao medidor (`_underlying`). Coletas (`claimGaugeReward()`) passam apenas  recompensa de SPIRIT (`want`) que é recebida pelo GaugeStaker quando coleta a recompensa, ignorando o saldo existente no GaugeStaker. Nenhum dos fundos é mantido no GaugeStaker, eles são sempre repassados na mesma transação.

```solidity
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

### Coleta das taxas do protocolo da SpiritSwap

Ter inSPIRIT dá ao GaugeStaker o direito de colegar uma porção das taxas do protocolo da SpiritSwap, que são distribuídas para os depositadores de binSPIRIT em uma pool de recompensas. As taxas do protocolo são distribuídas uma vez por semana na forma de SPIRIT e precisam ser coletadas do contrato Fee Distributor (Distribuidor de Taxas). O contrato Reward Pool (Pool de Recompensas) vai chamar  a função de coleta via `claimVeWantReward()` . Apenas a recompensa de SPIRIT (`want`) é imediatamente passada de volta para a pool de recompensas, se houver algo disponível para coletar.

```solidity
// pass through rewards from the fee distributor
function claimVeWantReward() external onlyRewardPool {    
    uint256 _before = balanceOfWant();    
    feeDistributor.claim();    
    uint256 _balance = balanceOfWant().sub(_before);    
    want.safeTransfer(msg.sender, _balance);
}
```

### Aprovando estratégias

O Beefy Keeper pode aprovar um endereço de estratégia desde que não haja uma estratégia ativa  que tem fundos oriundos do mesmo medidor que a nova estratégia. Uma estratégia antiga precisa ser suspensa antes que uma nova estratégia para o mesmo medidor seja testada, assim os fundos dos usuários estão sempre protegidos. A aprovação da moeda (`_want`) assinalada à pool é resetada e aumentada para o limite máximo para ser gasta no medidor. O medidor é mapeado para a estratégia aprovada e a estratégia tem acesso permitido ao GaugeStaker para o medidor específico.

```solidity
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

### Atualizando estratégias

Uma nova estratégia para um medidor com uma estratégia existente pode ser proposta uma vez que foi completamente testada. `proposeStrategy()` deve ser chamada no GaugeStaker antes de `upgradeStrat()` no cofre para que a troca se suceda. A nova estratégia deve ter o mesmo medidor que a estratégia anterior. `upgradeStrategy()` é apenas chamada em `retireStrat()` na estratégia anterior, então é controlada indiretamente pelo dono do cofre atualizando o endereço da estratégia do cofre.

```solidity
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

Funções críticas são sempre manejadas por meio de transações multi-assinatura e trancas de tempo. Nenhum fundo é guardado diretamente no GaugeStaker e apenas a estratégia aprovada ativa pode interagir com os fundos em um medidor.

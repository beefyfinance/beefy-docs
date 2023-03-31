---
description: Tradução feita a partir da atualização de fevereiro de 2023
---

# Contrato StratFeeManager

O [contrato StratFeeManager](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Common/StratFeeManagerInitializable.sol) é uma coleção de dependências importantes que são importadas e utilizadas em cada [.](./ "mention") da Beefy.

Originalmente, estas dependências eram divididas em dois contratos - [StratManager.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Common/StratManager.sol) e [FeeManager.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Common/FeeManager.sol). Após a mudança para Solidity V0.8, os dois foram combinados em um único contrato - [StratFeeManager.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Common/StratFeeManager.sol). A versão atual - [StratFeeManagerInitializable.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Common/StratFeeManagerInitializable.sol) - facilitou uma mudança para estratégias de clonagem por procuração (que devem ser inicializadas com os argumentos relevantes para a estratégia e suas dependências), para evitar a necessidade de implantar cada estratégia individualmente.

## Dependências

Os contratos StratFeeManager também introduzem dependências adicionais em si, especificamente o [Ownable.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/Ownable.sol) - que introduz funcionalidade para definir o proprietário de um contrato e restringir a funcionalidade somente a eles - e o [Pausable.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/security/Pausable.sol) - que introduz funcionalidade para congelar a funcionalidade em um contrato, colocando o contrato em pausa. Ambas as dependências são, em última instância, incluídas em cada Contrato de Estratégia Beefy.

## Modificadores

Introduz um modificador _onlyManager()_ para restringir funções a serem utilizadas apenas pelo gerente de estratégia.

```solidity
modifier onlyManager() {
    require(msg.sender == owner() || msg.sender == keeper, "!manager");
    _;
}
```

## Funções View

### getFees()

Devolve o valor de todas as taxas do contrato de configuração de taxas.

```solidity
function getFees() internal view returns (IFeeConfig.FeeCategory memory) {
    return beefyFeeConfig.getFees(address(this));
}
```

### getAllFees()

Retorna o valor de todas as taxas do contrato de configuração de taxas, assim como as taxas dinâmicas de depósito e retirada.

```solidity
function getAllFees() external view returns (IFeeConfig.AllFees memory) {
    return IFeeConfig.AllFees(getFees(), depositFee(), withdrawFee());
}
```

### getStratFeeId()

Devolve o valor integral da ID da taxa de estratégia a partir do contrato de configuração da taxa.

```solidity
function getStratFeeId() external view returns (uint256) {
    return beefyFeeConfig.stratFeeId(address(this));
}
```

## Funções Write

### setStratFeeId()

Define um novo valor integral para a ID da taxa da estratégia, que indica a taxa relevante para a estratégia.

```solidity
function setStratFeeId(uint256 _feeId) external onlyManager {
    beefyFeeConfig.setStratFeeId(_feeId);
    emit SetStratFeeId(_feeId);
}
```

### setWithdrawalFee()

Estabelece um novo valor integral para a taxa de retirada do contrato que é cobrada em cada coleta.

```solidity
function setWithdrawalFee(uint256 _fee) public onlyManager {
    require(_fee <= WITHDRAWAL_FEE_CAP, "!cap");
    withdrawalFee = _fee;
    emit SetWithdrawalFee(_fee);
}
```

### setVault()

Define um novo endereço para o cofre do contrato, que gerencia os fundos do usuário.

```solidity
function setVault(address _vault) external onlyOwner {
    vault = _vault;
    emit SetVault(_vault);
}
```

### setUnirouter()

Define um novo endereço para o roteador do contrato que processa as trocas dentro do contrato.

```solidity
function setUnirouter(address _unirouter) external onlyOwner {
    unirouter = _unirouter;
    emit SetUnirouter(_unirouter);
}
```

### setKeeper()

Estabelece um novo endereço para o encarregado do contrato, que pode "entrar em pânico" com a estratégia.

```solidity
function setKeeper(address _keeper) external onlyManager {
    keeper = _keeper;
    emit SetKeeper(_keeper);
}
```

### setStrategist()

Define um novo endereço para o estrategista do contrato que recebe a taxa do estrategista.

```solidity
function setStrategist(address _strategist) external {
    require(msg.sender == strategist, "!strategist");
    strategist = _strategist;
    emit SetStrategist(_strategist);
}
```

### setBeefyFeeRecipient()

Define um novo endereço para o destinatário da taxa da Beefy sobre as coletas, normalmente um contrato de tesouraria da Beefy.

```solidity
function setBeefyFeeRecipient(address _beefyFeeRecipient) external onlyOwner {
    beefyFeeRecipient = _beefyFeeRecipient;
    emit SetBeefyFeeRecipient(_beefyFeeRecipient);
}
```

### setBeefyFeeConfig()

Define um novo endereço para o contrato de configuração de taxas utilizado pela estratégia de coleta de taxas.

```solidity
function setBeefyFeeConfig(address _beefyFeeConfig) external onlyOwner {
    beefyFeeConfig = IFeeConfig(_beefyFeeConfig);
    emit SetBeefyFeeConfig(_beefyFeeConfig);
}
```

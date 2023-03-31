---
description: Tradução feita a partir da atualização de fevereiro de 2023
---

# Contrato FeeConfigurator

O Contrato [BeefyFeeConfigurator](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/infra/BeefyFeeConfigurator.sol) é um contrato de infraestrutura hospedado em cada uma das blockchains em que a Beefy se instalou. O contrato gerencia a configuração de tarifas para cada estratégia na rede relevante, com a qual o [contrato-stratfeemanager.md](../contrato-de-estrategia/contrato-stratfeemanager.md "mention") faz interface através da [IFeeConfig.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/interfaces/common/IFeeConfig.sol).

O endereço relevante para o Contrato FeeConfigurator ("_beefyFeeConfig_") em cada rede é exibido na API Beefy utilizando o endpoint [#get-config](../api-da-beefy.md#get-config "mention").

## Modificadores

Inclui um modificador padrão _onlyManager()_ para controlar o acesso às funções Write.

```solidity
modifier onlyManager() {
    require(msg.sender == owner() || msg.sender == keeper, "!manager");
    _;
}
```

## Funções View

### getFees()

Retorna uma estrutura _FeeCategory_ para um argumento específico de endereço de estratégia, mostrando as taxas totais cobradas, as taxas para Beefy, o chamador da coleta e o estrategista, uma string mostrando a descrição do tipo de categoria de taxa, e uma variável booleana "_active_", mostrando se a categoria de taxa está ligada ou não.

Inclui um argumento variável booleano "_\_adjust_", que exibe as taxas como uma % da coleta total, se for definida como verdadeira, ou como uma % da taxa total, se for definida como falsa.

```solidity
function getFees(address _strategy) external view returns (FeeCategory memory) {
    return getFeeCategory(stratFeeId[_strategy], false);
}

function getFees(address _strategy, bool _adjust) external view returns (FeeCategory memory) {
    return getFeeCategory(stratFeeId[_strategy], _adjust);
}
```

### getFeeCategory()

Retorna uma estrutura _FeeCategory_ para um número integral específico de identificação da estratégia, como descrito acima. Também inclui a opção de variável booleana "_\_adjust_".

```solidity
function getFeeCategory(uint256 _id, bool _adjust) public view returns (FeeCategory memory fees) {
    uint256 id = feeCategory[_id].active ? _id : 0;
    fees = feeCategory[id];
    if (_adjust) {
        uint256 _totalFee = fees.total;
        fees.beefy = fees.beefy * _totalFee / DIVISOR;
        fees.call = fees.call * _totalFee / DIVISOR;
        fees.strategist = fees.strategist * _totalFee / DIVISOR;
    }
}
```

## Funções Write

### setStratFeeId()

Atualiza o mapeamento de _stratFeeId_ para mostrar em última instância qual estrutura de _FeeCategory_ está sendo usada por uma determinada estratégia, por meio de um mapeamento de _feeCategory_ intermediária e valores inteiros de _feeId_.

Isto inclui 3 opções, incluindo uma para a estratégia de atualizar sua própria _feeId_, uma para estipular o endereço da estratégia e a _feeId_ como argumentos, e uma para definir uma gama de estratégias, dando tanto uma série de endereços de estratégia quanto uma série de _feeIds_ como argumentos. Cada uma das três, então, usa a função interna _\_setStratFeeId()_ para atualizar cada estratégia.

```solidity
function setStratFeeId(uint256 _feeId) external {
_setStratFeeId(msg.sender, _feeId);
}

function setStratFeeId(address _strategy, uint256 _feeId) external onlyManager {
    _setStratFeeId(_strategy, _feeId);
}

function setStratFeeId(address[] memory _strategies, uint256[] memory _feeIds) external onlyManager {
    uint256 stratLength = _strategies.length;
    for (uint256 i = 0; i < stratLength; i++) {
        _setStratFeeId(_strategies[i], _feeIds[i]);
    }
}

function _setStratFeeId(address _strategy, uint256 _feeId) internal {
    stratFeeId[_strategy] = _feeId;
    emit SetStratFeeId(_strategy, _feeId);
}
```

### setFeeCategory()

Define os parâmetros para uma determinada estrutura da _FeeCategory_ (nova ou existente), incluindo a divisão das taxas entre a Beefy, o chamador da coleta e o estrategista.

```solidity
function setFeeCategory(
    uint256 _id,
    uint256 _total,
    uint256 _call,
    uint256 _strategist,
    string memory _label,
    bool _active,
    bool _adjust
) external onlyOwner {
    require(_total <= totalLimit, ">totalLimit");
    if (_adjust) {
        _call = _call * DIVISOR / _total;
        _strategist = _strategist * DIVISOR / _total;
    }
    uint256 beefy = DIVISOR - _call - _strategist;
    FeeCategory memory category = FeeCategory(_total, beefy, _call, _strategist, _label, _active);
    feeCategory[_id] = category;
    emit SetFeeCategory(_id, _total, beefy, _call, _strategist, _label, _active);
}
```

### setKeeper()

Atualiza o encarregado nomeado no contrato da FeeConfigurator.

```solidity
function setKeeper(address _keeper) external onlyManager {
    keeper = _keeper;
    emit SetKeeper(_keeper);
}
```

### pause() / unpause()

Define uma FeeCategory específica (usando o ID da categoria como argumento) para ativa ("unpaused") - significando que uma estratégia definida para aquela categoria usará aquela categoria - ou inativa ("paused") - significando que a estratégia voltará à configuração padrão da taxa.

```solidity
function pause(uint256 _id) external onlyManager {
    feeCategory[_id].active = false;
    emit Pause(_id);
}

function unpause(uint256 _id) external onlyManager {
    feeCategory[_id].active = true;
    emit Unpause(_id);
}
```

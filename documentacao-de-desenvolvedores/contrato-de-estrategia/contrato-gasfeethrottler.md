---
description: Tradução feita a partir da atualização de fevereiro de 2023
---

# Contrato GasFeeThrottler

O Contrato [GasFeeThrottler](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/utils/GasFeeThrottler.sol) (antigo GasThrottler) é um dispositivo de contrato inteligente usado para garantir que os preços do gás para transações de contrato infantil sempre caiam abaixo de um máximo fixo, ou de outra forma faça com que a transação seja revertida. Para isso, ele aponta para um [Contrato de Preço de Gás](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/utils/GasPrice.sol) específico, onde o preço máximo do gás pode ser configurado pelo proprietário do contrato. O GasFeeThrottler é incorporado em todos os [.](./ "mention").

## GasFeeThrottler.sol

O contrato Throttler tem três elementos principais que são herdados por seus contratos infantis:

1. a **variável shouldGasThrottle** - que é booleana fixada para "verdadeira" para indicar que um contrato infantil herdou a restrição de gás;
2. a **variável GasPrice** - que conecta o Throttler ao [#gasprice.sol](contrato-gasfeethrottler.md#gasprice.sol "mention") para identificar o preço máximo do gás fixado por esse contrato e;
3. o **modificador gasThrottle()** - que exige que os preços do gás para transações decorrentes das funções modificadas do contrato infantil sejam sempre iguais ou inferiores ao preço máximo fixo do gás.

```solidity
contract GasFeeThrottler {

    bool public shouldGasThrottle = true;

    address public gasprice = address(0xA43509661141F254F54D9A326E8Ec851A0b95307);

    modifier gasThrottle() {
        if (shouldGasThrottle && Address.isContract(gasprice)) {
            require(tx.gasprice <= IGasPrice(gasprice).maxGasPrice(), "gas is too high!");
        }
        _;
    }
}
```

## GasPrice.sol

O contrato GasPrice fornece três elementos fundamentais para facilitar seu propósito:

1. a **variável maxGasPrice** - que armazena o valor do preço máximo atual do gás definido pelo contrato, e pode ser chamada externamente usando a interface [IGasPrice.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/utils/IGasPrice.sol);
2. um **evento NewMaxGasPrice** - que é acionado em mudanças na variável maxGasPrice, e retorna os preços antigo e novo para referência externa e;
3. a **função setMaxGasPrice** - que aceita um valor inteiro para o novo \_maxGasPrice como argumento, emite o evento NewMaxGasPrice e atualiza a variável maxGasPrice.

```solidity
contract GasPrice is Ownable {

    uint public maxGasPrice = 10000000000;

    event NewMaxGasPrice(uint oldPrice, uint newPrice);

    function setMaxGasPrice(uint _maxGasPrice) external onlyOwner {
        emit NewMaxGasPrice(maxGasPrice, _maxGasPrice);
        maxGasPrice = _maxGasPrice;
    }
}
```

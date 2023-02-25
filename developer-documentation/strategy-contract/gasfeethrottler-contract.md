---
description: 'Last Update: February 2023'
---

# GasFeeThrottler Contract

The [GasFeeThrottler Contract](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/utils/GasFeeThrottler.sol) (formerly GasThrottler) is a smart contract device used to ensure that gas prices for child contract transactions always fall below a fixed maximum, or otherwise causes the transaction to be reverted. To do so, it points to a specific [GasPrice Contract](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/utils/GasPrice.sol), where the maximum gas price can be configured by the contract's owner. The GasFeeThrottler is incorporated into every [.](./ "mention").

## GasFeeThrottler.sol

The throttler contract has three main elements which are inherited by its child contracts:

1. the **shouldGasThrottle variable** - which is boolean fixed to _"true"_ to indicate that a child contract has inherited gas throttling;
2. the **gasPrice variable** - which connects the throttler to [#gasprice.sol](gasfeethrottler-contract.md#gasprice.sol "mention") to identify the max gas price fixed by that contract; and
3. the **gasThrottle() modifier** - which requires that gas prices for transactions arising from the child contract's modified functions always are equal to or below the fixed max gas price.

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

The GasPrice contract provides three core elements to facilitate its purpose:

1. the **maxGasPrice variable** - which stores the current maximum gas price value set by the contract, and can be called externally using the [IGasPrice.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/utils/IGasPrice.sol) interface;
2. a **NewMaxGasPrice event** - which is triggered on changes to the maxGasPrice variable, and returns the old and new prices for external reference; and
3. the **setMaxGasPrice function** - which accepts an integer value for the new \_maxGasPrice as an argument, emits the NewMaxGasPrice event and updates the maxGasPrice variable.

<pre class="language-solidity"><code class="lang-solidity">contract GasPrice is Ownable {

    uint public maxGasPrice = 10000000000;

    event NewMaxGasPrice(uint oldPrice, uint newPrice);
<strong>
</strong><strong>    function setMaxGasPrice(uint _maxGasPrice) external onlyOwner {
</strong>        emit NewMaxGasPrice(maxGasPrice, _maxGasPrice);
        maxGasPrice = _maxGasPrice;
    }
}
</code></pre>


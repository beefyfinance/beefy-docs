---
description: 'Last Update: February 2023'
---

# FeeConfigurator Contract

The [BeefyFeeConfigurator Contract](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/infra/BeefyFeeConfigurator.sol) is an infrastructure contract hosted on each of the blockchains which Beefy has deployed on. The contract manages the configuration of fees for each strategy on the relevant chain, which the [stratfeemanager-contract.md](../strategy-contract/stratfeemanager-contract.md "mention") interfaces with through [IFeeConfig.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/interfaces/common/IFeeConfig.sol).

The relevant address for the FeeConfigurator Contract (_"beefyFeeConfig"_) on each chain is displayed in the Beefy API using the [#get-config](../beefy-api.md#get-config "mention") endpoint.

## Modifier

Includes a standard _onlyManager()_ modifier to control access to write functions.&#x20;

```solidity
modifier onlyManager() {
    require(msg.sender == owner() || msg.sender == keeper, "!manager");
    _;
}
```

## View Functions

### getFees()

Returns a _FeeCategory_ structure for a specific strategy address argument, displaying the total fees charged, the fees for Beefy, the harvest caller and the strategist, a string showing the description of the type of fee category, and _"active"_ boolean variable, showing whether the fee category is switched on or not.&#x20;

Includes an _"\_adjust"_ boolean variable argument, which displays fees as a % of the total harvest if set to true, or as a % of the total fee if set to false.

{% code overflow="wrap" %}
```solidity
function getFees(address _strategy) external view returns (FeeCategory memory) {
    return getFeeCategory(stratFeeId[_strategy], false);
}

function getFees(address _strategy, bool _adjust) external view returns (FeeCategory memory) {
    return getFeeCategory(stratFeeId[_strategy], _adjust);
}
```
{% endcode %}

### getFeeCategory()

Returns a _FeeCategory_ structure for a specific strategy ID integer, as described above. Also includes the _"\_adjust"_ boolean variable option.

{% code overflow="wrap" %}
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
{% endcode %}

## Write Functions

### setStratFeeId()

Updates the _stratFeeId_ mapping to show ultimately what _FeeCategory_ structure is being used by a particular strategy, by way of an intermediate _feeCategory_ mapping and _feeId_ integer values.

This includes 3 options, including one for the strategy to update its own _feeId_, one to stipulate the strategy address and _feeId_ as arguments, and one to set a range of strategies by giving both an array of strategy addresses and an array of _feeIds_ as arguments. Each of the three then use the internal _\_setStratFeeId()_ function to update each strategy.

<pre class="language-solidity"><code class="lang-solidity">function setStratFeeId(uint256 _feeId) external {
_setStratFeeId(msg.sender, _feeId);
}

function setStratFeeId(address _strategy, uint256 _feeId) external onlyManager {
<strong>    _setStratFeeId(_strategy, _feeId);
</strong>}

function setStratFeeId(address[] memory _strategies, uint256[] memory _feeIds) external onlyManager {
    uint256 stratLength = _strategies.length;
    for (uint256 i = 0; i &#x3C; stratLength; i++) {
        _setStratFeeId(_strategies[i], _feeIds[i]);
    }
}

function _setStratFeeId(address _strategy, uint256 _feeId) internal {
    stratFeeId[_strategy] = _feeId;
    emit SetStratFeeId(_strategy, _feeId);
}
</code></pre>

### setFeeCategory()

Sets the parameters for a given _FeeCategory_ structure (new or existing), including the split in fees between Beefy, the harvest caller and the strategist.

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

Updates the named keeper in the FeeConfigurator contract.

```solidity
function setKeeper(address _keeper) external onlyManager {
    keeper = _keeper;
    emit SetKeeper(_keeper);
}
```

### pause() / unpause()

Sets a specific FeeCategory (using the category ID as an argument) to either active ("unpaused") - meaning a strategy set to that category will use that category - or inactive ("paused") - meaning the strategy will revert to the default fee configuration.&#x20;

<pre class="language-solidity"><code class="lang-solidity">function pause(uint256 _id) external onlyManager {
<strong>    feeCategory[_id].active = false;
</strong>    emit Pause(_id);
}

function unpause(uint256 _id) external onlyManager {
    feeCategory[_id].active = true;
    emit Unpause(_id);
}
</code></pre>

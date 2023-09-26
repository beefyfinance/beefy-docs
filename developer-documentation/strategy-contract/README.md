---
description: 'Last Update: February 2023'
---

# Strategy Contract

[Strategy Contracts](https://github.com/beefyfinance/beefy-contracts/tree/master/contracts/BIFI/strategies) are the primary driver of Beefy's investment model, which facilitate the autocompounding of yield farm rewards. Beefy's process has three key steps: (1) staking deposited tokens in the relevant farms; (2) harvesting rewards; and (3) swapping rewards for more deposit tokens and reinvesting the proceeds

Each strategy contract is ultimately dependent on a [vault-contract.md](../vault-contract.md "mention") for the capital they deploy, and do not have any direct interaction with ordinary users. The vault and strategy contracts are kept separate to isolate any risks in the strategy from user deposits.

## Dependencies

All Beefy strategies rely on a range of dependencies and interfaces which are imported into the strategy contract on deployment. The core dependencies, which allow the strategy to inherit a range of functionality are:

* the [stratfeemanager-contract.md](stratfeemanager-contract.md "mention"); and
* the [gasfeethrottler-contract.md](gasfeethrottler-contract.md "mention").

## Interfaces

The key interfaces which allow the strategy to interact with third party contracts are:

* **the router contract interface** - which allows for swaps between the different tokens involved in the autocompounding process (e.g. IUniswapRouterETH.sol);
* **the liquidity pool contract interface** - which is the underlying pool that our vaults provide liquidity to and that the farms are built on top of (e.g. IUniswapV2Pair.sol); and
* **the chef contract interface** - the farm which is issuing rewards for providing liquidity (e.g. IMiniChefV2.sol).

## View Functions

### balanceOf() / balanceOfWant()

Checks the amount of the underlying farm token (or "want") stored in the strategy. Returns the specific amount of tokens.

```solidity
function balanceOf() public view returns (uint256) {
    return balanceOfWant() + balanceOfPool();
}

function balanceOfWant() public view returns (uint256) {
    return IERC20(want).balanceOf(address(this));
}
```

### balanceOfPool()

Checks the amount of underlying farm token (or "want") stored in the chef contract. Returns the specific amount of tokens.

```solidity
function balanceOfPool() public view returns (uint256) {
    (uint256 _amount, ) = IMiniChefV2(chef).userInfo(poolId, address(this));
    return _amount;
}
```

### rewardsAvailable()

Checks the amount of pending rewards held by the chef contract capable of being claimed by the strategy contract. Returns the specific amount of tokens.

```solidity
function rewardsAvailable() public view returns (uint256) {
    return IMiniChefV2(chef).pendingSushi(poolId, address(this));
}
```

### callReward()

Most strategies include a _callReward()_ function, which is used to determine the amount of "native" token rewards available to the _harvest()_ caller.

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

## Write Functions

### deposit()

Deposits the underlying farm token (or "want") into in the farm by way of the connected chef contract. First checks that the strategy is holding some of the underlying farm token (or "want") before depositing the entire balance in the chef.

<pre class="language-solidity"><code class="lang-solidity"><strong>function deposit() public whenNotPaused {
</strong>    uint256 wantBal = IERC20(want).balanceOf(address(this));
    if (wantBal > 0) {
        IMiniChefV2(chef).deposit(poolId, wantBal, address(this));
        emit Deposit(balanceOf());
    }
}
</code></pre>

### withdraw()

External function called by the vault to facilitate user withdrawals. First checks that the balance of the underlying farm token (or "want") is sufficient to fulfil the request, and then withdraws that amount from the chef contract, before transferring back to the vault contract.

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

Harvest invokes the compounding of the vault for all users. Specifically, this harvests from the chef contract, charges fees on the harvest and then deposits the harvested rewards back into the farm to achieve the autocompounding effect.

This function is completely decentralized, meaning that anyone is able to call the function, and can earn a reward between 0.05 - 0.5% of the total yield. This can be called by any one of three methods, detailed below.

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

Internal method to charge fees on every [#harvest](./#harvest "mention") call, by swapping the native token in the strategy to the output token via the router contract.  The contract then calculates the output for the different fee recipient and transfers the output tokens according to the allocation. The recipients are the harvest caller, the strategist who deployed the contract and the Beefy treasury.

{% code overflow="wrap" %}
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
{% endcode %}

### addLiquidity()

Internal method to add liquidity to the underlying pool for the farm as part of the [#harvest](./#harvest "mention") function. Swaps the output token to the underlying tokens of the farm, and then adds both to the liquidity pool to obtain the underlying farm deposit token (or "want"). The remainder of the _harvest()_ call then deposits these tokens in the farm.

{% code overflow="wrap" %}
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
{% endcode %}

### setHarvestOnDeposit()

Most Beefy vaults [harvest on deposit](../../beefy-products/vaults.md#what-is-harvesting-on-deposit). This means that, before the user's funds enter the strategy, the yield on the entire vault is harvested and reinvested. This prevents new depositors from stealing the yield of existing depositors. As a result, any vault that is set to harvest on deposit is able to remove the withdrawal fee completely.

_harvestOnDeposit_ is a boolean variable which is set to true when the vault is harvesting on deposit. This is toggled by the _setHarvestOnDeposit()_ function, set out below:

<pre class="language-solidity"><code class="lang-solidity">bool public harvestOnDeposit;

function setHarvestOnDeposit(bool _harvestOnDeposit) external onlyManager {
    harvestOnDeposit = _harvestOnDeposit;
    if (harvestOnDeposit) {
        setWithdrawalFee(0);
<strong>    } else {
</strong>        setWithdrawalFee(10);
    }
}
</code></pre>

### beforeDeposit()

External function used to facilitate harvests on deposit, if active.  Checks first that harvest on deposit is active and that the caller is the vault, before harvesting.

```solidity
function beforeDeposit() external override {
    if (harvestOnDeposit) {
        require(msg.sender == vault, "!vault");
        _harvest(tx.origin);
    }
}
```

### panic()

Beefy does not directly touch any user funds held in the protocol. During times of uncertainty or upgrades to the underlying yield farm, Beefy can withdraw all funds out of third party contracts and hold them safely in the strategy using the _panic()_ function. By "panicking" the strategy, users remain able to withdraw their funds from the vault without any delay or exposure to third party risks. This function also removes all allowances to both the UniRouter and the underlying yield farm contract, to ensure no funds can be withdrawn by those contracts.

```solidity
function panic() public onlyManager {
    pause();
    IMiniChefV2(chef).emergencyWithdraw(poolId, address(this));
}
```

### pause() / unpause()

All Beefy strategies are pausable, meaning that functionality can be halted during the strategy's ordinary operations by the strategy manager. This is inherited through [StratManager.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Common/StratManager.sol), and relies on the standard [Pausable.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/security/Pausable.sol) abstract contract. This function also removes all allowances to both the UniRouter and the underlying yield farm contract, to ensure no funds can be withdrawn by those contracts.

```solidity
function pause() public onlyManager {
    _pause();
    _removeAllowances();
}
```

In the reverse, strategies can also be unpaused, by reversing the actions in the pause function.

```solidity
function unpause() external onlyManager {
    _unpause();
    _giveAllowances();
    deposit();
}
```

The functions affected by a pause in most strategy contracts are [#deposit](./#deposit "mention"), [#withdraw](./#withdraw "mention") and [#harvest](./#harvest "mention").

### \_giveAllowances / \_removeAllowances()

Internal functions used to set and remove all allowances with third party contracts, to control whether third party contracts have the necessary permissions to withdraw funds from the strategy. The relevant contracts are the underlying farm token/_want()_ (e.g. LP token), the strategy output token (often the same as the _want()_), the native chain token (used for gas) and the underlying tokens used for the farm.

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

External function used as part of a migration from one strategy to another. This effectively closes down the strategy by withdrawing all funds and transferring them back to the vault. It can only be triggered by a call from the vault contract.

```solidity
function retireStrat() external {
    require(msg.sender == vault, "!vault");
    IMiniChefV2(chef).emergencyWithdraw(poolId, address(this));
    uint256 wantBal = IERC20(want).balanceOf(address(this));
    IERC20(want).transfer(vault, wantBal);
}
```

---
description: 'Last Update: February 2023'
---

# Strategy Contract

Strategy Contracts are the primary driver of Beefy's investment model, which facilitate the autocompounding of yield farm rewards. Beefy's process has three key steps: (1) staking deposited tokens in the relevant farm; (2) harvesting rewards; (3) swapping rewards for more deposit tokens and reinvesting the proceeds.

Besides handling deposits and withdrawals, the primary function of the vault is to direct deposited funds to the relevant autocompounding [.](./ "mention"). The vault and strategy contracts are kept separate to isolate any risks in the strategy from user deposits.

## Dependencies & Interfaces

All Beefy strategies rely on a range of dependencies and interfaces which are imported into the strategy contract on deployment. The core dependencies, which allow the strategy to inherit a range of functionality are:

* StratFeeManagerInitializable.sol and
* GasFeeThrottler.sol

The key interfaces which allow the strategy to interact with third party contracts are:

* The router contract (e.g. IUniswapRouterETH.sol) - which allows for swaps between the different tokens involved in the autocompounding process;
* The liquidity pool contract (e.g. IUniswapV2Pair.sol) - which is the underlying pool that our vaults provide liquidity to and that the farms are built on top of; and
* The chef contract (e.g. IMiniChefV2.sol) - the farm which is issuing rewards for providing liquidity.

## View Functions

### balanceOf() / balanceOfWant()

Checks the amount of the underlying farm token (or "want") stored in the strategy. Returns the specific amount of tokens.

```solidity
function balanceOf() public view returns (uint256) {
    return balanceOfWant().add(balanceOfPool());
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
function callReward() public view returns (uint256) {
    uint256 outputBal = rewardsAvailable();
    uint256 nativeOut;
    if (outputBal > 0) {
        try IUniswapRouterETH(unirouter).getAmountsOut(outputBal, outputToNativeRoute)
            returns (uint256[] memory amountOut) 
        {
            nativeOut = amountOut[amountOut.length -1];
        }
        catch {}
    }
    return nativeOut.mul(45).div(1000).mul(callFee).div(MAX_FEE);
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
    if (tx.origin == owner() || paused()) {
        IERC20(want).safeTransfer(vault, wantBal);
    } else {
        uint256 withdrawalFeeAmount = wantBal.mul(withdrawalFee).div(WITHDRAWAL_MAX);	
        IERC20(want).safeTransfer(vault, wantBal.sub(withdrawalFeeAmount));
    }
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
    if (outputBal > 0) {
        chargeFees(callFeeRecipient);
        addLiquidity();
        uint256 wantHarvested = balanceOfWant();
        deposit();
        emit StratHarvest(msg.sender, wantHarvested, balanceOf());
        lastHarvest = block.timestamp;
    }
}
```

### chargeFees()

Internal method to charge fees on every [#harvest](./#harvest "mention") call, by swapping the native token in the strategy to the output token via the router contract.  The contract then calculates the output for the different fee recipient and transfers the output tokens according to the allocation. The recipients are the harvest caller, the strategist who deployed the contract and the Beefy treasury.

{% code overflow="wrap" %}
```solidity
function chargeFees(address callFeeReciepient) internal {
    uint256 toOutput = IERC20(native).balanceOf(address(this));
    if (toOutput > 0) {
        IUniswapRouterETH(unirouter).swapExactTokensForTokens(
            toOutput, 0, nativeToOutputRoute, address(this), now
        );
    }        
    uint256 toNative = IERC20(output).balanceOf(address(this)).mul(45).div(1000);
    IUniswapRouterETH(unirouter).swapExactTokensForTokens(
        toNative, 0, outputToNativeRoute, address(this), now
    );
    uint256 nativeBal = IERC20(native).balanceOf(address(this));
    uint256 callFeeAmount = nativeBal.mul(callFee).div(MAX_FEE);
    IERC20(native).safeTransfer(callFeeReciepient, callFeeAmount);
    uint256 beefyFeeAmount = nativeBal.mul(beefyFee).div(MAX_FEE);
    IERC20(native).safeTransfer(beefyFeeRecipient, beefyFeeAmount);
    uint256 strategistFee = nativeBal.mul(STRATEGIST_FEE).div(MAX_FEE);
    IERC20(native).safeTransfer(strategist, strategistFee);
}
```
{% endcode %}

### addLiquidity()

Internal method to add liquidity to the underlying pool for the farm as part of the [#harvest](./#harvest "mention") function. Swaps the output token to the underlying tokens of the farm, and then adds both to the liquidity pool to obtain the underlying farm deposit token (or "want"). The remainder of the _harvest()_ call then deposits these tokens in the farm.

{% code overflow="wrap" %}
```solidity
function addLiquidity() internal {
    uint256 outputHalf = IERC20(output).balanceOf(address(this)).div(2);
    if (lpToken0 != output) {
        IUniswapRouterETH(unirouter).swapExactTokensForTokens(
            outputHalf, 0, outputToLp0Route, address(this), now
        );
    }
    if (lpToken1 != output) {
        IUniswapRouterETH(unirouter).swapExactTokensForTokens(
            outputHalf, 0, outputToLp1Route, address(this), now
        );
    }
    uint256 lp0Bal = IERC20(lpToken0).balanceOf(address(this));
    uint256 lp1Bal = IERC20(lpToken1).balanceOf(address(this));
    IUniswapRouterETH(unirouter).addLiquidity(
        lpToken0, lpToken1, lp0Bal, lp1Bal, 1, 1, address(this), now
    );
}
```
{% endcode %}

### setHarvestOnDeposit()

Most Beefy vaults [harvest on deposit](../../products/vaults.md#what-is-harvesting-on-deposit). This means that, before the user's funds enter the strategy, the yield on the entire vault is harvested and reinvested. This prevents new depositors from stealing the yield of existing depositors. As a result, any vault that is set to harvest on deposit is able to remove the withdrawal fee completely.

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
    IERC20(want).safeApprove(chef, uint256(-1));
    IERC20(output).safeApprove(unirouter, uint256(-1));
    IERC20(native).safeApprove(unirouter, uint256(-1));
    IERC20(lpToken0).safeApprove(unirouter, 0);
    IERC20(lpToken0).safeApprove(unirouter, uint256(-1));
    IERC20(lpToken1).safeApprove(unirouter, 0);
    IERC20(lpToken1).safeApprove(unirouter, uint256(-1));
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

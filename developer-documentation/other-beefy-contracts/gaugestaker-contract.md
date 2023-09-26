---
description: 'Last Update: June 2022'
---

# GaugeStaker Contract

## What is the GaugeStaker? <a href="#what-is-the-gaugestaker" id="what-is-the-gaugestaker"></a>

The [GaugeStaker contract](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Gauge/GaugeStaker.sol) is the central smart contract for the [binSPIRIT](../../beefy-products/beefy-escrowed-tokens/binspirit.md) token, which manages both the collection of SpiritSwap protocol revenue for inSPIRIT holders and the delivery of inSPIRIT farm boosts to other Beefy SpiritSwap vaults.

## How does the GaugeStaker work?

The GaugeStaker has three notable roles: (1) managing user SPIRIT deposits to accumulate inSPIRIT rewards; (2) managing voting for SpiritSwap boosted farms; and (3) passing tokens between other Beefy SpiritSwap strategies and boosted farming gauges.&#x20;

When users deposit SPIRIT, the GaugeStaker will automatically stake the SPIRIT with SpiritSwap to receive non-transferrable inSPIRIT. All staked SPIRIT must also be locked (so cannot be withdrawn), so the GaugeStaker locks all deposits for the longest possible period of time (currently 4 years) to receive the maximum amount of inSPIRIT. Protocol revenue rewards accrue constantly on the locked SPIRIT, and the GaugeStaker automatically claims these rewards and returns them to the [Beefy binSPIRIT vault](https://app.beefy.finance/#/vault/beefy-binspirit) on a regular basis, where they are automatically compounded.

Holders of inSPIRIT are also entitled to [vote](../../beefy-products/beefy-escrowed-tokens/binspirit.md#can-i-vote-with-binspirit) in SpiritSwap governance and for the distribution of boosted farm rewards, so the GaugeStaker manages the allocation of these votes.&#x20;

Finally, inSPIRIT holders also received boosted rewards on selected SpiritSwap farms. All boosted Beefy SpiritSwap vaults are configured to pass all of their deposits, withdrawals and harvesting of rewards through the GaugeStaker, to receive the benefits of the boost. This provides the highest possible boost across each of the farms, as the GaugeStaker holds the full concentration of Beefy's accumulated inSPIRIT.

## GaugeStaker Functionality

The GaugeStaker contract incorporates a range of different functionality and methods to execute its two roles. These include:

### Deposit SPIRIT to mint binSPIRIT

A user can deposit SPIRIT (`want`) and the contract will confirm the amount that is received by checking balances before and after the transfer. If the received amount is non-zero then check if an existing lock for SPIRIT exists, which it likely will unless the lock has not been initiated before or has been left to expire. If the lock exists then it will extended out to the full 4 years if the current lock time is less than the full amount, and the received balance of SPIRIT is locked to get a 1:1 amount of inSPIRIT. If no lock currently exists then create a new one and lock the balance of SPIRIT on the contract. Finally mint an equal amount of binSPIRIT as the received balance of SPIRIT from the user.

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

### Vote on which gauges to boost

The Beefy Keeper can vote on gauge incentives using the inSPIRIT balance on the GaugeStaker as voting power. It will be mainly used to vote for Beefy and strategic partner's gauges, and can be governed by Beefy DAO to vote for various incentives on gauges. The voting function is a simple call to SpiritSwap's Gauge Proxy contract which records the votes and decides the distribution of gauge incentives. The Beefy keeper can split the voting power between multiple gauges in a single call using the parameter arrays.

```solidity
// vote on boosted farms
function vote(address[] calldata _tokenVote, uint256[] calldata _weights) external onlyManager {    
    gaugeProxy.vote(_tokenVote, _weights);    
    emit Vote(_tokenVote, _weights);
}
```

### Pass through tokens between strategies and gauges

Strategies for Beefy's SpiritSwap vaults must pass through their deposits, withdrawals and harvests to and from the GaugeStaker. Only a whitelisted strategy can interact with the GaugeStaker, and each gauge is assigned at most one strategy.

Deposits and withdrawals pass through the exact amount that is requested (`_amount`) in the token that is assigned to the gauge (`_underlying`). Harvests (`claimGaugeReward()`) pass through only the SPIRIT (`want`) reward that's received by the GaugeStaker when claiming the reward, ignoring the existing balance on the GaugeStaker. None of the funds are kept on the GaugeStaker, they are always passed across in the same transaction.

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

### Claim SpiritSwap protocol fees

Holding inSPIRIT gives the GaugeStaker the right to claim a portion of SpiritSwap's protocol fees, which will be distributed to binSPIRIT stakers in a reward pool. The protocol fees are distributed once a week in the form of SPIRIT and need to be claimed from the Fee Distributor contract. The Reward Pool contract will call the claim function via `claimVeWantReward()`. Only the SPIRIT (`want`) reward is immediately passed back to the Reward Pool, if there is anything available to claim.

```solidity
// pass through rewards from the fee distributor
function claimVeWantReward() external onlyRewardPool {    
    uint256 _before = balanceOfWant();    
    feeDistributor.claim();    
    uint256 _balance = balanceOfWant().sub(_before);    
    want.safeTransfer(msg.sender, _balance);
}
```

### Whitelisting strategies

The Beefy Keeper can whitelist a strategy address as long as there isn't an active strategy that has funds deployed in the same gauge as the new strategy. An old strategy must be panicked before a new strategy for the same gauge can be tested, so user funds are always protected. The approval for the token (`_want`) assigned to the gauge is reset and increased to the max limit for spending by the gauge. The gauge is mapped to the whitelisted strategy and the strategy is allowed access to the GaugeStaker for the specified gauge.

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

### Upgrading strategies

A new strategy for a gauge with an existing strategy can be proposed once it has been fully tested. `proposeStrategy()` should be called on the GaugeStaker before `upgradeStrat()` on the vault so the switch will succeed. The new strategy must have the same gauge as the previous strategy. `upgradeStrategy()` is only called in `retireStrat()` on the previous strategy, so is controlled indirectly by the vault owner through upgrading the strategy address on the vault.

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

## Contracts <a href="#contracts" id="contracts"></a>

* binSPIRIT/GaugeStaker: [0x44e314190D9E4cE6d4C0903459204F8E21ff940A](https://ftmscan.com/address/0x44e314190D9E4cE6d4C0903459204F8E21ff940A)
* Reward Pool: [0xFAE44b30F6F9BbD44E6B7687471dd73D71FaBDC6](https://ftmscan.com/address/0xFAE44b30F6F9BbD44E6B7687471dd73D71FaBDC6)

Critical functions are always managed via multi-sig transactions and timelocks. No funds are stored directly on the GaugeStaker and only the active whitelisted strategy can interact with funds stored in a gauge.

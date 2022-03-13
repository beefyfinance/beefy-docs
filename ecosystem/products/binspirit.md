---
description: Beefy wrapped SPIRIT.
---

# binSPIRIT

## Introduction

### What is inSPIRIT?

When users lock their SPIRIT tokens in SpiritSwap for between 1 week and four years, they receive a proportional amount of inSPIRIT. inSPIRIT is non-transferrable and the amount in the holder's wallet decreases steadily to 0 when the lock is over. inSPIRIT holders can claim protocol revenue fees (variable week by week but have been up to 80% APR) and receive up to a 2.5x boost in farms. The boost depends on the user's balance of inSPIRIT compared to all other holders and the balance they have staked in the farm compared with the farm’s TVL. You also will not be able to liquidate your position until the end of the time lock.

### What is binSPIRIT?

binSPIRIT is the Beefy wrapped version of SPIRIT, allowing holders to earn SpiritSwap protocol fees without having to lock their SPIRIT. A user can mint binSPIRIT 1:1 using SPIRIT through the UI on the binSPIRIT vault page. If it is more profitable to buy binSPIRIT then Beefy's Smart Minter will do exactly that, yielding the user more binSPIRIT for their SPIRIT:

![beMINT determines the most profitable strategy](../../.gitbook/assets/binspirit\_mint.jpg)

Users can also get binSPIRIT by buying on a DEX. binSPIRIT can be staked in the Beefy vault for more binSPIRIT, or directly in the reward pool to receive SPIRIT.&#x20;

The SPIRIT used to mint binSPIRIT is locked for inSPIRIT. Beefy uses this inSPIRIT to boost all Beefy SpiritSwap vaults and vote for incentive emissions.

### How does binSPIRIT keep its peg?

Should a user want to liquidate their position they will be able to trade binSPIRIT on an exchange. Unlike inSPIRIT, users are never locked in and can leave anytime. This also means that binSPIRIT may not always be pegged to SPIRIT, but will maintain a loose peg.&#x20;

If binSPIRIT goes under peg then the SpiritSwap protocol fees will buy back more binSPIRIT per SPIRIT and the Beefy vault APY will increase. APR for the reward pool would increase as well, allowing users to buy and stake binSPIRIT for a much larger proportion of the SpiritSwap protocol fees than just locking SPIRIT.

If binSPIRIT goes over peg then arbitrageurs will mint binSPIRIT and sell for a profit.

## How does the Gauge Staker work?

The Gauge Staker contract has two notable parts: locking SPIRIT to mint binSPIRIT and passing tokens between strategies and gauges. Locking the SPIRIT on the Gauge Staker allows the contract to obtain non-transferrable inSPIRIT. All SpiritSwap strategies for gauges will pass their deposits, withdrawals and harvest rewards through the Gauge Staker. Since all deposits are coming from the Gauge Staker address the highest boost can be obtained across all gauges as the contract also holds the concentrated inSPIRIT.

#### Deposit SPIRIT to mint binSPIRIT

A user can deposit SPIRIT (`want`) and the contract will confirm the amount that is received by checking balances before and after the transfer. If the received amount is non-zero then check if an existing lock for SPIRIT exists, which it likely will unless the lock has not been initiated before or has been left to expire. If the lock exists then it will extended out to the full 4 years if the current lock time is less than the full amount, and the received balance of SPIRIT is locked to get a 1:1 amount of inSPIRIT. If no lock currently exists then create a new one and lock the balance of SPIRIT on the contract. Finally mint an equal amount of binSPIRIT as the received balance of SPIRIT from the user.

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

#### Vote on which gauges to boost

The Beefy Keeper can vote on gauge incentives using the inSPIRIT balance on the Gauge Staker as voting power. It will be mainly used to vote for Beefy and strategic partner's gauges, and can be governed by Beefy DAO to vote for various incentives on gauges. The voting function is a simple call to SpiritSwap's Gauge Proxy contract which records the votes and decides the distribution of gauge incentives. The Beefy keeper can split the voting power between multiple gauges in a single call using the parameter arrays.

```
// vote on boosted farms
function vote(address[] calldata _tokenVote, uint256[] calldata _weights) external onlyManager {    
    gaugeProxy.vote(_tokenVote, _weights);    
    emit Vote(_tokenVote, _weights);
}
```

#### Pass through tokens between strategies and gauges

Strategies for Beefy's SpiritSwap vaults must pass through their deposits, withdrawals and harvests to and from the Gauge Staker. Only a whitelisted strategy can interact with the Gauge Staker, and each gauge is assigned at most one strategy.

Deposits and withdrawals pass through the exact amount that is requested (`_amount`) in the token that is assigned to the gauge (`_underlying`). Harvests (`claimGaugeReward()`) pass through only the SPIRIT (`want`) reward that's received by the Gauge Staker when claiming the reward, ignoring the existing balance on the Gauge Staker. None of the funds are kept on the Gauge Staker, they are always passed across in the same transaction.

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

Holding inSPIRIT gives the Gauge Staker the right to claim a portion of SpiritSwap's protocol fees, which will be distributed to binSPIRIT stakers in a reward pool. The protocol fees are distributed once a week in the form of SPIRIT and need to be claimed from the Fee Distributor contract. The Reward Pool contract will call the claim function via `claimVeWantReward()`. Only the SPIRIT (`want`) reward is immediately passed back to the Reward Pool, if there is anything available to claim.

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

The Beefy Keeper can whitelist a strategy address as long as there isn't an active strategy that has funds deployed in the same gauge as the new strategy. An old strategy must be panicked before a new strategy for the same gauge can be tested, so user funds are always protected. The approval for the token (`_want`) assigned to the gauge is reset and increased to the max limit for spending by the gauge. The gauge is mapped to the whitelisted strategy and the strategy is allowed access to the Gauge Staker for the specified gauge.

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

A new strategy for a gauge with an existing strategy can be proposed once it has been fully tested. `proposeStrategy()` should be called on the Gauge Staker before `upgradeStrat()` on the vault so the switch will succeed. The new strategy must have the same gauge as the previous strategy. `upgradeStrategy()` is only called in `retireStrat()` on the previous strategy, so is controlled indirectly by the vault owner through upgrading the strategy address on the vault.

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

## Contracts

* binSPIRIT/GaugeStaker: [0x44e314190D9E4cE6d4C0903459204F8E21ff940A](https://ftmscan.com/address/0x44e314190D9E4cE6d4C0903459204F8E21ff940A)
* Reward Pool: [0xFAE44b30F6F9BbD44E6B7687471dd73D71FaBDC6](https://ftmscan.com/address/0xFAE44b30F6F9BbD44E6B7687471dd73D71FaBDC6)

Critical functions are always managed via multi-sig transactions and timelocks. No funds are stored directly on the Gauge Staker and only the active whitelisted strategy can interact with funds stored in a gauge.

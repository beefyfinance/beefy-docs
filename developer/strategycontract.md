---
description: Strategy Contract
---

# Strategy Contract

## Important View Functions

### _Want_
```
function want() external view returns (IERC20);
```
Want refers to the underlying token used. 

### _Vault_
```
function vault() external view returns (address);
```
Vault refers to the Beefy Vault(AKA MooToken) that deposits into the strategy.

### _Balance Of_
```
function balanceOf() external view returns (uint256);
```

Balance Of is the amount of "want" stored in the strategy and yield source. This is the function read by the vault contract.

### _Call Reward_
```
function callReward() external view returns (uint256);
```
Most strategies will have a call reward function. This is to determine the amount of "native" token reward available to the harvest caller. 

### _Withdraw Fee_
```
function withdrawalFee() external view returns (uint256);
```
WithdrawalFee is a number up to 10 (max withdraw fee) that is divided by 10000 (.1%) to calculate the amount of withdraw fee to withhold on a user withdraw. 

### _Harvest On Deposit_
```
function harvestOnDeposit() external view returns (bool);
```
Most Beefy vaults harvest on deposit. What this means is that before the users funds enter the strat the whole vault yield is harvested and reinvested. This prevents new depositors from stealing the yields of existing depositors. Due to this any vault that is set to harvest on deposit is able to remove the withdrawFee completely. 


## Important Write Functions
### _Harvest_
``` 
function harvest() external;
```
Harvest invokes the compounding of the vault for all users. This function is completely decentralized to call and can earn a reward betweek .05-.5% of the total yield for the harvest caller. 

### _Panic_
```
function panic() external onlyManager;
```
Beefy cannot directly touch user funds. During times of uncertainity or upgrades to the underlying yield farm, Beefy can pull all funds out of the yield farm and keep them safely in the strategy using the panic function. This will allow users to withdraw without any issues. It also removes all allowances to both the unirouter and yield farm.

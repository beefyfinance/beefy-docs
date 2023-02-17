---
description: 'Last Update: February 2023'
---

# StratFeeManager Contract

The [StratFeeManager Contract](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Common/StratFeeManagerInitializable.sol) is collection of important dependencies which are imported and used in all Beefy Strategy Contracts.&#x20;

Originally, these dependencies were split into two contracts - [StratManager.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Common/StratManager.sol) and [FeeManager.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Common/FeeManager.sol). After the move to Solidity V0.8, the two were combined into a single contract - [StratFeeManager.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Common/StratFeeManager.sol). The current verison - [StratFeeManagerInitializable.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/strategies/Common/StratFeeManagerInitializable.sol) - facilitated a move to proxy clone strategies (which must be initialized with the relevant arguments for the strategy and its dependencies), to avoid the need to deploy every single strategy individually.

## Dependencies

The StratFeeManager contracts also introduce addition dependencies themselves, specifically [Ownable.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/Ownable.sol) - which introduces functionality to set a contract's owner and restrict functionality to them alone - and [Pausable.sol](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/security/Pausable.sol) - which introduces functionality to freeze functionality in a contract by putting the contract on pause. Both dependencies are ultimately included in every Beefy Strategy Contract.

## Modifiers

Introduces an _onlyManager()_ modifier to constrain functions to use by the strategy manager only.

```solidity
modifier onlyManager() {
    require(msg.sender == owner() || msg.sender == keeper, "!manager");
    _;
}
```

## View Functions

### getFees()

Returns the value of all fees from the fee configuration contract.

```solidity
function getFees() internal view returns (IFeeConfig.FeeCategory memory) {
    return beefyFeeConfig.getFees(address(this));
}
```

### getAllFees()

Returns the value of all fees from the fee configuration contract, as well the dynamic deposit and withdrawal fees.

```solidity
function getAllFees() external view returns (IFeeConfig.AllFees memory) {
    return IFeeConfig.AllFees(getFees(), depositFee(), withdrawFee());
}
```

### getStratFeeId()

Returns the integer value of the strategy fee ID from the fee configuration contract.

```solidity
function getStratFeeId() external view returns (uint256) {
    return beefyFeeConfig.stratFeeId(address(this));
}
```

## Write Functions

### setStratFeeId()

Sets a new integer value for the strategy's fee ID, which indicates the relevant fee for the strategy.

```solidity
function setStratFeeId(uint256 _feeId) external onlyManager {
    beefyFeeConfig.setStratFeeId(_feeId);
    emit SetStratFeeId(_feeId);
}
```

### setWithdrawalFee()

Sets a new integer value for the contract's withdrawal fee which is charged on each harvest.

```solidity
function setWithdrawalFee(uint256 _fee) public onlyManager {
    require(_fee <= WITHDRAWAL_FEE_CAP, "!cap");
    withdrawalFee = _fee;
    emit SetWithdrawalFee(_fee);
}
```

### setVault()

Sets a new address for the contract's vault, which manages user funds.

```solidity
function setVault(address _vault) external onlyOwner {
    vault = _vault;
    emit SetVault(_vault);
}
```

### setUnirouter()

Sets a new address for the contract's router which processes swaps within the contract.

```solidity
function setUnirouter(address _unirouter) external onlyOwner {
    unirouter = _unirouter;
    emit SetUnirouter(_unirouter);
}
```

### setKeeper()

Sets a new address for the contract's keeper, who can "panic" the strategy.

```solidity
function setKeeper(address _keeper) external onlyManager {
    keeper = _keeper;
    emit SetKeeper(_keeper);
}
```

### setStrategist()

Sets a new address for the contract's strategist who receives the strategist fee.

```solidity
function setStrategist(address _strategist) external {
    require(msg.sender == strategist, "!strategist");
    strategist = _strategist;
    emit SetStrategist(_strategist);
}
```

### setBeefyFeeRecipient()

Sets a new address for the recipient of Beefy's fee on harvests, typically a Beefy treasury contract.

```solidity
function setBeefyFeeRecipient(address _beefyFeeRecipient) external onlyOwner {
    beefyFeeRecipient = _beefyFeeRecipient;
    emit SetBeefyFeeRecipient(_beefyFeeRecipient);
}
```

### setBeefyFeeConfig()

Sets a new address for the fee configuration contract used by the strategy to fetch fees.

```solidity
function setBeefyFeeConfig(address _beefyFeeConfig) external onlyOwner {
    beefyFeeConfig = IFeeConfig(_beefyFeeConfig);
    emit SetBeefyFeeConfig(_beefyFeeConfig);
}
```


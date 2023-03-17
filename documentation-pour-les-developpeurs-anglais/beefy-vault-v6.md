# Beefy Vault V6

## Important View Functions

### _Want_

```
function want() external view returns (IERC20);
```

Want refers to the underlying token in both the Beefy Vault and Strategy contracts.

### _Balance_

```
function balance() external view returns (uint256);
```

xBalance is the amount of "want" stored in the vault, strategy and yield source.

### _Total Supply_

```
function totalSupply() external view returns (uint256);
```

Total Supply is the total amount of mooTokens minted. MooTokens are always 18 decimals. ()

### _Get Price Per Full Share_

```
function getPricePerFullShare() external view returns (uint256);
```

This function is calculated using balance() / totalSupply(). This represents the amount of underlying token that is owed for 1 mooToken.

### _Strategy_

```
function strategy() external view returns (address);
```

This function displays the current underlying strategy contract that the vault is using.

## Important Write Functions

### _Deposit_

```
function deposit(uint256 _amount) external;
```

Core deposit function of the strategy. Users deposit an \_amount of want and will receive minted mooTokens (shares) in return. There is additionally a helper function depositAll() that will find the total amount of want held in the user's wallet and deposit it all.

### _Withdraw_

```
function withdraw(uint256 _shares) external;
```

Unlike deposit, withdraw requests you send it your mooTokens(\_shares) in order to withdraw. Similar to deposit there is a withdrawAll() helper function that will use all mooTokens a user holds in there wallet for withdraw.

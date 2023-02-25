---
description: 'Last Update: February 2023'
---

# Vault Contract

The [Beefy Vault Contract](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/vaults/BeefyVaultV7.sol) is the central user-facing implementation of the Beefy protocol, which accepts and manages user deposits and mints mooTokens as a proof of receipt to facilitate withdrawals. It follows the ERC-20 [standard](https://eips.ethereum.org/EIPS/eip-20) for fungible, transferrable tokens.

Besides handling deposits and withdrawals, the primary function of the vault is to direct deposited funds to the relevant autocompounding [strategy-contract](strategy-contract/ "mention"). The vault and strategy contracts are kept separate to isolate any risks in the strategy from user deposits.

## View Functions

### want()

Returns the address of the underlying farm token (e.g. the LP token) used in both the Beefy Vault and Strategy contracts. Note that this is not the same as the underlying assets used for the farm.

```solidity
function want() public view returns (IERC20Upgradeable) {
    return IERC20Upgradeable(strategy.want());
}
```

### balance()

Returns the amount of "want" (i.e. underlying farm token) stored in the vault and strategy and yield source as an integer.

```solidity
function balance() public view returns (uint) {
    return want().balanceOf(address(this)) + IStrategyV7(strategy).balanceOf();
}
```

### available()

Returns the amount of "want" (i.e. underlying farm token) stored in the vault alone as an integer.

```solidity
function available() public view returns (uint256) {
    return want().balanceOf(address(this));
}
```

### totalSupply()

Returns the total amount of mooTokens minted as an integer, which are always displayed as 18 decimal token. This is a standard method inherited from the ERC-20 standard. See[#what-are-mootokens](../products/vaults.md#what-are-mootokens "mention") for more details.

```solidity
function totalSupply() public view virtual override returns (uint256) {
    return _totalSupply;
}
```

### getPricePerFullShare()

Returns the current price per share of the vault (i.e. per mooToken) as an integer denominated in the "want" (i.e. underlying farm token). This is calculated as _Price per Full Share =_ [#balance](beefy-vault-v6.md#balance "mention") _/_ [#totalsupply](beefy-vault-v6.md#totalsupply "mention").

```solidity
function getPricePerFullShare() public view returns (uint256) {
    return totalSupply() == 0 ? 1e18 : balance() * 1e18 / totalSupply();
}
```

### strategy()

Returns the address current underlying strategy contract that the vault is using to generate yield.

```solidity
function strategy() external view returns (address);
```

## Write Functions

### deposit()

Executes a transfer of a specified \_amount of "want" (i.e. underlying farm token) from the depositor to the vault, and then mints a proportional quantity of mooTokens to the depositor in return.

```solidity
function deposit(uint _amount) public nonReentrant {
    strategy.beforeDeposit();
    uint256 _pool = balance();
    want().safeTransferFrom(msg.sender, address(this), _amount);
    earn();
    uint256 _after = balance();
    _amount = _after - _pool; // Additional check for deflationary tokens
    uint256 shares = 0;
    if (totalSupply() == 0) {
        shares = _amount;
    } else {
        shares = (_amount * totalSupply()) / _pool;
    }
    _mint(msg.sender, shares);
}
```

Additionally, there is a helper function _depositAll()_ that deposits the entire balance of "want" in the user's wallet at the time of the transaction.

### withdraw()

Executes a burn of a specified \_amount of mooTokens from the depositor, and then transfers a proportional quantity of "want" (i.e. underlying farm token) to the depositor in return.

```solidity
function withdraw(uint256 _shares) public {
    uint256 r = (balance() * _shares) / totalSupply();
    _burn(msg.sender, _shares);
    uint b = want().balanceOf(address(this));
    if (b < r) {
        uint _withdraw = r - b;
        strategy.withdraw(_withdraw);
        uint _after = want().balanceOf(address(this));
        uint _diff = _after - b;
        if (_diff < _withdraw) {
            r = b + _diff;
        }
    }
    want().safeTransfer(msg.sender, r);
}
```

Similarly to [#deposit](beefy-vault-v6.md#deposit "mention")_,_ there is a helper function _withdrawAll()_ that withdraw the entire balance of mooTokens in the user's wallet at the time of the transaction.

### earn()

Executes a transfer of [#available](beefy-vault-v6.md#available "mention") "want" (i.e. underlying farm token) from the Vault Contract to the strategy contract and triggers the strategy's _deposit()_ function to deploy the funds and begin earning.

```solidity
function earn() public {
    uint _bal = available();
    want().safeTransfer(address(strategy), _bal);
    strategy.deposit();
}
```

### proposeStrat()

Writes the address of an alternate strategy to the Vault Contract's memory, in anticipation of upgrade the current strategy to the alternate using [#upgradestrat](beefy-vault-v6.md#upgradestrat "mention").

```solidity
function proposeStrat(address _implementation) public onlyOwner {
    require(address(this) == IStrategyV7(_implementation).vault(), "Proposal not valid for this Vault");
    require(want() == IStrategyV7(_implementation).want(), "Different want");
    stratCandidate = StratCandidate({
        implementation: _implementation,
        proposedTime: block.timestamp
    });
    emit NewStratCandidate(_implementation);
}
```

### upgradeStrat()

Replaces the address of the current strategy with an alternate strategy specified by [#proposestrat](beefy-vault-v6.md#proposestrat "mention").

```solidity
function upgradeStrat() public onlyOwner {
    require(stratCandidate.implementation != address(0), "There is no candidate");
    require(stratCandidate.proposedTime + approvalDelay < block.timestamp, "Delay has not passed");
    emit UpgradeStrat(stratCandidate.implementation);
    strategy.retireStrat();
    strategy = IStrategyV7(stratCandidate.implementation);
    stratCandidate.implementation = address(0);
    stratCandidate.proposedTime = 5000000000;
    earn();
}
```

## BeefyVaultV7.sol

The current release of our standard Beefy Vault Contract is [BeefyVaultV7.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/vaults/BeefyVaultV7.sol), which was [released](https://github.com/beefyfinance/beefy-contracts/pull/83) in August 2022. The V7 release improved on the previous version in a few keys ways:

* Introduced vault upgradeability through proxy patterns, to facilitate updates and changes to live Beefy vaults without needing to deprecate and re-deploy;
* Updated the strategy interface to allow for upgradeable strategies; and
* Amended all contracts to remove reliance on the SafeMath library, which has been generally retired following incorporation of its features into Solidity v0.8.

Separately, a ERC-4646-compliant wrapper contract was released for the V7 vault in November 2022, which allows developers to incorporate Beefy Vaults into their projects with standardised vault functionality and interfaces. See [beefywrapper-contract.md](other-beefy-contracts/beefywrapper-contract.md "mention") for more information.

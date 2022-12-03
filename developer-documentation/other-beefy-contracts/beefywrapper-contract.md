---
description: 'Last Update: November 2022'
---

# BeefyWrapper Contract

The [BeefyWrapper contract](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/vaults/BeefyWrapper.sol) is an ERC-4626 adapter interface that makes Beefy Vaults compatible with the ERC-4626 [standard](https://eips.ethereum.org/EIPS/eip-4626). It unlocks the composability of the standard and enables smoother interfacing and interaction with Beefy Vaults by external protocols, without the need for additional adapters and plug-ins.&#x20;

This page sets out some of the background to the ERC-4626 standard, and the functionality of the BeefyWrapper contract.

## Why ERC-4626?

The purpose of the ERC-4626 standard is to solve the problems caused by the diversity of vault designs found across DeFi. Many protocols have incorporated vault concepts into their architecture by reinventing the wheel to suit their own unique architecture and use cases. This means external projects hoping to implement a range of different vaults need to adapt and plug their code to reconcile it with the quirks of each protocol's unique vault design.&#x20;

The new standard recognises some common methods across the majority of vaults, and suggests that harmonising this functionality into a single standard can help to mitigate the quantity of adaptations and plug-ins required to work with most vaults. For protocols like Beefy, adopting ERC-4626 for our Beefy Vaults helps to facilitate new product development building on our products, and as a result promises to increase the range of use cases available to our users.

## Contract Methods

The functionality of the BeefyWrapper contract facilitates the minting and burning of wrapped Beefy Vault tokens in exchange for the transfer of the caller's Beefy Vault tokens. It also overrides the standard deposit and withdraw methods to facilitate deposits to the main Beefy Vault, in exchange for minting and burning of the wrapped Beefy Vault tokens.

### wrap()

Transfers the specified amount of the caller's Beefy Vault tokens to the wrapper contract to mint the same quantity of wrapped Beefy Vault tokens to the caller.

{% code overflow="wrap" %}
```solidity
// Wraps an amount of vault share tokens.
/// "amount" parameter is the total amount of vault share tokens to be wrapped.

function wrap(uint256 amount) public {

    // Transfers the specified amount of the caller's Beefy Vault tokens to the wrapper.
    IERC20Upgradeable(vault).safeTransferFrom(msg.sender, address(this), amount);
    
    // Mints the specified amount wrapped Beefy Vault tokens to the caller.
    _mint(msg.sender, amount);
}
```
{% endcode %}

### wrapAll()

Utilises the wrap() method, but using the full balance of the caller as the "amount" parameter.

{% code overflow="wrap" %}
```solidity
// Wraps all vault share tokens owned by the caller.

function wrapAll() external {
    wrap(IERC20Upgradeable(vault).balanceOf(msg.sender));
}
```
{% endcode %}

### unwrap()

Burns the specified amount of the caller's wrapped Beefy Vault tokens, to transfer the same quantity of unwrapped tokens from the wrapper contract back to the caller.

{% code overflow="wrap" %}
```solidity
// Unwraps an amount of vault share tokens.
/// "amount" parameter is the total amount of vault share tokens to be unwrapped.

function unwrap(uint256 amount) public {

    // Burns the specified amount of the caller's wrapped Beefy Vault tokens.
    _burn(msg.sender, amount);
    
    // Transfers the specified amount of Beefy Vault tokens back to the caller.
    IERC20Upgradeable(vault).safeTransfer(msg.sender, amount);
}
```
{% endcode %}

### unwrapAll()

Utilises the unwrap() method, but using the full balance of the caller as the "amount" parameter.

{% code overflow="wrap" %}
```solidity
// Unwraps all wrapped tokens owned by the caller.

function unwrapAll() external {
    unwrap(balanceOf(msg.sender));
}
```
{% endcode %}

### \_deposit()

Overrides the standard \_deposit() method to interact with the wrapper contract and issued wrapped Beefy Vault tokens, in place of the unwrapped version. Otherwise facilitates an ordinary transfer into the Beefy Vault.

{% code overflow="wrap" %}
```solidity
// Deposit assets to the vault and mint an equal number of wrapped tokens to vault shares.
/// "caller" parameter is the address of the sender of the assets.
/// "receiver" parameter is the address of the receiver of the wrapped tokens.
/// "assets" parameter is the amount of assets being deposited.
/// "shares parameter is the amount of shares being minted.

function _deposit(address caller, address receiver, uint256 assets, uint256 shares) internal virtual override {

    // Transfers the caller's tokens to the wrapper.
    IERC20Upgradeable(asset()).safeTransferFrom(caller, address(this), assets);
    uint balance = IERC20Upgradeable(vault).balanceOf(address(this));
    
    // Deposits the caller's tokens into the Beefy Vault.
    IVault(vault).deposit(assets);

    // Mints wrapped tokens to the receiver.
    shares = IERC20Upgradeable(vault).balanceOf(address(this)) - balance;
    _mint(receiver, shares);

    // Emits the Deposit event to signify a successful deposit.
    emit Deposit(caller, receiver, assets, shares);
}
```
{% endcode %}

### \_withdraw()

Overrides the standard \_withdraw() method to interact with the wrapped Beefy Vault tokens, in place of the unwrapped version. Otherwise facilitates an ordinary withdrawal from the Beefy Vault and returns the underlying tokens to the receiver.

<pre class="language-solidity" data-overflow="wrap"><code class="lang-solidity">// Burn wrapped tokens and withdraw assets from the vault.
/// "caller" parameter is the address of the caller of the withdraw.
/// "receiver" parameter is the address of the receiver of the assets.
/// "owner" parameter is the address of the owner of the burnt shares.
/// "assets" parameter is the amount of assets being withdrawn.
/// "shares parameter is the amount of shares being burnt.

function _withdraw(address caller, address receiver, address owner, uint256 assets, uint256 shares) internal virtual override {
    
    // Checks caller is not the contract's owner, and that the caller's spend                 allowance is sufficient for the call.
    if (caller != owner) {
        _spendAllowance(owner, caller, shares);
    }
    
    // Burns the caller's wrapped tokens.
    _burn(owner, shares);

    // Withdraws the caller's assets from the Beefy Vault.
    IVault(vault).withdraw(shares);
<strong>    uint balance = IERC20Upgradeable(asset()).balanceOf(address(this));
</strong>    if (assets > balance) {
        assets = balance;
    }

    // Transfers the caller's assets back to the receiver.
    IERC20Upgradeable(asset()).safeTransfer(receiver, assets);
    
    // Emits the Withdraw event to signify a successful withdrawal.
    emit Withdraw(caller, receiver, owner, assets, shares);
}
</code></pre>

### totalAssets()

Overrides the standard totalAssets() method to fetch the total assets held by the vault.

{% code overflow="wrap" %}
```solidity
// Fetches and returns the total assets as a uint256 value.

function totalAssets() public view virtual override returns (uint256) {

    return IVault(vault).balance();

}
```
{% endcode %}

### totalSupply()

Overrides the standard totalSupply() method to fetch the total shares issues by the vault.

{% code overflow="wrap" %}
```solidity
// Fetches and returns the total vault shares as a uint256 value.

function totalSupply() public view virtual override(ERC20Upgradeable, IERC20Upgradeable) returns (uint256) {

    return IERC20Upgradeable(vault).totalSupply();
    
}
```
{% endcode %}

## BeefyWrapperFactory Contract

The [BeefyWrapperFactory contract](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/vaults/BeefyWrapperFactory.sol) is a factory contract which provides a minimal proxy pattern for use in creating new Beefy Vault wrappers. A factory contract allows users to generate and deploy their own proxy contracts that all point to the same implementation contract, where the logic resides.&#x20;

Through the BeefyWrapperFactory, BeefyWrapper contracts can be deployed for any vaults. The factory contract has only one key function - clone().

### clone()

Uses the OpenZeppelin standard proxy template [ClonesUpgradeable.sol](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/blob/master/contracts/proxy/ClonesUpgradeable.sol) to create a proxy contract which is a clone of the BeefyWrapper contract.

{% code overflow="wrap" %}
```solidity
// Creates a new Beefy Vault wrapper as a proxy of the template instance.
/// "_vault" parameter is the cloned Beefy Vault.
/// "proxy" return is the new proxied Beefy Vault wrapper.

function clone(address _vault) external returns (address proxy) {
    
    // Proxy is set as a clone of the instance of the BeefyWrapper contract.
    proxy = implementation.clone();
    
    // Initializes the wrapper proxy set above.
    IWrapper(proxy).initialize(
        _vault,
        string.concat("W", IVault(_vault).name()),
        string.concat("w", IVault(_vault).symbol())
    );
    
    // Emits the ProxyCreated event to signify a successful deployment.
    emit ProxyCreated(proxy);
}
```
{% endcode %}

## Contracts

The template Beefy Vault wrapper contracts are publicly maintained in Beefy's GitHub repositories. See [BeefyWrapper.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/vaults/BeefyWrapper.sol) and [BeefyWrapperFactory.sol](https://github.com/beefyfinance/beefy-contracts/blob/master/contracts/BIFI/vaults/BeefyWrapperFactory.sol).

Wrapper contracts for each Beefy Vault will be deployed separately on the relevant chains, and will not necessarily be deployed to similar contract addresses. To test sample contracts deployed on the Polygon blockchain, see this instance of [BeefyWrapper.sol](https://polygonscan.com/address/0x776994eab59b894fb892d08a46329c5077c9e226) and this instance of [BeefyWrapperFactory.sol](https://polygonscan.com/address/0xd1cedfb11994ebbc1608ae46d7c7176294bdd599).
---
description: 'Last Update: November 2022'
---

# DelegateRegistry Contract

{% hint style="warning" %}
Please note that vote delegation for Beefy's Snapshot is currently unavailable. This is due to Beefy's custom solution built on top of the standard Snapshot tooling, which enables the full functionality of your $BIFI tokens on the various chains we're deployed on. Keep an eye on [Beefy's Discord](https://discord.gg/yq8wfHd) for details of when delegation is available again.
{% endhint %}

The [DelegateRegistry contract](https://github.com/gnosis/delegate-registry/blob/main/contracts/DelegateRegistry.sol) is a governance smart contract developed by Gnosis and used by Snapshot Labs to facilitate vote delegation in Snapshot-based governance spaces. Users can authorise another user to vote on their behalf using their voting power. Any user can delegate their voting power to any address on the relevant blockchain, though the delegated voting power will only be used where the delegate adddress votes as well. Users can also remove their delegations at any time.

Through this mechanism, trusted voices in the community can leverage their support with a small amount of effort on the part of their supporters. It also allows those short on time to ensure that their voting power is participating in governance, without requiring them to engage with every proposal that arises.

{% hint style="info" %}
Please note that vote delegation exists separately on each blockchain. Where you hold $BIFI across a number of different chains, the DelegateRegistry contract does not have any functionality to delegate across all chains. Instead, you must interact separately with the contract deployed on each different chain to delegate all of your $BIFI voting power.
{% endhint %}

## Contract Mapping

The DelegateRegistry contract is first and foremost a repository of information on existing delegations, which are stored in the "delegation" mapping in the contract:

{% code overflow="wrap" %}
```solidity
// SPDX-License-Identifier: LGPL-3.0-only    
// The first key is the delegator and the second key a id. 
// The value is the address of the delegate 

mapping (address => mapping (bytes32 => address)) public delegation;
```
{% endcode %}

Effectively, each delegation is stored by reference to the delegator's address (i.e. the user that is delegated their voting power), which is then mapped to the relevant Snapshot space ID (stored as a bytes32 value) and the delegate's address (i.e. the user that voting power is delegated to).

For full details of all delegations managed by Snapshot Labs' DelegateRegistry contract, you can explore the Snapshot Subgraph [here](https://thegraph.com/hosted-service/subgraph/snapshot-labs/snapshot).&#x20;

## Contract Events

The DelegateRegistry contract emits two possible events in its ordinary operations.

### SetDelegate

Signifies that the contract's [#setdelegate-1](delegateregistry-contract.md#setdelegate-1 "mention") method has successfully been called, and consequently the caller has selected a new delegate.

{% code overflow="wrap" %}
```solidity
// SPDX-License-Identifier: LGPL-3.0-only        
// Using these events it is possible to process the events to build up reverse lookups.
// The indeces allow it to be very partial about how to build this lookup (e.g. only for a specific delegate).

event SetDelegate(address indexed delegator, bytes32 indexed id, address indexed delegate);
```
{% endcode %}

### ClearDelegate

Signifies that one of the below [#contract-methods](delegateregistry-contract.md#contract-methods "mention") has successfully been called, and consequently the former delegate has been cleared for the caller.

{% code overflow="wrap" %}
```solidity
// SPDX-License-Identifier: LGPL-3.0-only        
// Using these events it is possible to process the events to build up reverse lookups.
// The indeces allow it to be very partial about how to build this lookup (e.g. only for a specific delegate).

event ClearDelegate(address indexed delegator, bytes32 indexed id, address indexed delegate);
```
{% endcode %}

## Contract Methods

The functionality behind the DelegateRegistry contract is very straightforward, and consists of just two methods to set and remove delegates.

### setDelegate()

To set a delegate, the contract requires two inputs: the relevant Snapshot space ID (stored as a bytes32 value); and the delegate's address (i.e. the user that voting power is delegated to). It then tests the inputs against a few requirements (e.g. the user is not delegating to itself, to a null address or to its current delegate) before executing the call.

{% code overflow="wrap" %}
```solidity
// SPDX-License-Identifier: LGPL-3.0-only
/// @dev Sets a delegate for the msg.sender and a specific id.
///      The combination of msg.sender and the id can be seen as a unique key.
/// @param id Id for which the delegate should be set
/// @param delegate Address of the delegate

function setDelegate(bytes32 id, address delegate) public {
        require (delegate != msg.sender, "Can't delegate to self");
        require (delegate != address(0), "Can't delegate to 0x0");
        address currentDelegate = delegation[msg.sender][id];
        require (delegate != currentDelegate, "Already delegated to this address");
        
        // Update delegation mapping
        delegation[msg.sender][id] = delegate;
        
        if (currentDelegate != address(0)) {
            emit ClearDelegate(msg.sender, id, currentDelegate);
        }

        emit SetDelegate(msg.sender, id, delegate);
}
```
{% endcode %}

Where the call is successful, the method will update the delegation mapping to the new delegate address. It then tests whether the user had previously delegated to another user, and if so it will then emit the [#cleardelegate](delegateregistry-contract.md#cleardelegate "mention") event to signify that the old delegate has been removed. Finally it will emit the [#setdelegate](delegateregistry-contract.md#setdelegate "mention")event to signify that the new delegate has been added.

Please note that the method does not also require the contract to use the [#cleardelegate-1](delegateregistry-contract.md#cleardelegate-1 "mention") method, which is only used to remove an existing delegate.

### clearDelegate()

To clear the current delegate, the contract requires one input, which is the relevant Snapshot space ID (stored as a bytes32 value). It then tests to ensure that a delegate has in fact been set before executing the call.

<pre class="language-solidity" data-overflow="wrap"><code class="lang-solidity">// SPDX-License-Identifier: LGPL-3.0-only
/// @dev Clears a delegate for the msg.sender and a specific id.
///      The combination of msg.sender and the id can be seen as a unique key.
/// @param id Id for which the delegate should be set

function clearDelegate(bytes32 id) public {
        address currentDelegate = delegation[msg.sender][id];
        require (currentDelegate != address(0), "No delegate set");
        
<strong>        // update delegation mapping
</strong>        delegation[msg.sender][id] = address(0);
        
        emit ClearDelegate(msg.sender, id, currentDelegate);
}
</code></pre>

Where the call is successful, the method will update the delegation mapping to the null address (i.e. singifying that the user has not delegated their voting power), and then emits the [#cleardelegate](delegateregistry-contract.md#cleardelegate "mention") event to signify that the old delegate has been removed.

## Delegation Walkthrough

There are two main methods that users can adopt to interact with the DelegateRegistry contract: either interacting through the Snapshot interface or by interacting directly with the contract (e.g. through a relevant block explorer). Below are brief walkthroughs for each method.

### Through the Snapshot Interface

1. Go to [the Snapshot interface delegation page](https://snapshot.org/#/delegate).
2. Connect your wallet the site, so that it can detect your address and so you can call the [#setdelegate-1](delegateregistry-contract.md#setdelegate-1 "mention") method.
3. Input the address or ENS name of the user you want to delegate your voting power to.
4. If you want to, you can select "limit delegation to a specific space" to confine your delegation to only the Beefy Snapshot space. To do so, input the following space: beefydao.eth.
5.  Click "Confirm" to initiate the transaction in your wallet. As this is a write transaction (i.e. submitting information for storage on the blockchain), you will have to pay a small amount of gas to facilitate the transaction.

    <figure><img src="../../.gitbook/assets/Snapshot Interface.png" alt=""><figcaption><p>The Snapshot interface's delegation page provides a clean and simple way to delegate your voting power.</p></figcaption></figure>
6. Once the transaction goes through, you will have successfully delegated to the user address that you provided on the chain on which the transaction was submitted. Now repeat steps 1-5 on any other chains that you wish to delegate voting power on.

### Through a Block Explorer

1. Go to your prefererred blockchain explorer for the blockchain you wish to use, and navigate to the DelegateRegistry contract address (0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446). Below we use Etherscan.io as an [example](https://etherscan.io/address/0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446).
2. Navigate to the "Write Contract" subtab on the "Contract" tab on the contract page (as below).
3.  Select the "Connect to Web3" button to connect your wallet and interact with the contract.

    <figure><img src="../../.gitbook/assets/Etherscan Interface.png" alt=""><figcaption><p>A blockchain explorer interface will provide you with full access to all delegation methods, events and transactions, though they are clearly less user friendly for most users.</p></figcaption></figure>
4. Scroll down to the [#setdelegate-1](delegateregistry-contract.md#setdelegate-1 "mention") method, and input the required details, those being:
   1. id (bytes32) - the address of the Snapshot space for which you are delegating (i.e. the Beefy Space ID: 0x626565667964616f2e657468).
   2. delegate (address) - the address of the user you want to delegate your voting power to.
5.  Click "Write" to initiate the transaction in your wallet. As this is a write transaction (i.e. submitting information for storage on the blockchain), you will have to pay a small amount of gas to facilitate the transaction.

    <figure><img src="../../.gitbook/assets/Etherscan Methods.png" alt=""><figcaption><p>The methods on each block explorer reflect those detailed in the <a data-mention href="delegateregistry-contract.md#contract-methods">#contract-methods</a> section above.</p></figcaption></figure>
6. Once the transaction goes through, you will have successfully delegated to the user address that you provided on the chain on which the transaction was submitted. Now repeat steps 1-5 on any other chains that you wish to delegate voting power on.

## Contracts

The DelegateRegistry contract and Beefy snapshot space are deployed on each different chain on which they operates at the exact same contract addresses, those being:

* DelegateRegistry - 0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446.
* Beefy Space ID - 0x626565667964616f2e657468 or beefydao.eth.

See for example the DelegateRegistry contract deployment on Ethereum [here](https://etherscan.io/address/0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446).

## More Information

For more details of how vote delegation works for Beefy's governance, see the [governance.md](../../community-governance/governance.md "mention") page (specifically [#how-do-i-delegate-my-vote](../../community-governance/governance.md#how-do-i-delegate-my-vote "mention") and [#how-do-i-become-a-delegate](../../community-governance/governance.md#how-do-i-become-a-delegate "mention")). You can also find the current maintained list of vote delegates in this [Google sheet](https://docs.google.com/spreadsheets/d/1sJH4jg3eEEJDpbws55qUmzPeLDiDuL\_5OAQobSn7m2Y/edit?usp=sharing).

For full details of all delegations managed by Snapshot Labs' DelegateRegistry contract, you can explore the Snapshot Subgraph [here](https://thegraph.com/hosted-service/subgraph/snapshot-labs/snapshot). Further information in available in Snapshot's [documentation](https://docs.snapshot.org/guides/delegation).

---
description: 'Last Update: February 2023'
---

# DelegateRegistry Contract

The [DelegateRegistry contract](https://github.com/gnosis/delegate-registry/blob/main/contracts/DelegateRegistry.sol) is a governance smart contract developed by Gnosis and used by Snapshot Labs to facilitate vote delegation in Snapshot-based governance spaces. Users can authorise another user to vote on their behalf using their voting power, by delegating to them on Ethereum. Users can also remove their delegations at any time.

Through this mechanism, trusted voices in the community can leverage their support with a small amount of effort on the part of their supporters. It also allows those short on time to ensure that their voting power is participating in governance, without requiring them to engage with every proposal that arises.

## Contract Mapping

The DelegateRegistry contract is first and foremost a repository of information on existing delegations, which are stored in the "delegation" mapping in the contract:

{% code overflow="wrap" %}
```solidity
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

Signifies that the contract's [#setdelegate-1](delegateregistry-contract.md#setdelegate-1 "mention") function has successfully been called, and consequently the caller has selected a new delegate.

{% code overflow="wrap" %}
```solidity
// Using these events it is possible to process the events to build up reverse lookups.
// The indeces allow it to be very partial about how to build this lookup (e.g. only for a specific delegate).

event SetDelegate(address indexed delegator, bytes32 indexed id, address indexed delegate);
```
{% endcode %}

### ClearDelegate

Signifies that one of the below [#contract-functions](delegateregistry-contract.md#contract-functions "mention") has successfully been called, and consequently the former delegate has been cleared for the caller.

{% code overflow="wrap" %}
```solidity
// Using these events it is possible to process the events to build up reverse lookups.
// The indeces allow it to be very partial about how to build this lookup (e.g. only for a specific delegate).

event ClearDelegate(address indexed delegator, bytes32 indexed id, address indexed delegate);
```
{% endcode %}

## Contract Functions

The functionality behind the DelegateRegistry contract is very straightforward, and consists of just two functions to set and remove delegates.

### setDelegate()

To set a delegate, the contract requires two inputs: the relevant Snapshot space ID (stored as a bytes32 value); and the delegate's address (i.e. the user that voting power is delegated to). It then tests the inputs against a few requirements (e.g. the user is not delegating to itself, to a null address or to its current delegate) before executing the call.

{% code overflow="wrap" %}
```solidity
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

Where the call is successful, the function will update the delegation mapping to the new delegate address. It then tests whether the user had previously delegated to another user, and if so it will then emit the [#cleardelegate](delegateregistry-contract.md#cleardelegate "mention") event to signify that the old delegate has been removed. Finally it will emit the [#setdelegate](delegateregistry-contract.md#setdelegate "mention")event to signify that the new delegate has been added.

Please note that the function does not also require the contract to use the [#cleardelegate-1](delegateregistry-contract.md#cleardelegate-1 "mention") function, which is only used to remove an existing delegate.

### clearDelegate()

To clear the current delegate, the contract requires one input, which is the relevant Snapshot space ID (stored as a bytes32 value). It then tests to ensure that a delegate has in fact been set before executing the call.

<pre class="language-solidity" data-overflow="wrap"><code class="lang-solidity">/// @dev Clears a delegate for the msg.sender and a specific id.
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

Where the call is successful, the function will update the delegation mapping to the null address (i.e. singifying that the user has not delegated their voting power), and then emits the [#cleardelegate](delegateregistry-contract.md#cleardelegate "mention") event to signify that the old delegate has been removed.

## Delegation Walkthrough

There are two main methods that users can adopt to interact with the DelegateRegistry contract: either interacting through the Snapshot interface or by interacting directly with the contract (e.g. through a relevant block explorer). Below are brief walkthroughs for each methods.

### Through the Snapshot Interface

1. Go to the [Snapshot interface delegation page](https://vote.beefy.finance/#/delegate/beefydao.eth).
2. Connect your wallet the site, so that it can detect your address and so you can call the [#setdelegate-1](delegateregistry-contract.md#setdelegate-1 "mention") function.&#x20;
3. Make sure you're connected to Ethereum with your wallet. **No other chain will work.**
4. Input the address or ENS name of the user you want to delegate your voting power to.
5. If you want to, you can select "limit delegation to a specific space" to confine your delegation to only the Beefy Snapshot space. To do so, input the following space: beefydao.eth.
6.  Click "Confirm" to initiate the transaction in your wallet. As this is a write transaction (i.e. submitting information for storage on the blockchain), you will have to pay a small amount of gas to facilitate the transaction.

    <figure><img src="../../.gitbook/assets/Snapshot Interface.png" alt=""><figcaption><p>The Snapshot interface's delegation page provides a clean and simple way to delegate your voting power.</p></figcaption></figure>
7. Once the transaction goes through, you will have successfully delegated to the user address that you provided across all chains that our BIFI token is deployed to.

### Through a Block Explorer

1. Go to the DelegateRegistry contract address on [Etherscan](https://etherscan.io/address/0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446).&#x20;
2. Navigate to the "Write Contract" subtab on the "Contract" tab on the contract page (as below).
3. Select the "Connect to Web3" button to connect your wallet and interact with the contract.&#x20;
4. Make sure your wallet is set to Ethereum. **No other chain will work.**

<figure><img src="../../.gitbook/assets/Screenshot 2023-11-07 at 14.46.27.png" alt=""><figcaption><p>The Etherscan interface will provide you with full access to all delegation methods, events and transactions, though they are clearly less user friendly for most users.</p></figcaption></figure>

1. Scroll down to the [#setdelegate-1](delegateregistry-contract.md#setdelegate-1 "mention") function, and input the required details, those being:
   1. id (bytes32) - the address of the Snapshot space for which you are delegating (i.e. the Beefy Space ID: 0x626565667964616f2e657468).
   2. delegate (address) - the address of the user you want to delegate your voting power to.
2.  Click "Write" to initiate the transaction in your wallet. As this is a write transaction (i.e. submitting information for storage on the blockchain), you will have to pay a small amount of gas to facilitate the transaction.

    <figure><img src="../../.gitbook/assets/BscScan Methods.png" alt=""><figcaption><p>The functions on each block explorer reflect those detailed in the <a data-mention href="delegateregistry-contract.md#contract-functions">#contract-functions</a> section above.</p></figcaption></figure>
3. Once the transaction goes through, you will have successfully delegated to the user address that you provided across all chains that our BIFI token is deployed to.

## Contracts

The DelegateRegistry contract and Beefy snapshot space are deployed at the following addresses:

* DelegateRegistry - [0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446](https://etherscan.io/address/0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446).
* Beefy Space ID - 0x626565667964616f2e657468 or beefydao.eth.

## More Information

For more details of how vote delegation works for Beefy's governance, see the [governance.md](../../dao/governance.md "mention") page (specifically [#how-do-i-delegate-my-vote](../../dao/governance.md#how-do-i-delegate-my-vote "mention") and [#how-do-i-become-a-delegate](../../dao/governance.md#how-do-i-become-a-delegate "mention")). You can also find the current maintained list of vote delegates in this [Google sheet](https://docs.google.com/spreadsheets/d/1sJH4jg3eEEJDpbws55qUmzPeLDiDuL\_5OAQobSn7m2Y/edit?usp=sharing).

For full details of all delegations managed by Snapshot Labs' DelegateRegistry contract, you can explore the Snapshot Subgraph [here](https://thegraph.com/hosted-service/subgraph/snapshot-labs/snapshot). Further information in available in Snapshot's [documentation](https://docs.snapshot.org/guides/delegation).

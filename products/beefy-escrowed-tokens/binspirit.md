---
description: Beefy-wrapped inSPIRIT
---

# binSPIRIT

## What is SPIRIT?

SPIRIT is the native token of SpiritSwap, a decentralized exchange native to the Fantom blockchain. It rewards holders with a share of the platform's revenues and also acts as a governance token. SPIRIT has a fixed supply and decaying emissions model.

Users can stake and lock their SPIRIT tokens on SpiritSwap for a fixed period between 1 week and 4 years, to receive a proportional amount of inSPIRIT. inSPIRIT holders receive a range of benefits, including: (1) a proportion of the protocol's revenues (which vary week by week, but have been as high as 80% APR); (2) voting rights in the protocol's governance and vault incentives gauge; (3) up to 2.5x boosted rewards from SpiritSwap farms, depending on the balance of inSPIRIT held by the user; and (4) access to bribes for voting for third party-incentivised gauges.

inSPIRIT is non-transferrable and the amount held by a given user decreases steadily to 0 when the lock is over. Users also cannot liquidate or transfer their locked SPIRIT positions until the end of the time lock.

## What is binSPIRIT?

binSPIRIT is the Beefy-escrowed version of inSPIRIT which is staked to accumulate inSPIRIT. Holders of binSPIRIT receive each of the benefits of inSPIRIT detailed above, but without being constrained by the SpiritSwap lock mechanism.

The token is fully backed 1:1 by SPIRIT, though is perpetually locked for inSPIRIT, so cannot be withdrawn back to SPIRIT. However, binSPIRIT is a transferrable ERC-20 token, so can be swapped for other tokens on decentralised exchanges, allowing holders to exit their positions at any time.

## How does one get binSPIRIT?

Users can mint binSPIRIT on the [binSPIRIT vault page](https://app.beefy.finance/#/vault/beefy-binspirit) at a 1:1 ratio. If it is more profitable to buy binSPIRIT, then Beefy's Smart Minter will do exactly that, yielding the user more binSPIRIT for their SPIRIT. Users can also get binSPIRIT by buying on a decentralised exchange.

![beMINT determines the most profitable strategy](../../../.gitbook/assets/binspirit\_mint.jpg)

## How does binSPIRIT work?

Beefy uses the deposited SPIRIT to accumulate as much inSPIRIT as it can by immediately and perpetually locking all deposits on SpiritSwap for the longest available period. It then puts the accumulated inSPIRIT to use to claim SpiritSwap protocol revenues, boost its SpiritSwap vaults and vote for SpiritSwap incentive emissions. &#x20;

All protocol revenues are paid out in SPIRIT, which is automatically claimed by Beefy and then returned to the binSPIRIT vault, either by minting more binSPIRIT (if binSPIRIT is over peg) or by purchasing binSPIRIT on a decentralised exchange (if under peg) and then in either case redepositing the binSPIRIT into the vault.

All deposits, withdrawals and harvest rewards from Beefy's boosted SpiritSwap vaults are routed through the binSPIRIT contract, so that they may receive the benefit of its inSPIRIT boost. By keeping all of the accumulated inSPIRIT in one contract, and running all the vaults through that contract, binSPIRIT ensures that each vault receives the maximum available boost. All boosted rewards are retained by the individual Beefy vaults.

The binSPIRIT contract also submits votes on Beefy's behalf for SpiritSwap governance proposals and vault incentive gauges. binSPIRIT holders are empowered to [vote](binspirit.md#can-i-vote-with-binspirit) on gauges, as described furhter below.

For further details of binSPIRIT's specific functionality and methods, see the description of its main [GaugeStaker smart contract](../../../developer-documentation/other-contracts/gaugestaker-contract.md).

## How can I earn with my binSPIRIT?

Once you're holding binSPIRIT, there are a few available options. You can either: &#x20;

1. Stake it in the Beefy binSPIRIT vault to earn protocol revenue, which is autocompounded into more binSPIRIT;
2. Deposit it into a binSPIRIT liquidity pool with a decentralised exchange (e.g. SpiritSwap, Solidly) to earn trading fees (and potentially rewards); or
3. Deposit it into the SPIRIT-binSPIRIT LP on SpiritSwap, and stake in the [Beefy SPIRIT-binSPIRIT LP vault](https://app.beefy.finance/#/vault/spirit-binspirit-spirit) to earn autocompounded trading fees and rewards.&#x20;

## But what about fees?

Beefy strives to maintain some of the lowest yield-optimizing fees, and charges standard fees on its binSPIRIT vaults. No Beefy fees are charged for using Beefy's Smart Minter to convert SPIRIT into binSPIRIT.

## How does binSPIRIT keep its peg?

Should a user want to liquidate their position they will be able to trade binSPIRIT on an exchange. By contrast to inSPIRIT, users are never locked in and can exit their position at any time. This also means that binSPIRIT may not always be pegged to SPIRIT, but aims to maintain a loose peg.&#x20;

If binSPIRIT goes under peg, then the contract will use the claimed SpiritSwap protocol revenues to buy back more binSPIRIT. This increases the size of each binSPIRIT holder's proportional share of deposited SPIRIT, leaving them with more than they would have achieved from locking the same SPIRIT directly on SpiritSwap.

If binSPIRIT goes over peg, then the contract will use protocol revenues to mint more binSPIRIT at at a profit.

## Can I vote with binSPIRIT? <a href="#can-i-vote-with-binspirit" id="can-i-vote-with-binspirit"></a>

No. Though Beefy had previously set up a binSPIRIT voting system and a [dedicated Snapshot page](https://snapshot.org/#/binspirit.eth), the move to SpiritSwap V2 has allowed Beefy to automate the process of bribing to help us obtain the highest return for holders. Beefy then returns all bribe earnings directly to the binSPIRIT vaults, facilitating high returns with minimal effort.

Though Beefy has automated the process, we are still open to receiving direct offers for binSPIRIT bribes. Please reach out to the Core team on Discord, Telegram or Twitter to find out more.

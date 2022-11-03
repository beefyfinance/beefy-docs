---
description: Beefy-escrowed JOE
---

# beJOE

## What is JOE? <a href="#what-is-joe" id="what-is-joe"></a>

JOE is the native token of Trader Joe, a decentralized exchange native to the Avalanche blockchain. It rewards holders with a share of the platform’s revenues and also acts as a governance token. JOE has a fixed supply and decaying emissions model.

Users can stake JOE to earn veJOE and receive boosted JOE rewards in selected Trader Joe Farms and governance voting power.

## What is beJOE?

beJOE is a Beefy-escrowed version of JOE staked to earn veJOE, maximizing emissions on boosted Beefy vaults. beJOE stakers earn 5% of emissions from those boosted vaults.&#x20;

The token is fully backed 1:1 by JOE and can be redeemed for JOE held in reserve. This reserve only fills up when a new user deposits.

## How does one get beJOE?

You can mint beJOE on the beJOE [vault](https://app.beefy.finance/#/vault/beefy-beJoe) or [earnings pool](https://app.beefy.finance/#/vault/beefy-beJoe-earnings) pages at a 1:1 ratio. There is no incentivised liquidity for beJOE, instead there will be a withdrawal reserve.

![beJOE is minted and burned at a 1:1 rate with JOE](<../../../.gitbook/assets/image (3) (1).png>)

## How does beJOE work?

When you mint beJOE, the contract will immediately try to stake the deposited JOE into veJOE, subject to two conditions: (1) the required reserve must be maintained; and (2) the staking must trigger a “Speed Up" bonus.

If the contract's JOE reserves at the time of minting exceed the required reserve amount (which is currently 20% of the contract's JOE already staked into veJOE), the contract can stake any excess JOE into veJOE. If the JOE reserves are under the required reserve amount, then the deposited JOE will be added to the reserve to cover the current shortfall.

The “Speed Up" bonus on Trader Joe doubles the rate of veJOE accruals for 14 days after JOE is staked, provided that the amount of JOE staked adds an additional 5% (or more) on top of the total amount of JOE already staked into veJOE . The contract therefore checks before staking whether the available balance (including both the deposit and any pre-existing excess over the required reserve) would meet or exceed the 5% threshold, and will only stake the available balance if it does. Otherwise, it waits for further JOE deposits to increase the available balance before staking.

Once the contract's JOE is staked into veJOE, it will automatically accrue veJOE rewards. veJOE provides 2 benefits: (1) boosted rewards on certain Trader Joe farms; and (2) (future) voting rights in Trader Joe governance. The amount of each benefit is proportional to the balance of veJOE held by the contract, so the aim is to accrue as much veJOE as possible.

Though veJOE rewards accrue constantly on the contract's staked JOE, the rewards must be harvested to be added to the contract's balance of veJOE. Rewards are automatically harvested whenever JOE is staked into veJOE, and otherwise manually harvested by the contract when new beJOE is minted but the conditions for staking are not met.

## How can I earn with my beJOE? <a href="#what-can-i-do-with-bejoe" id="what-can-i-do-with-bejoe"></a>

Once you’re holding beJOE, there are a couple of available options. You can either:

1. Stake it in the beJOE vault to earn more beJOE; or
2. Stake it in the beJOE earnings pool to earn JOE.

In every Beefy vault for a Trader Joe farm which is boosted for veJOE holders, 5% of the value of every harvest will be diverted to the beJOE reward pool to be paid out to beJOE holders. This reflects the value added by the beJOE contract, which gathers the veJOE needed to boost these vaults.

As the boosted rewards on Trader Joe farms are paid out in JOE, these can be paid back to beJOE holders either directly in JOE (through the earnings pool), or by compounding beJOE (through the vault) by minting more beJOE with the JOE rewards.

## How does the beJOE strategy work?

![](../../../.gitbook/assets/Flow\_beJOE.png)

## But what about fees? <a href="#but-what-about-fees" id="but-what-about-fees"></a>

Beefy strives to maintain some of the lowest yield-optimizing fees, and charges standard fees on its beJOE vaults, plus an additional 5% delivered directly to beJOE stakers.

## How does beJOE keep its peg?

There's no liquidity provided for beJOE, so it will always be at 1:1 with JOE. Users can burn beJOE for JOE while the reserve lasts. This reserve only fills up when a new user deposits.

In a last-resort scenario, all locked JOE in beJOE can be unlocked and released to the reserve. Beefy's competitors do not have this. However this would also end the boosts available for Beefy vaults and the rewards streamed to the beJOE reward pool, so is unlikely to be triggered.

## Can I vote with beJOE? <a href="#vejoe-model" id="vejoe-model"></a>

Not yet, but beJOE implements EIP-1271 (signature validation for contracts), so future governance/bribes with TraderJoe can be organised.

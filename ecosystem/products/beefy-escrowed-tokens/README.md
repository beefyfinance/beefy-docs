---
description: 'Last Update: October 2022'
---

# Beefy-escrowed Tokens

## What is Escrow?

An escrow mechanism is where one party holds another's rights or assets in custody for them, pending fulfilment of a specific condition (e.g. safe receipt of goods purchased with those assets). In DeFi, escrow mechanisms involve you providing your tokens to a third party (e.g. Beefy) to allow them to implement some functionality with those tokens on your behalf. As such, all escrow mechanisms are typically built around some token economic (**"tokenomic"**) design in the tokens you hold.

For example, a blockchain's native token (e.g. Fantom's FTM) may be used for staking purposes to secure a blockchain by fairly and safely validating its transactions. The tokenomic design allows users to stake their tokens in order to earn transaction fees from users of the blockchain, giving the native token an ability to earn or generate value for the holder. However, staking is complicated and has trade offs, like locking your tokens and limiting your ability to trade in them. So third party escrow solutions (e.g. Beefy's beFTM) have been created to allow you to access the benefits of tokenomics (i.e. staking your FTM) without having to manage the staking yourself, and whilst allowing you to still trade your interest in the locked tokens.

## What is Vote Escrow?

A vote escrow mechanism is a form of tokenomic escrow design which aims to reward long term holders of a protocol's governance tokens with more voting power, to favour their interests in governance matters over short term holders. This is achieved by holders staking and typically locking their governance tokens with the protocol (typically for a return from protocol earnings), thereby limiting their ability to deal in those tokens. In doing so, the holder either unlocks voting rights (which are otherwise not available to holders) or boosts their existing voting power, typically in line with the amount of time that their tokens are staked/locked for. This voting power is often used to direct the economics of the relevant protocol, like by having users vote on how to distribute newly issued tokens as additional incentives among the protocol's liquidity pools.

The vote escrow system was pioneered in DeFi by Curve Finance's CRV and veCRV token design (hosted on Ethereum). Other notable examples of escrow designs include Convex's veCVX (Ethereum), Balancer's veBAL (Ethereum), Frax's veFXS (Ethereum), Mai Finance's eQI (Polygon), Trader Joe's veJOE (Avalanche), Platypus's vePTP (Avalanche), Velodrome's veVELO (Optimism).

## What are Vote-escrowed Tokens?

In most vote escrow systems, the voting power of users is not linearly related to the number of governance tokens held, but instead depends on factors like the length of time which the tokens are locked for. In light of this, the concept of vote-escrowed tokens (**"veTokens"**) was developed, to reflect the amount of voting power that a user has arising from their staked/locked tokens. As the factors that impact on voting power change over time, the user's amount of veTokens will also change, even as the number of governance tokens held stays the same.

One point of confusion is that - despite the name - veTokens aren't always represented by an ERC20 token, so aren't necessarily received and held by users in their wallet. This is because veToken economics ("**veTokenomics**") are designed to allow for voting power to change constantly as the input factors (e.g. length of the lock period) change. If veTokens were to be issued to users, they would require constant rebasing (adjusting the total supply and nominal holdings of all users) to maintain a fair record,  which would add a lot of additional complexity and cost. Furthermore, as veTokenomics were designed to incentivise long-term holding of governance tokens, implementing voting power in a transferable ERC20 format may undermine that goal, as it would allow long term holders to trade their interests in the same way that short term holders do.

<details>

<summary>Example of veTokenomics</summary>

Imagine a voter holds 1 EXMPL token, issued by Example DAO and which entitles them to 1 whole vote in Example DAO's existing governance process.

Example DAO then implements a vote escrow design, where the voter can stake and lock their tokens for any length of time up to 2 years, and will receive a voting power boost equal to the number of time in years remaining in their lock.

In ordinary circumstances, the voter's 1 EXMPL token would entitled them to governance voting power equal to a static 1 veEXMPL, or 1 whole vote in the governance process.

The voter could then opt to lock their 1 EXMPL token for 2 years, and would receive 3 veEXMPL (1 base + 2 bonus), which amounts to 3 whole votes instead.

After a year of boosted voting, the holder's lock period would have decreased to 1 year, consequently reducing their bonus and veEXMPL so that they are entitled to 2 votes. The user can decide at any time to extend their lock back to 2 years to increase their veEXMPL, or they may decide that they want to exit the lock by waiting another year, and then sell their tokens.

</details>

## What are Beefy-escrowed Tokens?

Beefy-escrowed token ("**beTokens**") are wrapper tokens, designed and implemented by Beefy to unlock the benefits of escrow tokenomics whilst enabling our users to trade their interests in the partners' governance tokens. Effectively, we put in place an interim smart contract which can hold the governance tokens, lock them with the partner protocol for the maximum possible lock and gain access to the benefits of the escrow model. In addition, we add extra value by combining these features with issuing a new ERC20 beToken to you which you can then exchange to exit the lock at any time.

Each beToken is uniquely designed around the different veTokenomic model of our partner protocols, so they come with a range of different possible features. These can include: withdrawal reserves; supported DEX liquidity; pegged or free-floating pricing; a Beefy voting process for allocating votes on the underlying protocol; user-led or Beefy-led bribes; and boosts to associated Beefy vaults.&#x20;

Beefy always support our beTokens with vaults on the Beefy platform, where you can stake your beTokens to earn a return. This may be in the form of an autocompounding beToken Vault (i.e. earn more beTokens) or an Earnings Pool (i.e. earning more of the underlying governance token). In either case, you're free to withdraw from your staking at any time, to trade in your beToken and exit your position.

## What Beefy-escrowed Tokens are there?

In this section, we provide a page covering each of the different beTokens that we currently operate. At the time of writing, these include:

{% content-ref url="beftm.md" %}
[beftm.md](beftm.md)
{% endcontent-ref %}

{% content-ref url="binspirit.md" %}
[binspirit.md](binspirit.md)
{% endcontent-ref %}

{% content-ref url="bejoe.md" %}
[bejoe.md](bejoe.md)
{% endcontent-ref %}

{% content-ref url="beqi.md" %}
[beqi.md](beqi.md)
{% endcontent-ref %}

{% content-ref url="bevelo.md" %}
[bevelo.md](bevelo.md)
{% endcontent-ref %}

## Where can I find out more?

This section provides full details of the designs of each of our existing beTokens. You can also raise any specific questions about our beTokens by reaching out to us on the [Beefy Discord](https://discord.gg/yq8wfHd) server.

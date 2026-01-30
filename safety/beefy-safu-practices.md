---
description: 'Last Update: January 2026'
---

# SAFU Standards

At Beefy, we recognise three words to live by: _SAFU First. Always._ You can craft the most incredible features into your smart contracts, but if you can’t adequately safeguard user funds, your contracts don’t deserve to have users. That’s why safety is the first, last and foremost consideration in every product we release.

This page describes the various practices that Beefy's contributors take to ensure that: (i) our new products are meet safety standards before launch; (ii) our existing products are properly maintained and observed; and (iii) our response to any security concerns are issues are rapid and safe. It also explains how live risk points are managed on the Beefy UI, to ensure users are appraised of any threats they may face.

<figure><img src="../.gitbook/assets/safu (2).png" alt=""><figcaption><p>Beefy has adopted a stringent risk management framework - our SAFU Standards - that assess a range of considerations for our autocompounding strategies to ensure all products meet our high security standards.</p></figcaption></figure>

## New Token Requirements

Before Beefy will consider a farm for vaulting, we ensure that the underlying tokens included in the product are all suitably SAFU for our users. New tokens must meet the following:

* token contracts must have been verified in the block explorer;
* non-native tokens must be from reputable bridges;
* new tokens must have sufficient liquidity; and
* tokenholders with more than 5% of circulating supply must not be either an externally-owed account (**"EOA"**) or a multi-signature account.

In addition, tokens are flagged as risky in our UI if they do not also meet the following:

* token contracts (and related protocol functionality) should be properly audited by reputable third-party providers;
* rug/migrator functions should be either completely removed or timelocked sufficiently;&#x20;
* token emission rates should be either hard capped or timelocked sufficiently; and
* all proxy implementation changes (i.e. upgrades to the contracts) should be timelocked.

As described in [risk-checklist.md](risk-checklist.md "mention"), we also look to identify and flag the following risk checks for all new tokens:

* If a large proportion of the circulating supply is concentrated in a small number of large holders, we flag the concentrated in the addressbook token flags; and
* If the article is a synthetic copy of another asset, meaning intended to be pegged to another asset's price but not backed and redeemable 1:1 for the underlying asset, we indicate that products using this asset involve synthetic assets.

## New Farm/Pool/Market Requirements

Before a new farm, pool or marekt is vaulted on Beefy, it must meet the following:

* contracts must have been verified in the block explorer;
* liquidity must be sufficient for swapping farm token rewards; and
* reward token emissions should be timelocked to ensure they cannot be changed unpredictably.

In addition, products are flagged as risky in our UI if they do not also meet the following:

* rug/migrator functions should be either completely removed or timelocked sufficiently;
* all proxy implementation changes (i.e. upgrades to the contracts) should be timelocked;
* if the underlying protocol is relatively new or has not secured significant value for a sustained duration, we indicate that it is not battle-tested;
* if the strategy for the new farm involves multiple layers of contracts or particularly novel or complicated logic, we indicate that it is a complex strategy; and
* if the underlying protocol involves the use of external curators to manage risk in their pools or markets, we flag that the product is curated.

## Vault Testing Procedure

Once a product has gone through due diligence and is being prepared, our strategists will follow a manual testing procedure on every new vault before it can go live on our app. This is to ensure that the vault works as intended and user funds are always SAFU. The sequential procedure is:

1. deposit a small amount of the asset;&#x20;
2. withdraw all;&#x20;
3. deposit again, wait 1 minute and check that `callReward()` is not 0;&#x20;
4. harvest the strategy;&#x20;
5. panic the strategy;&#x20;
6. withdraw 50% while panicked to make sure users can leave;&#x20;
7. try to deposit, an error should pop up but don't send the deposit through;&#x20;
8. unpause the strategy;  and then
9. deposit the 50% that has previously been withdrawn and harvest again.

## Strategy Upgrades

Occasionally, Beefy strategists will come out with a new innovative strategy, or yield farms change their reward contracts. In those circumstances, Beefy vaults have the flexibility to adapt to these changes, and can swap strategies so users don't have to migrate their funds to a new vault. This is done automatically by way of a strategy upgrade.

The new strategy is deployed with a dummy vault and all of the manual tests outlined above are completed. After passing the checks, the new strategy is assigned to the existing vault. The existing vault receives an onchain proposal for the new strategy to be added by way of the Beefy developer multi-sig wallet, and has to wait until the timelock delay has passed before the strategies are switched.

## Timelock Monitor

During the life of our vaults, the projects and protocols that we build on top of will naturally need to use functionality in their smart contracts which are susceptible to abuse (and for which a timelock was advisable for implementing a Beefy vault). To protect against the risk of abuse, we have implemented the #👀-timelock-monitor channel in the [Beefy Discord Server](https://discord.gg/yq8wfHd).

By displaying the relevant contract and protocol, the triggered event, the method scheduled to be called and the end time for the timelock, the Timelock Monitor provides all the information needed to assess the risk and protect user funds. As a public channel, the monitor provides free access to this information for our users, as well as insight into how Beefy’s team is handling these risks, to inform decision-making.

## Panic

Even with all of our precautions, sometimes something can go wrong with the underlying farm or assets in a Beefy vault, for which reacting quickly is of great importance. Beefy strategies have a keeper that is allowed to ["panic"](../developer-documentation/strategy-contract/#panic) the relevant strategy, which withdraws the staked funds from the farm back to the strategy contract and removes all allowances. This ensures that users funds are then kept available for the users to withdraw.

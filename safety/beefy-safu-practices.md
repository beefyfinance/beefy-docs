---
description: 'Last Update: February 2024'
---

# SAFU Standards

At Beefy, we recognise three words to live by: _SAFU First. Always._ You can craft the most incredible features into your smart contracts, but if you can’t adequately safeguard user funds, your contracts don’t deserve to have users. That’s why safety is the first, last and foremost consideration in every product we release.

This page describes the various practices that Beefy's contributors take to ensure that our new products are safe before launch, our existing products are properly maintained and observed, and our response to any security concerns are issues are rapid and safe. It also explains how live risk points  are managed on the Beefy UI, to ensure users are appraised of any threats they may face.

<figure><img src="../.gitbook/assets/safu (2).png" alt=""><figcaption><p>Beefy has adopted a stringent risk management framework - our SAFU Standards - that assess a range of considerations for our autocompounding strategies to ensure all products meet our high security standards.</p></figcaption></figure>

## New Token Requirements

Before Beefy will consider a farm for vaulting, we ensure that the underlying tokens included in the product are all suitably SAFU for our users. New tokens must meet the following:

* token contracts must have been verified in the block explorer;
* non-native tokens must be from reputable bridges;
* new tokens must have sufficient liquidity; and
* tokenholders with more than 5% of circulating supply must not be either an externally-owed account (**"EOA"**) or a multi-signature account.

In addition, tokens are flagged as risky in our UI if they do not also meet the following:

* rug/migrator functions should be either completely removed or timelocked sufficiently;&#x20;
* token emission rates should be either hard capped or timelocked sufficiently; and
* all proxy implementation changes (i.e. upgrades to the contracts) should be timelocked.

## New Farm Requirements

Before a new farm is vaulted on Beefy, the projects involved with the farm have to meet the following:

* contracts must have been verified in the block explorer; and
* liquidity must be sufficient for swapping farm token rewards.

In addition, vaults are flagged as risky in our UI if they do not also meet the following:

* rug/migrator functions should be either completely removed or timelocked sufficiently; and
* all proxy implementation changes (i.e. upgrades to the contracts) should be timelocked.

## New Vault Testing Procedure

Once a farm has been accepted and a vault is being prepared, our strategists will follow a manual testing procedure on every new vault before it can go live on our app. This is to ensure that the vault works as intended and user funds are always SAFU. The sequential procedure is:

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

## Risk Warnings

As described above, not all SAFU Standards are essential for Beefy's products, though every one is important. Where a token or farm meets all of the minimum standards but not all of the advisable points, a risk warning (as shown below) is displayed on the Beefy UI to notify users of the risk points specific to the relevant product(s).

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption><p>Where a product meets all minimum SAFU Standards, but does not meet all advisable points, a risk warning is displayed on the Beefy UI to warn users of the potential risks of the product.</p></figcaption></figure>

A comprehensive list of all risk points is also available in the [UI public repository](https://github.com/beefyfinance/beefy-v2/blob/main/src/locales/en/risks.json). These descriptions match those shown on the UI, and the comprehensive list allows for a top-down comparison of all the advisable risk points that Beefy is still willing to vault.

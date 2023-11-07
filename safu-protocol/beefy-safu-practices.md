---
description: '"Don''t Trust, Verify"'
---

# Beefy SAFU Practices

At Beefy, we recognise three words to live by: _SAFU First. Always._ You can craft the most incredible features into your smart contracts, but if you can’t adequately safeguard user funds, your contracts don’t deserve to have users. That’s why safety is the first, last and foremost consideration in every product we release.

This page describes the various practices that Beefy's contributors take to ensure that all new products are safe before launch, all ongoing products are properly maintained and observed, and that our response to any security concerns are issues are rapid and safe.

![Beefy has adopted a stringent SAFU management approach, that monitors a range of security factors as prerequisites for all of our products.](<../.gitbook/assets/safu (1).png>)

## New Farm Requirements

Before a new farm can be vaulted on Beefy, the projects involved with the farm have to pass a stringent set of SAFU rules:

* contracts must have been verified in the block explorer;
* non-native tokens must be from reputable bridges;
* liquidity must be sufficient for swapping farm token rewards;
* rug/migrator functions must be either completely removed or timelocked sufficiently;
* farm token emission rates must have been timelocked (if farm token pairs are being vaulted);
* farm token holders with >5% circulating supply must not be either externally owned accounts (**"EOAs"**) or multi-sigs; and
* all proxy implementation changes (i.e. upgrades to the contracts) must be timelocked.

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

## Strategy upgrades

Occasionally, Beefy strategists will come out with a new innovative strategy, or yield farms change their reward contracts. If that's the case, Beefy vaults have the flexibility to adapt to these changes, and have the ability to swap strategies so users don't have to migrate their funds to a new vault: it's done automatically by a strategy upgrade.

The new strategy is deployed with a dummy vault and all of the manual tests outlined above are completed. After passing the checks, the new strategy is assigned to the vault. The vault gets proposed the new strategy through a multi-sig wallet and has to wait until the timelock delay has passed before the vault uses the new strategy.

## Timelock Monitor

During the life of our vaults, the projects and protocols that we build on top of will naturally need to use functionality in their smart contracts which are susceptible to abuse (and for which a timelock was required to implement a Beefy vault). To protect against the risk of abuse, we have implemented the #👀-timelock-monitor channel on the [Beefy Discord](https://discord.gg/yq8wfHd).

By displaying the relevant contract and protocol, the triggered event, the method scheduled to be called and the end time for the timelock, the Timelock Monitor provides all the information needed to assess the risk and protect user funds. As a public channel, the monitor provides free access to this information for our users, as well as insight into how Beefy’s team is handling these risks, to inform decision-making.

## Panic

Even with all of our precautions, sometimes something can go wrong with the underlying farm or assets in a Beefy vault, for which reacting quickly is of great importance. Beefy strategies have a keeper that is allowed to panic, which withdraws the staked funds from the farm back to the strategy contract and removes all allowances. This ensures that funds are always available for Beefy stakers to withdraw in case of emergency.

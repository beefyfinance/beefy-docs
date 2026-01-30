---
description: 'Last Update: January 2026'
---

# Risk Checklist

<figure><img src="../.gitbook/assets/image (11).png" alt="Cover image for the Beefy Risk Checklist introductory article."><figcaption><p>Cover image for the Beefy Risk Checklist introductory article.</p></figcaption></figure>

The Beefy Risk Checklist is a module for [Beefy's web application](https://app.beefy.com/) aimed at updating users on the risk profile of the products they're exploring with a clear and succinct overview of key risk checks performed by Beefy.

{% hint style="danger" %}
The Risk Checklist is not intended as a substitute for user due diligence, nor as an endorsement of the safety of underlying assets or protocols included within the Beefy product. It is intended as an aid to user or professional due diligence only. **Don't trust, verify.**
{% endhint %}

Due diligence and risk evaluation in DeFi is an enormous and significant topic that all users face. We at Beefy recognise that it is impossible to concretely capture the full risk profile of any digital assets in a manner befitting a sleek and simple user interface. Nonetheless, we aim to ensure our users are prompted to explore key risks when using Beefy, and to kickstart their due diligence by showcasing some of the common checks performed by Beefy when onboarding new products.

In DeFi, projects like Beefy are often faced with a choice: either wash your hands of risk analysis entirely (_Do Your Own Research_), or help your users to navigate risks (while yourself suffering some risk of overreliance on that help). **Beefy chooses to help.** We care deeply about our users and always want to assist in identifying and managing risk where reasonably possible.

With that said, risk is a complex grey area, and one in need of constant improvement. We're always grateful for thoughts and feedback from our users to help us improve (see [Comment & Review](risk-checklist.md#comment-and-review)).

{% hint style="info" %}
To learn more about the context of the Risk Checklist and the specific updates introduced at the end of 2025, check out our [introductory article](https://beefy.com/articles/risk-checklist/) on safety changes introduced at the end of 2025.
{% endhint %}

## Checklist Items

The Beefy Risk Checklist is comprised of a selection of common checklist items that are applied to each and every product listed on the Beefy web application.&#x20;

Within the app, we attempt to display these checks simply with a one-line explanation of what the check indicates about the product. We then use red coloring and ❌ crosses to identify checks that have failed to fully pass our check (i.e. indicate some risk item that users ought to be aware of). We use green coloring and ✅ ticks to indicate checks performed which did not identify a specific risk.

By default, we only display risk items and do not show the checks that have passed (users must actively select _"Other checks"_ to see what other checks have been performed). We recognise that user psychology can sometimes assume that if most checks are green then the product is mostly safe. This is not the case: failing any one of our checks means that a material risk is inherent in the product which the user should research and understand.

The checklist design is flexible, meaning that more risk items can be added over time. Below we describe each risk item one by one.

<figure><img src="../.gitbook/assets/Screenshot 2026-01-27 at 10.06.15.png" alt="Screenshot of the Beefy Risk Checklist as it appears by default on the Beefy web application"><figcaption><p>Screenshot of the Beefy Risk Checklist as it appears by default on the Beefy web application.</p></figcaption></figure>

### Highly Complex

By _“highly complex”_, we mean that the product is inherently difficult for users to understand and assess risk for due to its combination of many layers of smart contracts, intertwined processes or even novel code that the user is unlikely to have seen before.&#x20;

There is nothing inherently risky about a system being complex, though experience tells us that — for smart contracts at the very least — complexity is correlated with risk.

We look at several key factors in determining high complexity:

* [ ] The Beefy strategy contains novel elements or many intertwined processes which may be likely to cause issues due to their complexity.
* [ ] The underlying protocols combine to add multiple layers between the user and the ultimate deployment of their assets.
* [ ] The underlying assets of a product involve multiple layers between the user and the ultimate exposure those assets provide.

The key factors listed above are alternative conditions for a product to be considered complex. If even one element of the product exhibits an unusually high level of complexity, then the whole product must be labelled as complex.

### Curated

By _“curated”_, we mean that the Beefy product depends directly upon the ongoing management of some designated curator or third party beyond Beefy and the issuers of the underlying platform/protocol.&#x20;

Though often thought of as external parties, we include as curators any project which retains centralised discretion to curate their products’ exposure to different underlying assets and strategies. Users should be made aware that they are putting their assets in the hands of a dedicated party who has some meaningful discretion over their allocation.

The sole factor in determining this checklist item is whether the underlying platform or asset relies on curators or other third parties to manage the product’s asset or risk allocations.

### Audited

By _“audited”_, we mean that all the core components which comprise the Beefy products (including all underlying protocols and assets) have been properly and publicly audited.

The use of the _"core components"_ is important here. Smart contract designs are often tweaked or feature minor updates over time without the need to re-audit the core logic. We do not look for fresh audits with every version update, but instead require that a public audit is available for the core logic (and any functionality which touches user funds) in the product we are building on top of.

We look at several key factors in confirming audited status:

* [ ] All Beefy contracts involved in the product should be derived from properly audited code.
* [ ] All underlying protocols involved in the product should have issued public audits for the core components of the system which the product relies on.
* [ ] All underlying assets involved in the product should have issued public audits for their core token contracts and any associated mechanisms (e.g. staking mechanisms).

The key factors listed above are all necessary conditions for a product to be considered audited.

### Battle-tested

By _“battle-tested”_, we mean that a protocol has been well tried and tested over a long-enough period and with sufficient value to indicate that the code is well proven. Were there to be relatively-obvious and exploitable issues with the code, we would expect that a protocol hosting sufficient value would be exploited at some stage.

Importantly, this is about more than just age or value. A codebase that has been around doing nothing for years and suddenly surged in value does not automatically become battle-tested by virtue of that value increase. It’s important that the value has been sustained consistently for a good portion of the protocol’s age (or that reasons for interruption are understood).

We look at several key factors to determine whether or not a product (and its underlying protocol) should be classified as _"battle-tested"_:

* [ ] Underlying protocols’ code has been public and live in production for at least 1 year.
* [ ] Underlying protocols’ code has secured an average of at least $100 million in value over a three-month period.
* [ ] If code is copied or forked from a battle-tested protocol, any material changes have been thoroughly reviewed, and must also be battle-tested independently if they secure meaningful value.

The key factors listed above are all necessary conditions for a product to be considered battle-tested.

### Correlated

By _“correlated”_, we mean that the directional exposure a product faces in only one direction, indicating a limited risk of impermanent loss at most. This is a careful choice of language, as we are not opining on the actual extent of impermanent loss, but rather the nature of the underlying assets and their theoretical profile with respect to impermanent loss.

We look at several key factors to assess the degree of correlation of a product:

* [ ] The product incorporates only single-asset markets and pools, indicating no exposure to impermanent loss.
* [ ] The product incorporates only identical or derivative assets, indicating minimal exposure to impermanent loss.
* [ ] The product incorporates only closely-correlated assets, indicating a more-limited risk of impermanent loss.

The key factors listed above are alternative conditions for a product to be considered correlated. Only products exhibiting no, minimal or limited risk of impermanent loss should be labelled as _"Correlated"_. All other products should be labelled as _“Not Correlated”_.

By _“identical assets”_, we mean assets that should in theory reflect the same thing, for example different deployments of the same stablecoin (e.g. a USDC-USDC.e pair). By “derivative assets”, we mean assets that are derived solely from another asset, and are purely intended to track its exact value (e.g. Synthetix’s sETH is a derivative of ETH).&#x20;

By _“closely-correlated assets”_, we mean assets that are based on the same core asset, but are expected to gradually alter their precise value over time. For instance: (i) a wrapped liquid-staking token that gradually grows in value as staking gains are compounded beneath the same deposit token (e.g. Lido’s wstETH); (ii) yield-bearing deposit tokens (e.g. Sky’s sUSDS); (iii) fiat-denominated money market instruments like treasury bills (e.g. Ethena’s USDtb).

### Timelocked

By _“timelocked”_, we mean that a project is making proper use of timelock smart contract standards to protect key functions from abuse.&#x20;

Critical functionality which can be called without warning or delay exposes products to risk; offering a timelock over these functions helps to build confidence that a project is not seeking to abuse these powers. This should apply across all protocols and assets incorporated into any Beefy product.

A proper timelock should rely on sound code from tried-and-tested timelock contracts, as well as incorporating a sufficiently-long timelock. What length is sufficient depends on the function, but we like to see a 24-hour timelock as a base standard, unless there is sufficient justification for a shorter time period.

We check the following sources for timelocks to validate this checklist item:

* [ ] All underlying protocols have guarded any critical functions from misuse by way of a timelock contract guarded by a project multi-sig wallet.
* [ ] All underlying assets have guarded any critical functions from misuse by way of a timelock contract guarded by a project multi-sig wallet.

The key factors listed above are all necessary conditions for a product to be considered timelocked.

### Verified

By _“verified”_, we mean that a project has properly ensured that all core smart contracts are publicly-verified and fully visible on at least one major blockchain explorer.&#x20;

This involves a process of submitting the deployed smart contract code to the explorer, to indicate that a live account can demonstrate that it has deployed the code. Only once verified can a project’s code be fully and properly reviewed by external parties.

We check the following timelock sources to validate this checklist item:

* [ ] All underlying protocols have publicly verified the core smart contracts involved in the products incorporated into the relevant Beefy product.
* [ ] All underlying assets have publicly verified the core smart contracts involved in the products incorporated into the relevant Beefy product.

The key factors listed above are all necessary conditions for a product to be considered verified.

### Synthetic Assets

By _“synthetic asset”_, we mean an asset that is pegged to and does not have 1:1 backing and redemption with a specified underlying asset, such as a fiat currency.&#x20;

This covers a wide variety of products, from fully-algorithmic stablecoins (which lack backing), to synthetic derivatives (e.g. Synthetix’s sETH), right the way through to overcollateralised stablecoins backed by assets other than fiat or other backed stablecoins (e.g. USDS).

The sole factor in determining this checklist item is whether any underlying assets in the Beefy product are synthetic in nature.

<figure><img src="../.gitbook/assets/Screenshot 2026-01-27 at 10.07.51.png" alt="Screenshot of the Beefy Risk Checklist on the Beefy web application when extended to show all checks performed."><figcaption><p>Screenshot of the Beefy Risk Checklist on the Beefy web application when extended to show all checks performed.</p></figcaption></figure>

## Application Configurations

Risk Checklist items are configured for each product on the Beefy web application through the [`beefy-v2` repository](https://github.com/beefyfinance/beefy-v2) (for Beefy products and platforms) and the [`beefy-api` repository](https://github.com/beefyfinance/beefy-api) (for tokens).&#x20;

These items are set by the relevant strategists involved with onboarding a new product, token or platform/protocol, and reviewed periodically as updates are added.

### Vault Config

The [vault config files](https://github.com/beefyfinance/beefy-v2/tree/main/src/config/vault) contain the full metadata of each Beefy product, including all of the items in the risk checklist. They are displayed as boolean values, where `false` indicates the risk is not relevant to this product, and `true` signals that the risk should be displayed on the app.

```json
// beefy-v2/src/config/vault/{chain}.json

{
  "id": "{platform-token0-token1}",
  ...
  "risks": {
    "complex": false,
    "curated": false,
    "notAudited": false,
    "notBattleTested": false,
    "notCorrelated": false,
    "notTimelocked": false,
    "notVerified": false,
    "synthAsset": false
  },
  ...
}
```

### Platforms Config

{% hint style="info" %}
Note that we refer interchangeably to _"Platform"_ and _"Protocol"_ in respect of the Risk Checklist. We mean the DeFi application that Beefy builds on top of to deposit user assets and earn fees or rewards.
{% endhint %}

The [platforms config file](https://github.com/beefyfinance/beefy-v2/blob/main/src/config/platforms.json) details all of the different DeFi protocols that Beefy builds on top of, providing the metadata to populate the web application. It also specifies platform-specific risks, ensuring that these risks are automatically inherited by the Risk Checklist (even if not flagged in the vault config).

```json
// beefy-v2/src/config/platforms.json

{
    "id": "{platform}",
    ...
    "risks": ["NO_TIMELOCK", "HIGHLY_COMPLEX", "NOT_BATTLE_TESTED"],
    ...
},
```

### Tokens Configs

The tokens config files form part of the Beefy [`blockchain-addressbook` package](https://www.npmjs.com/package/blockchain-addressbook), which lives within the [`beefy-api` repository](https://github.com/beefyfinance/beefy-api/tree/master/packages/address-book). Every token which has ever been added to Beefy is detailed in the addressbook.&#x20;

The `tags` field of each token entry in the addressbook is used to both identify the asset category and identify any checklist items arising in the token. As with the platform risks, these risks are then automatically inherited by the Risk Checklist, and override anything not flagged in the vault config.

```typescript
// beefy-api/packages/address-book/src/address-book/{chain}/tokens/tokens.ts

{token}: {
  ...
  tags: ['LARGE_HOLDERS', 'NO_TIMELOCK', 'STABLECOIN', 'SYNTHETIC'],
},
```

## Comment & Review

Beefy aims to provide one of the most effective and consistent risk reviews in DeFi, whilst ensuring our process remains accessible for users of any experience level and efficient for management across thousands of products.

With that said, risk profiles are ever-changing and keeping our reviews up to date is a constant struggle. We fully encourage and embrace comments and reviews from our community and from the projects we integrate and work alongside.

If you spot something in our checklists that you think is no longer accurate or needs to be revised, or want to provide general feedback on Beefy's approach to risk assessment, don't hesitate to reach out in the [Beefy Discord server](https://beefy.finance/discord).

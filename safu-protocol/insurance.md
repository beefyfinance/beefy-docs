---
description: 'Last Update: October 2022'
---

# Insurance

{% hint style="warning" %}
**Disclaimer:** Nothing on this page constitutes any formal insurance, legal or financial advice, or any recommendation to purchase or not purchase the products described herein. This page is intended for general information and educational purposes only. No warranty, whether express or implied, is given in relation to the information on this page. Beefy shall not be liable to readers for any technical, editorial, typographical or other errors or omissions associated with this page, or any harm, damage, losses or claims that may result from your use of this information. Always check the date of last update, to ensure the information on this page is not materially outdated.
{% endhint %}

Though Beefy does not offer insurance coverage directly to our users, there are a number of available products which offer cover for our protocol, smart contracts and users' portfolios. This page summarises the key types of DeFi insurance products that are available at present, some of the risks associated with them, and the different Beefy products that are available right now (including from our official partners and unaffiliated products).

## Why Insurance?

On a simple level, insurance can feel like a counterintuitive concept in DeFi, as the pace of change and technology development necessarily makes DeFi an inherently risky pursuit. But digging a bit deeper, we can observe that insurance is actually one of the earliest forms of decentralised financial products, in that it seeks to socialise risk and cost among thousands of willing participants, to ensure neither is concentrated at an individual level.&#x20;

At Beefy, we recognise that insurance is a requisite component of a stable, modern financial system, as it safeguards against massive damage and disruption arising from unlikely or unknowable, but retrospectively inevitable risks and events. Insurance allows users to enter the DeFi ecosystem and interact with this technology in a safer and more measured way, with protection against downside risks. It also helps to facilitate institutional capital, which may have more stringent risk management requirements that would otherwise isolate them from the space. As such, we think insurance helps to develop and extend DeFi, paving the way for mass adoption.

However, insurance is a complicated area of finance. Each and every underwritten policy is ultimately unique and deals with different types and levels of risk. As a result, it is vitally important that our users do their own research before buying insurance, and ensure their chosen products are suitable for them and priced fairly. It is always prudent to make sure to: (a) read the provider’s documentation and policy documents; (b) research the provider's financial position/backing to ensure it has sufficient liquidity to cover a pay out; and (c) check to ensure the policy's coverage is appropriate for the kinds of risks you wish to ensure against.

## Types of Insurance

As DeFi expands, the list of available insurance products is growing in tandem, including from both corporate and decentralised providers. Some of the key types include:

* **Smart Contact Coverage** - covers a specific smart contract-based product for a range of common issues like contract bugs, multi-sig failures and economic attacks. **For example:** [InsurAce's Smart Contract Vulnerability Cover](https://docs.insurace.io/landing-page/documentation-1/cover-wording/smart-contract-cover).
* **Protocol Coverage** - covers a specific DeFi protocol for a range of common risks and issues, like contract bugs, economic attacks and governance attacks. **For example:** [Nexus's Protocol Cover](https://nexusmutual.gitbook.io/docs/users/types-of-cover/protocol-cover).
* **Token Coverage** - covers a specific token product (e.g. an LP or autocompounding vault) for cross-stack risks in the underlying assets and protocols that the insured product is built on. **For example:** [Nexus's Yield Token Cover](https://nexusmutual.gitbook.io/docs/users/types-of-cover/full-stack-coverage-with-yield-token-cover) (e.g. Convex 3CRV), which covers failures in the issuing protocol (Convex), the LP/farm protocol (Curve) and the underlying tokens (DAI, USDC, USDT and CRV).
* **Portfolio Coverage** - covers a particular wallet up to a specified value of loss, including all applicable assets from insured protocols which the wallet holds. **For example:** [Solace's Portfolio Insurance cover](https://docs.solace.fi/docs/overview/faq/cover-products).
* **Custody/Custodian Coverage** - covers risks associated with custodial wallets and arrangements with centralised entities, including halted withdrawals, custodian hacks and haircuts arising from mismanagement. **For example:** [InsurAce's Custodian Risk Cover](https://docs.insurace.io/landing-page/documentation-1/cover-wording/custodian-risk-cover), and [Nexus's Custody Cover](https://nexusmutual.gitbook.io/docs/users/types-of-cover/custody-cover).
* **De-peg Coverage** - covers risks in an individual token product that arise as a result of the value of the asset de-pegging (i.e. failing to hold market value in line with the underlying assets that it is supposed to reflect). **For example:** [InsurAce's Stablecoin De-Peg Risk Cover](https://docs.insurace.io/landing-page/documentation-1/cover-wording/stablecoin-de-peg-cover) and [Nexus's Yield Token Cover](https://nexusmutual.gitbook.io/docs/users/types-of-cover/full-stack-coverage-with-yield-token-cover), which includes a number of specific de-peg risks.
* **Staking Coverage** - covers several risks that arise out of blockchain network staking and validating, such as missed rewards and slashing losses. **For example:** [Nexus's ETH2 Staking Cover](https://nexusmutual.gitbook.io/docs/users/types-of-cover/eth2-staking-cover), which specifically covers Ethereum's proof-of-stake beacon chain.
* **Bundled Product Coverage** - covers a combination of different protocols, products or different risks to create a single product that covers the users' overarching needs. **For example:** [InsurAce.io's CRV+CVX Bundled Cover](https://files.insurace.io/public/en/cover/Bundle\_CRV\_CVX\_v3.0.pdf), which targets Convex users with additional coverage for failures in Curve (which Convex is built on).

## Risks

Though Beefy advocates for the benefits of insurance, we also warn our users that insurance products themselves give rise to a number of risks which may result in your investment in the products being lost. In particular, we'd suggest users consider:

* **Coverage Amount** - insurance products typically require that you state upfront the amount of coverage that you want to purchase, typically denominated in fiat currencies. You may be encouraged to buy coverage up to the current value of your investment, or even above that. The coverage amount is typically not a guarantee of the amount you will be paid out, but does limit the maximum value of a pay-out. Furthermore, as the value of your assets change, the suitability of your coverage level will be impacted. For instance a sharp drop in the value of your portfolio will reduce the likelihood of claiming for the full coverage amount you obtained beforehand. Be sure to actively monitor your coverage levels.
* **Coverage Limitations** - coverage tends to be constrained to a closed list of claimable risk events (e.g. smart contract vulnerability covers "malfunction or programming flaw, or unauthorized, malicious, criminal attacks, hacks or exploits of any malfunction or programming flaw"). This may mean certain foreseeable events that you want cover for are not included in the product (e.g. a de-peg does not fall within the above definition, so is not covered by smart contract vulnerability cover).
* **Captured Products** - insurance products do not always seek to actively point out the limitations of their coverage and which products aren't captured. For instance, portfolio coverage may be tied to products which can be identified by the protocol, and may miss newer products or blockchains, resulting in inadequate coverage for your needs. As the product is general and the UI is user-friendly, you likely won't be told until your claim is rejected that specific products weren't captured in the coverage you purchased.
* **Pay Out Process** - all insurance products have strict conditions for paying out for a claim which must be met. For instance, some protocols require members to vote/decide on a claim before the protocol will pay out, which is a factor that is typically outside of users' control and unrelated to the pay out event. Be careful to check the process carefully when assessing whether a product is right for you, including assessing how frequently the product pays out for claims.
  * For example, insurance covering Beefy's protocol or smart contracts will likely pay out if our contracts fail, but will not pay out if the underlying assets that our contracts are built on top of fail. This happened with the Terra UST collapse, where our smart contracts worked as intended, even as the underlying assets' value sank towards zero.
* **Providing Coverage** - some decentralised insurance providers (e.g. InsureDAO, Bridge Mutual) offer peer-to-peer insurance products, where users can provide coverage to the protocol as an investment in exchange for a share of the premiums paid by coverage purchasers. Beefy warns our users that these products expose coverage providers to an asymmetric risk of losing your **entire** investment if there is a pay out event under the policy.&#x20;
  * Providing insurance coverage is effectively a bet on the security of the underlying protocol or smart contracts. Though our SAFU practices are Beefy's top priority, we would not encourage ordinary users to bet on the security of any rapidly changing DeFi technologies.
  * Where Beefy can offer you a similar rate of return on your assets whilst avoiding the pay-out risk, we know where we'd rather invest our funds...  :cow: :cow: :cow:&#x20;

## Partner Products

To bring the benefits of DeFi insurance to our users, Beefy has partnered with a selection of the leading insurance providers in the space, to create products which offer coverage over our protocol, products and contracts. At the time of writing, these are:

### InsurAce.io

InsurAce is a multi-chain insurance provider deployed on a range of chains including Ethereum, BSC, Avalanche, and Polygon. It offers coverage against Beefy smart contract vulnerability over more than half of the chains Beefy is deployed on.

The precise make up of InsurAce's organisational is not entirely clear, though InsurAce has some incorporated legal forms (e.g. InsurAce Global Limited in the UK). It's protocol is made up of two parts: an insurance arm and an investment arm. The investment arm generates profits from fees collected to fund their insurance activities. Users pay a fee (typically 2-5% APY) when using covered smart contracts and are reimbursed for their deposits if it fails.&#x20;

InsureAce operates a dedicated claims department that will review the different types of claims that can be submitted and vote on the outcome. The claim is first investigated by InsureAce's Advisory Board, which includes experts in Insurance, Security and Legal/Compliance. InsurAce are also aiming to develop a decentralised governance process over time, including the use of community Claim Assessors (who are $INSUR holders that have staked their tokens on the platform) to decide the outcome of claims. However, at the time of writing, the [Claim Assessor page](https://app.insurace.io/claim-assessor) is not live, and the current state of affairs is not made clear on the protocol site.

For more information, see our blog post [here](https://beefy.com/articles/get-to-grips-with-beefy-s-smart-contract-insurance-provided-by-insurace/) and find the InsurAce Beefy product on the coverage products page [here](https://app.insurace.io/coverage/buycovers) (Product ID #110). You can find raw data on InsurAce's coverage [here](https://data.insurace.io/cover-records).

### Nexus Mutual

Nexus Mutual is an Ethereum-based insurance alternative that provides coverage against specific protocols, yield tokens and custodians (i.e. centralised exchanges). It offers protocol coverage for Beefy across the vast majority of our deployed chains.&#x20;

Unlike most other providers, Nexus is a discretionary mutual whose members receive insurance-like protection, though it doesn't formally sell insurance. The project uses aligned incentives to enable risk-sharing among all its members, as members act as risk and claim assessors, whilst contributing capital to the protocol. Ownership of Nexus Mutual’s token, NXM, is used to buy cover and navigate the claims and risk assessment process. Holders can also take part in the Mutual's governance too.

Nexus offers a range of products including general protocol cover (i.e. covering all different products offered by the protocol) as well as "yield token cover", which covers the full stack of a yield bearing asset (e.g. base assets, liquidity pool and autocompounding vaults). Nexus also offers other novel products such as Ethereum 2.0 staking cover, and custodian cover which protects against the risk of loss caused by keeping assets in the custody of a centralised exchange.

For more information, see our blog post on the partnership [here](https://beefy.com/articles/cover-your-deposits-with-nexus-mutual/), and the Nexus Beefy product page [here](https://app.nexusmutual.io/cover/buy/get-quote?address=0x453D4Ba9a2D594314DF88564248497F7D74d6b2C). Details of the different types of coverage and their terms and conditions are available in Nexus' documentation [here](https://nexusmutual.gitbook.io/docs/users/types-of-cover).

### Solace

Solace is a decentralised, DAO-run insurance protocol, on a mission to forge innovation into intuitive protection tools for crypto explorers. It offers coverage for funds invested in Beefy as part of its all-encompassing portfolio insurance product.

By contrast to others, Solace has adopted a novel approach to claims (its optimistic payouts system), wherein users are not required to file claims following an insured event, but are instead automatically paid out where Solace's risk management team assesses that any event has occurred through on-chain analytics. For the future, Solace is also developing a parametric automated claims assessment system, which will be used to automatically quantify loss events using on-chain analytics.

Solace also provides an additional product (Solace Native) for protocols to cover their own smart contracts. This involves protocols holding underwriting tokens, which can be used to vote on a gauge allocation for their protocol among the wider underwriting pool.&#x20;

For more information, see Solace's twitter thread on the Beefy partnership [here](https://twitter.com/SolaceFi/status/1491533263936098305?s=20\&t=jZMt6Lw4uyPfW5NUPtW6UA), and check out Solace's documentation [here](https://docs.solace.fi/).

{% hint style="info" %}
Please note that Solace's portfolio insurance is tied to their implementation of Zapper's tooling for detecting the value of assets in your wallets. Where these tools do not detect your Beefy assets (e.g. if they're newly issued), you may not be able to recover for those assets under your policy. Always make sure to thoroughly check the "My Portfolio" and "Quote Simulator" parts of your ["My Policy" page](https://app.solace.fi/cover) on Solace's app to check what their Zapper implementation can detect, as this is the limit of what's covered by your policy (even if you purchase more coverage!).
{% endhint %}

### Comparison

<table><thead><tr><th width="157">Criteria</th><th width="194">InsurAce.io</th><th width="195">Nexus Mutual</th><th>Solace</th></tr></thead><tbody><tr><td>Deployed Chains</td><td>Ethereum, BSC, Polygon, Avalanche</td><td>Ethereum</td><td>Ethereum, Polygon, Aurora, Fantom</td></tr><tr><td>Beefy Chains Covered</td><td>9 chains, including BSC, Polygon and Fantom</td><td>15 chains including BSC, Polygon and Fantom</td><td>Not stated. Portfolio detected through Zapper. Includes coverage beyond deployed chain.</td></tr><tr><td>Product Types</td><td>Smart Contract, Custodian, De-Peg, Bundled.</td><td>Protocol, Yield Token, Custody, Staking (Smart Contract phased out)</td><td>Portfolio (and Native)</td></tr><tr><td>Beefy Product Types</td><td>Smart Contract</td><td>Protocol</td><td>Portfolio</td></tr><tr><td>Claim Assessment</td><td>Private Advisory Board</td><td>Public Members Vote</td><td>Private Automated Claims</td></tr></tbody></table>

## Unaffiliated Products

As Beefy is entirely open source and public, anyone is free to build on top of our products and code. However, this transparency can cause some confusion for ordinary users as to which products are built and tested by our team, and which aren't. Some insurance providers seek to add to this confusion by stating that their products are "official" or "verified", when they are nothing to do with Beefy. It is ultimately up to the user to do your own research and check that the product is what you think it is.

Below is a list of known products insurance products that offer coverage for Beefy's products or protocol, but are not officially offered in partnership with Beefy and have not been formally verified by our teams. Use at your own risk, and always do your own research.

<table><thead><tr><th width="159">Provider</th><th width="155">Insurance Type</th><th width="142">Blockchain(s)</th><th>Smart Contract(s)</th></tr></thead><tbody><tr><td><a href="https://app.insuredao.fi/optimism/purchase/0xe3f491c575e02902342ef8488bb3d6c392869fda">InsureDAO</a></td><td>Smart Contract</td><td>Optimism</td><td>0xe3f491c575e02902342ef8488bb3d6c392869fda</td></tr><tr><td><a href="https://app.bridgemutual.io/user/cover/137/0xf0E147862E069460D2ea8837f65aD5D2fCaC2D14">Bridge Mutual</a></td><td>Smart Contract</td><td>Polygon</td><td>0xf0E147862E069460D2ea8837f65aD5D2fCaC2D14</td></tr></tbody></table>

{% hint style="danger" %}
Readers are warned to note and consider the "Providing Coverage" risk in the [#risks](insurance.md#risks "mention") section above when considering these unaffiliated products.
{% endhint %}

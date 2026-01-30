---
description: 'Last Update: January 2026'
---

# Audits & Bounty

{% hint style="info" %}
For immediate access to Beefy's completed audit reports, visit the [`beefy-audits` repo](https://github.com/beefyfinance/beefy-audits).
{% endhint %}

To strengthen our mesh of security measures, Beefy also makes use of external assistance from industry-leading developers to identify problems and help craft solutions.

External support is typically _ad hoc_ in nature, arising particularly around new product development and launches, and where major upgrades or novel bugs emerge. Though Beefy seeks to maintain relations with a wide range of external blockchain security experts and organisations, we do not have standing engagements with preferred providers (save for our ongoing bug bounty).

## Formal Audits

Beefy's contributor team have gone through over a dozen audits across the project's lifetime for different products and variations on Beefy's core design. Each of the completed audit reports is available in the [`beefy-audits` repo](https://github.com/beefyfinance/beefy-audits).

In the below table, we divide those audits into several core categories:

<table><thead><tr><th width="279.1953125">Category</th><th width="155.74609375">Audits Complete</th><th width="270.5703125">Notable Auditors</th></tr></thead><tbody><tr><td>Core Beefy <a href="../beefy-products/vaults.md">Vault</a> &#x26; <a href="../beefy-products/strategies.md">Strategy</a></td><td>4</td><td>DeFiYield; CertiK</td></tr><tr><td><a href="../ecosystem/bifi-token/">BIFI Token</a></td><td>1</td><td>Zellic</td></tr><tr><td><a href="../developer-documentation/other-beefy-contracts/beefywrapper-contract.md">ERC-4626 Wrapper</a></td><td>1</td><td>Zellic</td></tr><tr><td><a href="../faq/how-to-guides/how-to-beefy-zap.md">Zap Tools</a></td><td>1</td><td>OpenZeppelin</td></tr><tr><td><a href="../beefy-products/clm.md">Cowcentrated Liquidity Manager</a></td><td>4</td><td>Zellic, Cyfrin, Certora, Sherlock</td></tr><tr><td><a href="../beefy-products/beefy-escrowed-tokens/bes.md">beS</a></td><td>1</td><td>Electisec</td></tr></tbody></table>

For auditors interested in working with Beefy, we maintain lists of potential providers, and will be happy to open a conversation and include you for consideration. Please reach out via the Beefy Discord to learn more.

## Audit Competitions

Audit competitions are a growing trend in DeFi to augment or substitute a traditional formal audit. Providers open up submissions to the public (and typically their own network of independent security researchers) and implement a process to review submissions alongside the project, looking for valuable contributions to be rewarded.&#x20;

Unlike a traditional bug bounty, audit competitions aim to accelerate the process of reviewing a new codebase by incentivising many reviewers to evaluate the code simultaneously and in competition with one another. They guarantee a pot of prizes for submissions, encouraging participants to submit as many issues as they can in case there are few other submissions (meaning they take a larger share of the prize pot).

The downside of audit competitions is they can involve a huge amount of work from the team, and incentivise nonsense or low-quality submissions. Though the quality of reviewers can be very high, there are no assurances that actual participation will be of a high-quality, unlike a traditional audit. As such, competitions are typicall complimentary to (not contrasted with) audits and bug bounties.

Beefy hosted a [CLM contest](https://audits.sherlock.xyz/contests/303) with Sherlock in May 2024, receiving 134 submissions but finding only 1 medium-severity bug.

## Bug Bounty

Beefy has offered a bug bounty program with [ImmuneFi](https://immunefi.com/bug-bounty/beefyfinance/information/) since July 2021. ImmuneFi is a platform for white-hat hackers and security experts to identify DeFi projects with bounty programs for them to review. Successful bugs identified by participants (and submitted through ImmuneFi) will receive a payout from Beefy's bug bounty fund to incentivise cooperation and support.

Due to the nature of how ImmuneFi works, the program shows specific contract addresses that are included within scope. However, the Beefy protocol integrates several thousand contracts at any given time, meaning that it is not always possible to ensure every contract is included with the scope. Beefy will generally honour the bounty in respect of live operational products displayed in our web application (not retired or paused) if submitted via ImmuneFi.

Questions in relation to our bounty program and audits can be submitted to the contributor team through the [Beefy Discord server](https://beefy.finance/discord).

---
description: 'Last Update: April 2026'
---

# Crosschain Zaps

### What are crosschain zaps?

Crosschain zaps are a massive upgrade to the Beefy user experience that lets you deposit into thousands of different yield strategies across multiple networks with a single click.&#x20;

You can now enter Beefy products in a single transaction using any supported token across 10 different blockchains.

You no longer need to figure out manual bridging or learn the nuances of individual networks—just select a route, approve the token, and zap.&#x20;

### Why did Beefy build crosschain zaps?

Traditional yield farming is often difficult, time-consuming, and risky. To get into a single vault, a user might have to navigate and wrap funds through 5 or 6 different protocols. By bundling all of these complex steps into one straightforward workflow, zap blurs the lines between active yield farmers and set-and-forget investors, making high yields accessible to users of all skill levels.&#x20;

### How do crosschain zaps work under the hood?&#x20;

Crosschain zaps aggregate and automate processes like simulating deposits, fetching quotes from multiple aggregators (like KyberSwap or 1inch), calculating precise swaps, and executing the crosschain bridge. On a technical level, it relies on three core components:&#x20;

* The “BeefyZapRouter”: a contract on the source chain that receives your transaction and processes arbitrary logic to deploy your assets for bridging and zapping.
* The “Hook Executor”: a private Beefy service that listens for your bridging event, fetches a cryptographic attestation from Circle’s API, and relays the message to your destination chain.
* The “CircleBeefyZapReceiver”: a contract on the destination chain that receives the bridged message, mints your bridged funds, executes the final deposit into the target Beefy Vault, and returns your receipt token (mooTokens).

For a more detailed explanation, see the [Zap page](https://docs.beefy.finance/beefy-products/zap#beneath-the-hood).

### How do I know what assets I have to zap?

A crosschain zap starts as a normal zap: after clicking deposit or withdraw, you’ll see a list of all supported chains and the top assets you have on them (shown with their token icons). Clicking a chain shows you a detailed overview of all of the assets on that chain which you can use to zap with.

### Which networks can I zap across?

Currently, crosschain zaps are available on 10 networks: Ethereum, Base, Arbitrum, OP Mainnet, Polygon, Avalanche, Linea, Monad, HyperEVM, and Sonic.

### What are the fees for crosschain zaps?

For crosschain zaps there are fixed and variable price elements.

The fixed element ($) - known as the Relay fee - is $0.10 for all chains save for Ethereum and Linea (where it’s $1). It's charged by Beefy to cover the cost of claiming bridged assets and initiating deposits.&#x20;

The variable element (%) is an aggregate of Beefy’s swap fees and bridge fees charged by CCTP. They're applicable on any step that swaps or bridges respectively. Zap fees displayed on the app are an approximation - check the tooltip for a precise breakdown.

For a more detailed breakdown of fees, see the [Zap page](https://docs.beefy.finance/beefy-products/zap#fees).

### I’m not seeing crosschain zap as an option for my chosen vault. Is this a glitch?

Though crosschain zap supports almost 1,000 Beefy products, not all products are currently zappable, meaning the option to zap from other chains will not be shown. Underlying protocols like Balancer V3 and Pendle require complex integrations to facilitate zaps, meaning zap may only be supported for some products or chains, or even for none at all. To find products which benefit from crosschain zaps, filter to the 10 supported chains and then check the “Zappable” tag in the filter bar.

### I tried using a crosschain zap but my transaction didn’t fully complete. Where did my funds go?

Depending on where in the process things stalled, your funds may be on the source chain in your deposit asset or USDC, or on the destination chain in USDC, the product’s deposit assets or the product’s deposit token. Your funds are typically returned to your wallet address, or waiting to be minted via CCTP on the destination chain (from which they can always be recovered later).

To begin with, check your transacting wallet’s balances and history, looking for any indication of additional USDC or deposit assets arriving in your wallet. If neither are found on the source or destination chain, reach out to Beefy in the #tech-support channel on our Discord server, and we will assist with minting from CCTP on the destination chain.

The Beefy web application displays the progress of zaps and invites users to continue zapping where the process is interrupted. Don’t panic if you don’t see these notifications or accidentally close the app, the process can always be resumed if you reach out to us.

### Why do crosschain zaps use Circle CCTP for bridging?

Circle's Cross-Chain Transfer Protocol (CCTP) is the perfect intermediary because it offers a consistent and uniform experience across highly fragmented blockchain architectures. Because USDC is stable and prioritized across DeFi, Beefy can use it to securely bridge value without having to stitch together a complicated fabric of different native tokens and smart contract standards.&#x20;

### How are my assets secured during a crosschain zap?

Crosschain zaps build exclusively on Circle CCTP, so all bridged assets are secured by Circle’s technology throughout the bridging process.&#x20;

CCTP is a crosschain messaging service (meaning it orders the release of equivalent assets on the destination chain) rather than a canonical bridge (which guarantees the storage of underlying assets on their native chain). Though traditionally canonical bridges have been viewed as offering stronger guarantees as to the backing and security of the underlying assets, in Circle’s case native USDC is all backed by underlying US dollars supported by a uniform guarantee from Circle. As such, all of the assets used during a crosschain zap’s bridging process carry the exact same level of security and legal guarantees throughout the process.&#x20;

CCTP’s positioning as a messaging service helps to dramatically lower the time and cost of bridging transactions, making it the perfect choice for DeFi integrations when coupled with their trusted institutional backing.

### Are crosschain zaps safe? What happens if a crosschain transaction fails in the middle?

Beefy built the UI and the smart contracts to be highly robust and capable of handling external issues with swap and bridge providers. On the destination chain, the final zap execution is wrapped in a "try/catch" mechanism. This means if a step fails, the transaction doesn't simply revert and get stuck; instead, it safely triggers a recovery path to ensure a proper refund or recovery outcome. Additionally, the Zap V3 core router codebase that this is built upon was audited by OpenZeppelin.

---
description: 'Last Update: April 2026'
---

# Contracts & Timelocks

### Addressbook

All addresses used are open source and verifiable. A collection of useful addresses on Beefy's chains for DeFi development are stored on GitHub: [Addressbook](https://github.com/beefyfinance/beefy-api/tree/master/packages/address-book).

### Contracts

From the Vault UI, one can easily find the Strategy addresses and Vault addresses. Additionally, all Beefy vault contracts can be viewed on [app.beefy.com](https://app.beefy.comhttps/app.beefy.com/). One can use this dashboard for example to check the [harvesting and compounding rate of a vault](../faq/how-to-guides/how-to-check-harvesting-compounding-rate.md).

### Oracles

Beefy's contracts do **not** use external oracles. The problem with oracles is, in short, that its data can be inaccurate or manipulated, and unreliable oracles can lead to exploits. Because Beefy's contracts do **not** rely on external data in any form, such as asset prices, our vaults are **not** susceptible to flashloan exploits.

### Timelocks

Beefy ensures that all privileged functions and upgrades are protected by standardised smart contract timelocks.&#x20;

Our strategy, vault and reward pool contracts (as well as any other contracts that handle user funds) are made ownable with ownership transferred to either the Beefy vault owner or the Beefy strategy owner on the relevant chain. Timelocked functions are then queued by the [Beefy Developer Multisig](contracts-and-timelocks.md#developer-multisig), and may be executed by individual contributors once the timelock has elapsed.

By default, a 6-hour timelock is configured for all strategy changes and upgrades. This allows sufficient warning and notice of significant changes, while allow Beefy to react rapidly to material changes or new risk vectors. Detailed of scheduled timelock transactions are published live to the Beefy Discord server in the #-citadel channel.

Vault and strategy owner addresses can be found in the [addressbook](contracts-and-timelocks.md#addressbook) under the Beefy protocol files.

### Developer Multisig

The Beefy developer multisig is staffed by Beefy's experienced senior developers and maintains responsibility for all privileged functions across Beefy's smart contracts. It is a 3 of 6 multisig

To effect these responsibilities, the dev multisig is set as either the direct owner of Beefy's contracts or as the owner of the timelock which in turn owns Beefy's contracts. The intention is that all privileged functionality should run through and be secured by the protection of the multisig.

All transactions are proposed either by members of the Developer Council or using automated bots to gather standardised calldata for common transactions. Only the Developer Council has signing rights, and the multisig facilitates no delegates or external roles.

The dev multisig is operating with best practices in line with Beefy's [multisig policies](contracts-and-timelocks.md#multisig-policies).

### Treasury Multisig

The Beefy's treasury multisig is staffed by Beefy's senior core contributors and maintains responsibility for gathering, custodying, deploying and spending Beefy DAO's treasury assets. It is a 4 of 7 multisig

Unlike the [dev multisig](contracts-and-timelocks.md#developer-multisig), the treasury multisig does not have access to any privileged functions or assets held by the Beefy protocol, and its functionality is solely linked to the Beefy DAO. Nonetheless, it secures millions of dollars of assets at any given time, and so great care and attention is paid to the signing and execution of transactions.

All transactions are proposed either by members of the Treasury Council or using automated bots to gather standardised calldata for common transactions. Only the Treasury Council has signing rights, and the multisig facilitates no delegates or external roles.

The dev multisig is operating with best practices in line with Beefy's [multisig policies](contracts-and-timelocks.md#multisig-policies). See the [treasury.md](../dao/treasury.md "mention") page for further information about the Beefy Treasury.

### Multisig Policies

Both Beefy's dev and treasury multisigs are operated in accordance with standard best practices for the operation of multisigs:

* All signers are longstanding contributors to Beefy DAO who have been known and vetted over the course of several years;
* Each signer is an independent human and distinct from all other signers;
* All signers are located in different geographic locations from all other signers;
* All signers must be EOAs and not multisigs or other smart contract accounts where ownership is capable of being transffered or shared;
* Contributors with private pre-existing relationships (e.g. friends, colleagues, couples) may not sit on the same multisig as one another;
* No external delegations or roles are granted to either multisig, save for automated proposal generation by bots developed and maintained by the Beefy Developer Council;
* Signers are occasionally reshuffled, bringing different members of the contributor team onto the multisigs and ensuring that all multisig signers are active contributors;
* Signers are anonymous, and details of their precise signing capabilities and setup are kept confidential;
* Regular advice and security updates are provided to all signers to ensure they are aware of best practices; and
* Private accounts for email, cloud storage and password management are provided to all signers, helping them to operate their roles without using personal or preexisting accounts or comingling their work.

Importantly, Beefy multisig signers are not doxxed or identity checked, and no personal data on our signers is stored. Where traditional institutions may rely on identification and audit trails to provide legal certainty and accountability, Beefy prioritises privacy and relies on modern technology and security standards to ensure the safe operation of multisigs.&#x20;

Put simply: Beefy focuses on minimising the surface area for issues with our multisigs, rather than paths for recourse after issues have already arisen.&#x20;

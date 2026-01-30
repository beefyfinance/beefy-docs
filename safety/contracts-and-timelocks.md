---
description: 'Last Update: January 2026'
---

# Contracts & Timelocks

## Addressbook

All addresses used are open source and verifiable. A collection of useful addresses on Beefy's chains for DeFi development are stored on GitHub: [Addressbook](https://github.com/beefyfinance/beefy-api/tree/master/packages/address-book).

## Contracts

From the Vault UI, one can easily find the Strategy addresses and Vault addresses. Additionally, all Beefy vault contracts can be viewed on [app.beefy.com](https://app.beefy.comhttps/app.beefy.com/). One can use this dashboard for example to check the [harvesting and compounding rate of a vault](../faq/how-to-guides/how-to-check-harvesting-compounding-rate.md).

## Oracles

Beefy's contracts do **not** use external oracles. The problem with oracles is, in short, that its data can be inaccurate or manipulated, and unreliable oracles can lead to exploits. Because Beefy's contracts do **not** rely on external data in any form, such as asset prices, our vaults are **not** susceptible to flashloan exploits.

## Example contracts

* DAI/USDC/USDT (Curve - Avalanche) vault code: [https://snowtrace.io/address/0x79A44dc13e5863Cf4AB36ab13e038A5F16861Abc#code](https://snowtrace.io/address/0x79A44dc13e5863Cf4AB36ab13e038A5F16861Abc#code)
* CAKE-BNB (PancakeSwap - BNB Chain) strategy code: [https://bscscan.com/address/0xDE238C509bcCBCd91B90dE40dF3e25B43A131311#code](https://bscscan.com/address/0xDE238C509bcCBCd91B90dE40dF3e25B43A131311#code)

## Timelocks

Contracts are secured with timelocks and multi-sig dev wallets. A 6 hour timelock is used for agility to make needed changes to keep our contracts secure, and as an added layer of protection the timelock is governed by a 3/5 signer multisig.

## Developer Multisigs

Multi-signature developer wallets are used to deploy changes to contracts, such as upgrading vault strategies. This ensures a secure workflow where every change is approved by Beefy's developers.

## Treasury Multisigs

Beefy's treasury spending is secured by requiring multiple signatures from trusted (community) members. [As voted on by the DAO](https://vote-archive.beefy.finance/#/beefy/proposal/QmR5mzwjs46b3YRYWtc12CqqxF6r7VfpPd6ZfiRXnR69go), the following members represent the Treasury Council: Power, AllTrades, Pablo, mjoaris, TBC, DefiDebauchery and YR2150. See the [treasury.md](../dao/treasury.md "mention") page for further information about the Beefy Treasury.

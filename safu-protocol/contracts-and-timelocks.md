# Contracts & Timelocks

## Address Book

All addresses used are open source and verifiable. A collection of useful addresses on Beefy's chains for DeFi development are stored on GitHub: [Address Book](https://github.com/beefyfinance/beefy-api/tree/master/packages/address-book).

## Contracts

From the Vault UI, one can easily find the Strategy addresses and Vault addresses. Additionally, all Beefy vault contracts can be viewed on [dashboard.beefy.finance](https://dashboard.beefy.finance). One can use this dashboard for example to check the [harvesting and compounding rate of a vault](../faq/how-to-guides/how-to-check-harvesting-compounding-rate.md).

## Oracles

Beefy's contracts do **not** use external oracles. The problem with oracles is, in short, that its data can be inaccurate or manipulated, and unreliable oracles can lead to exploits. Because Beefy's contracts do **not** rely on external data in any form, such as asset prices, our vaults are **not** susceptible to flashloan exploits.

## Example contracts

* DAI/USDC/USDT (Curve - Avalanche) vault code: [https://snowtrace.io/address/0x79A44dc13e5863Cf4AB36ab13e038A5F16861Abc#code](https://snowtrace.io/address/0x79A44dc13e5863Cf4AB36ab13e038A5F16861Abc#code)
* WBTC (Scream - Fantom) lending strategy code: [https://ftmscan.com/address/0x4374207377C1A36e386A757B774D53a0B6Ff2cEE#code](https://ftmscan.com/address/0x4374207377C1A36e386A757B774D53a0B6Ff2cEE#code)
* CAKE-BNB (PancakeSwap - BNB Chain) regular strategy code: [https://bscscan.com/address/0xDE238C509bcCBCd91B90dE40dF3e25B43A131311#code](https://bscscan.com/address/0xDE238C509bcCBCd91B90dE40dF3e25B43A131311#code)

## Timelocks

Contracts are secured with timelocks and multi-sig dev wallets. A 6 hour timelock is used for agility to make needed changes to keep our contracts secure, and as an added layer of protection the timelock is governed by a 3/5 signer multisig.&#x20;

* Arbitrum (6 hours): [0x6d28afD25a1FBC5409B1BeFFf6AEfEEe2902D89F](https://arbiscan.io/address/0x6d28afD25a1FBC5409B1BeFFf6AEfEEe2902D89F)
* Avalanche (6 hours): [0x37DC61A76113E7840d4A8F1c1B799cC9ac5Aa854](https://snowtrace.io/address/0x37DC61A76113E7840d4A8F1c1B799cC9ac5Aa854)
* BSC (6 hours): [0x65CF7E8C0d431f59787D07Fa1A9f8725bbC33F7E](https://bscscan.com/address/0x65cf7e8c0d431f59787d07fa1a9f8725bbc33f7e)
* Celo (6 hours): [0x5B96bbAca98D777cb736dd89A519015315E00D02](https://explorer.celo.org/address/0x5B96bbAca98D777cb736dd89A519015315E00D02/transactions)
* Cronos (6 hours): [0x4f4DB83d75876f34fd927d5fa78D5D7b4479E6ce](https://cronoscan.com/address/0x4f4DB83d75876f34fd927d5fa78D5D7b4479E6ce)
* Fantom (6 hours): [0x847298aC8C28A9D66859E750456b92C2A67b876D](https://ftmscan.com/address/0x847298aC8C28A9D66859E750456b92C2A67b876D)
* Fuse (6 hours): [0xa9E6E271b27b20F65394914f8784B3B860dBd259](https://explorer.fuse.io/address/0xa9E6E271b27b20F65394914f8784B3B860dBd259/transactions)
* HECO (6 hours): [0x587479672077fBD7cb08EE1fd13fca6a9ef69d9e](https://hecoinfo.com/address/0x587479672077fBD7cb08EE1fd13fca6a9ef69d9e)
* Metis (6 hours): [0xdf68Bf80D427A5827Ff2c06A9c70D407e17DC041](https://andromeda-explorer.metis.io/address/0xdf68Bf80D427A5827Ff2c06A9c70D407e17DC041/transactions)
* Moonriver (6 hours): [0xc8BD4Ae3d3A69f0d75e3788d2ee557E66EBC98D8](https://moonriver.moonscan.io/address/0xc8BD4Ae3d3A69f0d75e3788d2ee557E66EBC98D8)
* Harmony One (6 hours): [0x6d28afD25a1FBC5409B1BeFFf6AEfEEe2902D89F](https://explorer.harmony.one/address/0x6d28afd25a1fbc5409b1befff6aefeee2902d89f)
* Polygon (6 hours): [0x6fd13191539e0e13B381e1a3770F28D96705ce91](https://polygonscan.com/address/0x6fd13191539e0e13b381e1a3770f28d96705ce91)

## Developer Multisigs

Multi-signature developer wallets are used to deploy changes to contracts, such as upgrading vault strategies. This ensures a secure workflow where every change is approved by Beefy's developers.

* Arbitrum: [0xf7EC8986c660Fa8269f6440A631B22337f398Ccd](https://gnosis-safe.io/app/arb1:0xf7EC8986c660Fa8269f6440A631B22337f398Ccd/)
* Avalanche: [0x3A0b8B7a3ea8D1670e000b1Da5bD41373bF8da42](https://gnosis-safe.io/app/avax:0x3A0b8B7a3ea8D1670e000b1Da5bD41373bF8da42/balances)
* BSC: [0x44b74ED902e6423B51Bd9e44B6e5646749376943](https://gnosis-safe.io/app/bnb:0x44b74ED902e6423B51Bd9e44B6e5646749376943/)
* Fantom: [0x238dc3781DD668abd5135e233e395885657D304A](https://safe.fantom.network/#/safes/0x238dc3781DD668abd5135e233e395885657D304A/)
* Fuse: [0xe26a8aC2936F338Fd4DAebA4BD22a7ec86465fE1](https://gnosis-safe.fuse.io/fuse:0xe26a8aC2936F338Fd4DAebA4BD22a7ec86465fE1/)
* Harmony: [0xE3c985f5e317eFd4aca1f00aa5F1DFEC40b2Af74](https://multisig.harmony.one/#/safes/0xE3c985f5e317eFd4aca1f00aa5F1DFEC40b2Af74/)
* Polygon: [0x09dc95959978800E57464E962724a34Bb4Ac1253](https://gnosis-safe.io/app/matic:0x09dc95959978800E57464E962724a34Bb4Ac1253/)
* Metis: [0xFf9810A3dA8a554B84Ed79D67461eCA6Eb3fA9BD](https://metissafe.tech/metis-andromeda:0xFf9810A3dA8a554B84Ed79D67461eCA6Eb3fA9BD/)
* Moonriver: [0x1fdd00b45eba7f6d35b92803eaddd68f7cc4a193](https://multisig.moonbeam.network/mriver:0x1fdd00b45eba7f6d35b92803eaddd68f7cc4a193/)

## Treasury Multisigs

Beefy's treasury spending is secured by requiring multiple signatures from trusted (community) members. [As voted on by the DAO](https://vote-archive.beefy.finance/#/beefy/proposal/QmR5mzwjs46b3YRYWtc12CqqxF6r7VfpPd6ZfiRXnR69go), the following members represent the Treasury Council: Power, AllTrades, Pablo, mjoaris, TheBeefyCow, DefiDebauchery and YR2150.

* Fantom: [0xdFf234670038dEfB2115Cf103F86dA5fB7CfD2D2](https://safe.fantom.network/#/safes/0xdFf234670038dEfB2115Cf103F86dA5fB7CfD2D2/balances)[  ](https://safe.fantom.network/#/safes/0xdFf234670038dEfB2115Cf103F86dA5fB7CfD2D2/balances)
* BSC: [0x7C780b8A63eE9B7d0F985E8a922Be38a1F7B2141](https://gnosis-safe.io/app/bnb:0x7C780b8A63eE9B7d0F985E8a922Be38a1F7B2141/balances)
* HECO : [0xdbb72c8b7ebdd52a4813b9d262386dfdab69c9ba](https://www.xdao.app/128/dao/0xdbB72c8B7eBdD52A4813B9D262386dfDAB69c9bA)
* Polygon: [0xe37dD9A535c1D3c9fC33e3295B7e08bD1C42218D](https://gnosis-safe.io/app/matic:0xe37dD9A535c1D3c9fC33e3295B7e08bD1C42218D/balances)
* Arbitrum: [0x3f5eddad52C665A4AA011cd11A21E1d5107d7862](https://gnosis-safe.io/app/arb1:0x3f5eddad52C665A4AA011cd11A21E1d5107d7862/balances)
* Harmony: [0x523154a03180FD1CB26F39087441c9F91BcD0389](https://multisig.harmony.one/#/safes/0x523154a03180FD1CB26F39087441c9F91BcD0389/balances)
* Moonriver: [0x617f12E04097F16e73934e84f35175a1B8196551](https://multisig.moonbeam.network/mriver:0x617f12E04097F16e73934e84f35175a1B8196551/balances)
* Fuse: [0x1C124c2CaB83b3C3B5D0f0899CeeA5e06964599F](https://gnosis-safe.fuse.io/fuse:0x1C124c2CaB83b3C3B5D0f0899CeeA5e06964599F/balances)
* Avalanche: [0x26dE4EBffBE8d3d632A292c972E3594eFc2eCeEd](https://gnosis-safe.io/app/avax:0x26dE4EBffBE8d3d632A292c972E3594eFc2eCeEd/balances)
* Metis: [0x0f9602B7E7146a9BaE16dB948281BebDb7C2D095](https://metissafe.tech/metis-andromeda:0x0f9602B7E7146a9BaE16dB948281BebDb7C2D095/balances)
* Optimism: [0x4ABa01FB8E1f6BFE80c56Deb367f19F35Df0f4aE](https://gnosis-safe.io/app/oeth:0x4ABa01FB8E1f6BFE80c56Deb367f19F35Df0f4aE/home)
* Ethereum: [0xc9C61194682a3A5f56BF9Cd5B59EE63028aB6041](https://gnosis-safe.io/app/eth:0xc9C61194682a3A5f56BF9Cd5B59EE63028aB6041/home)


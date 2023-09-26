---
description: 'Last Update: September 2023'
---

# Treasury

At the heart of Beefy's operations is our Treasury, which is managed by our Core contributor team. As our $BIFI token is fully distributed, with no tokens reserved for later use, our entire operation is funded by our ongoing revenue-generating activities. To keep the lights on and our vaults autocompounding, Beefy relies on the constant vigilance of its treasury team to manage the use of our Treasury responsibly, and with the DAO's best interests at heart.

This page explains the history and structure of the Beefy Treasury, summarises our approach to treasury management, and provides the details you'll need to access our live treasury activities.

## History

Beefy's core product - our Beefy Vaults - are designed from the ground up to generate fees for the project (see [beefy-finance-fees-breakdown.md](../ecosystem/beefy-bulletins/beefy-finance-fees-breakdown.md "mention")) to sustain our activities. As such, we have always been a revenue-generating project, and have always had some level of treasury inflows and outflows.

Over time, our treasury activities have become increasingly sophisticated. Initially, the project's founders privately managed the inflows from the smart contract to cover their costs in operating and maintaining the protocol. The original [BeefyTreasury contract](https://bscscan.com/address/0x4a32de8c248533c28904b24b4cfcfe18e9f2ad01#code) was [deployed](https://bscscan.com/tx/0xccc2a94cde6aa10e3928a837b17cb7705f8ec3104afb66842627cc9cdaf4621c) on 6 November 2020. The Treasury contract was very basic in functionality, allowing the native chain token and ERC-20/BEP-20 tokens to be withdrawn by the owner, which was the [BeefyDeployer EOA](https://bscscan.com/address/0x565eb5e5b21f97ae9200d121e77d2760fff106cb).&#x20;

By March 2021, Beefy had expanded to include more contributors, and so the Core contributor team created the #💵-treasury channel in the [Beefy Discord](https://discord.gg/yq8wfHd) as a place for discussion of all treasury-related issues. Over the next few months, Beefy became increasingly multichain, and additional BeefyTreasury contracts were deployed on [Avalanche](https://snowtrace.io/address/0xa3e3af161943cfb3941b631676134bb048739727#code), [Polygon](https://polygonscan.com/address/0x09ef0e7b555599a9f810789fff68db8dbf4c51a0#code), [Fantom](https://ftmscan.com/address/0xe6cce165aa3e52b2cc55f17b1dbc6a8fe5d66610#code) together with some other early chains. However, the Core team recognised the limitation of the early Treasury's design, and a move MultiSig wallets was debated, despite MultiSig solutions not being available on all chains.&#x20;

By September 2021, the DAO had settled on moving to MultiSig wallets on BSC and Polygon (as the two chains with MultiSig solutions available at the time), and establishing the Treasury Council as the signers of the MultiSig. On 3 September 2021, a soft vote was concluded on Discord to appoint the new members of the Treasury Council. This was followed up by a [Snapshot Proposal](https://vote-archive.beefy.finance/#/beefy/proposal/QmafULDojJ4StzJtuwjBZutnUkzb9TUhTLCLZe5R7deWLo), which confirmed the initial 7 members. On 11 September, ownership of the original BeefyTreasury contract on BSC was [transferred](https://bscscan.com/tx/0x34a89b3cd5564fbd22672169b9cce43a538cf764cb73e1a28fe4db89241ae7ad) to the new MultiSig. Since then, the MultiSig system and Treasury Council has continued and expanded to each of Beefy's new chains.

Also in September 2021, Beefy's Core team began to implement bots in the #💵-treasury channel, initially displaying the value of the Treasury for the benefit of DAO members. By October 2022, this had evolved to include each new transactions live when posted from any of the Treasury's multisig wallets. Some of the key bot commands are:

* **Show Full Treasury:** `@Bitch I'm a Cow#9189 treasury`
* **Show Full Treasury on Specified Chain:** `@Bitch I'm a Cow#9189 treasury {blockchain}`
* **Show Current Cowllector Balances:** `@Bitch I'm a Cow#9189 cowllector balances`

## Treasury Council

As described above, the Treasury Council was formed in September 2021 as the team that should conduct and manage all Treasury transactions and related activities for Treasury management. The role of the Treasury Council has expanded gradually, to now include:

* Orchestrating, signing and executing all Treasury transactions (i.e. payments out of Treasury);
* Managing Treasury assets, such as creating and exiting protocol-owned liquidity and holding grants, pending rewards and other external assets;
* Monitoring and providing operating capital (e.g. gas) for Beefy's infrastructure, including our Cowllector, Fee Batch Harvester and contributor EOAs;
* Arranging for payment of key expenses, including contributor salaries, sponsorships, recurring hosting and service fees and reimbursement for contributor expenses; and
* Handling regular bribe payments to partner exchanges.

The Treasury Council has 8 members, and requires consensus from any 4 to sign off on any MultiSig transaction before it can be executed. Details of the current 8 members and their Treasury EOA wallets are:

* **Beef Nugget:** 0xd38d0dd50d03cea499df2b4c8d4b47458bee9358
* **ChiliConCarne:** 0x645c2c6105604bfce05c1aab2cb598af393553d5
* **DefiDebauchery:** 0x037465bF6a4A8D7F552AE18046478C6A727178F3
* **Moodini:** 0xdae7624267e4515f40266a38505f4f7e13dbf6c4
* **Red Bull:** 0x03e7302e3ecba4c1bd0e1841b55bf2c939e03fd3
* **Ser Loin:** 0xa2894cec4a49014b00e84e71861344fc794b8c27
* **TBC:** 0x428b2F01Bfb0917FE6FF463f37B0c47F1782B9Cd
* **YR2150:** 0xF24f555d6765D559BFF4C5557dD9024CBA10d30e

Any questions for the Treasury Council should be directed to the #💵-treasury channel on the [Beefy Discord](https://discord.gg/yq8wfHd). For security purposes, please do not directly message Council members instead, or your messages will be ignored and potentially blocked or reported.

## Treasury Infrastructure

Beefy's Treasury relies on a few core building blocks of infrastructure to facilitate the secure inflows and outflows of funds from Treasury. The core elements are:

* **Treasury Multisig** - multi-signature wallets controlled by the Treasury Council, used to hold all of the main assets of the treasury securely, and in a manner that can't be exploited by any single individual;&#x20;
* **Treasury Contributor Wallets** - externally-owned accounts (**EOA**s) controlled by different Beefy contributors, such as our Treasury Council members and other key DAO contributors. By using EOAs to interact with external protocols and contracts, we isolate the risk of hacks or exploits impacting the Beefy Treasury, by isolating it from externals and giving no or very limited exteranl approvals;
* **Cowllector** - the Beefy Cowllector is a bot created and maintained by the Beefy Core which seeks to harvest Beefy vaults regularly (at least every 24 hours for all chains but Ethereum) and wherever a profitable opportunity presents itself. As the harvest caller claims a small fee as a proportion of the harvest, the Cowllector analyses the size of the potential reward versus the cost of harvesting, and makes automatic calls where appropriate;
* [revenue-bridge.md](../ecosystem/protocol/revenue-bridge.md "mention") - the Beefy Revenue Bridge is a set of contracts on each chain which facilitate the bridging of Beefy's fees back to Ethereum. The bridge contract performs a few functions to allocate and prepare them for bridging. The bridge itself contains multiple different bridging services, and will use the preferred method which has been specified to the contract. The bridge can either bridge directly to Ethereum, or back via any number of intermediate chains; and
* [fee-batch.md](../ecosystem/protocol/fee-batch.md "mention") - the Beefy Fee Batch is a set of contracts on each chain, which aggregate Beefy's fees from across the protocol into one place, to be able to efficiently distribute them to stakeholders. On Ethereum, the fees arrive to the Fee Batch, which aggregates all of the protocol's fees. Once a sufficient amount of tokens are batched token, the Fee Batch distributes them both to Treasury and - after swapping back to native $ETH - to the [governance-pools.md](../ecosystem/protocol/governance-pools.md "mention").

The treasury multisigs can be found at the following addresses for the following chains:

* Arbitrum: [0x3f5eddad52C665A4AA011cd11A21E1d5107d7862](https://gnosis-safe.io/app/arb1:0x3f5eddad52C665A4AA011cd11A21E1d5107d7862/balances)
* Avalanche: [0x26dE4EBffBE8d3d632A292c972E3594eFc2eCeEd](https://gnosis-safe.io/app/avax:0x26dE4EBffBE8d3d632A292c972E3594eFc2eCeEd/balances)
* Base: [0x1A07DceEfeEbBA3D1873e2B92BeF190d2f11C3cB](https://app.safe.global/home?safe=base:0x1A07DceEfeEbBA3D1873e2B92BeF190d2f11C3cB)
* BSC: [0x7C780b8A63eE9B7d0F985E8a922Be38a1F7B2141](https://gnosis-safe.io/app/bnb:0x7C780b8A63eE9B7d0F985E8a922Be38a1F7B2141/balances)
* Canto: [0xF09d213EE8a8B159C884b276b86E08E26B3bfF75](https://safe.neobase.one/canto:0xF09d213EE8a8B159C884b276b86E08E26B3bfF75/home)
* Cronos: [0xa9721Ae5042482D7a884A2138f580459B680920f](https://cronos-safe.org/cro:0xa9721Ae5042482D7a884A2138f580459B680920f/home)
* Ethereum: [0xc9C61194682a3A5f56BF9Cd5B59EE63028aB6041](https://gnosis-safe.io/app/eth:0xc9C61194682a3A5f56BF9Cd5B59EE63028aB6041/home)
* Fantom: [0xdFf234670038dEfB2115Cf103F86dA5fB7CfD2D2](https://safe.fantom.network/#/safes/0xdFf234670038dEfB2115Cf103F86dA5fB7CfD2D2/balances)[  ](https://safe.fantom.network/#/safes/0xdFf234670038dEfB2115Cf103F86dA5fB7CfD2D2/balances)
* Fuse: [0x1C124c2CaB83b3C3B5D0f0899CeeA5e06964599F](https://gnosis-safe.fuse.io/fuse:0x1C124c2CaB83b3C3B5D0f0899CeeA5e06964599F/balances)
* Kava: [0x07F29FE11FbC17876D9376E3CD6F2112e81feA6F](https://app.oryy.io/kava:0x07F29FE11FbC17876D9376E3CD6F2112e81feA6F/home)
* Metis: [0x0f9602B7E7146a9BaE16dB948281BebDb7C2D095](https://metissafe.tech/metis-andromeda:0x0f9602B7E7146a9BaE16dB948281BebDb7C2D095/balances)
* Moonbeam: [0x3E7F60B442CEAE0FE5e48e07EB85Cfb1Ed60e81A](https://multisig.moonbeam.network/mbeam:0x3E7F60B442CEAE0FE5e48e07EB85Cfb1Ed60e81A/home)
* Moonriver: [0x617f12E04097F16e73934e84f35175a1B8196551](https://multisig.moonbeam.network/mriver:0x617f12E04097F16e73934e84f35175a1B8196551/balances)
* Optimism: [0x4ABa01FB8E1f6BFE80c56Deb367f19F35Df0f4aE](https://gnosis-safe.io/app/oeth:0x4ABa01FB8E1f6BFE80c56Deb367f19F35Df0f4aE/home)
* Polygon PoS: [0xe37dD9A535c1D3c9fC33e3295B7e08bD1C42218D](https://gnosis-safe.io/app/matic:0xe37dD9A535c1D3c9fC33e3295B7e08bD1C42218D/balances)
* Polygon zkEVM: [0x6fdfb18D09d5fa9a76ac76cb6Cdc53c8F23C3B29](https://zksafe.quickswap.exchange/home?safe=zkEVM:0x6fdfb18D09d5fa9a76ac76cb6Cdc53c8F23C3B29)
* zkSync: [0x9F9FE15FDa14eAA2d878Ed667C805A7CC13c2560](https://zksafe.protofire.io/home?safe=zksync:0x9F9FE15FDa14eAA2d878Ed667C805A7CC13c2560)

Older retired treasuries (either on retired chains or replaced by new treasuries) include:

* Arbitrum: [0xc3a4fdcba79DB04b4C3e352b1C467B3Ba909D84A](https://arbiscan.io/address/0xc3a4fdcba79db04b4c3e352b1c467b3ba909d84a)
* Aurora: [0x088C70Ddff3a3774825dd5e5EaDB356404248d83](https://app.safe.global/home?safe=aurora:0x088C70Ddff3a3774825dd5e5EaDB356404248d83)
* Avalanche: [0xA3e3Af161943CfB3941B631676134bb048739727](https://snowtrace.io/address/0xa3e3af161943cfb3941b631676134bb048739727)
* BSC: [0x4A32De8c248533C28904b24B4cFCFE18E9F2ad01](https://bscscan.com/address/0x4a32de8c248533c28904b24b4cfcfe18e9f2ad01)
* Celo: [0xca807d809f9639cefb3d31a7951cec3ab405a2fd](https://www.xdao.app/42220/dao/0xCA807D809f9639CEfb3d31a7951Cec3ab405a2fd)
* Cronos: [0x3f385082Ee3dFf58ca0a6a7fe44Ea0B5d6b4168E](https://cronoscan.com/address/0x3f385082ee3dff58ca0a6a7fe44ea0b5d6b4168e)
* Emerald: [0x8fd0869271d26e6653f5d5650685630f75b6aedf](https://www.xdao.app/42262/dao/0x8FD0869271d26E6653f5d5650685630F75b6AEDf)
* Fantom: [0xe6CcE165Aa3e52B2cC55F17b1dBC6A8fe5D66610](https://ftmscan.com/address/0xe6cce165aa3e52b2cc55f17b1dbc6a8fe5d66610)
* Fuse: [0x922f8807E781739DDefEe51df990457B522cBCf5](https://explorer.fuse.io/address/0x922f8807E781739DDefEe51df990457B522cBCf5)
* Harmony: [0x523154a03180FD1CB26F39087441c9F91BcD0389](https://multisig.harmony.one/#/safes/0x523154a03180FD1CB26F39087441c9F91BcD0389/balances)
* HECO : [0xdbb72c8b7ebdd52a4813b9d262386dfdab69c9ba](https://www.xdao.app/128/dao/0xdbB72c8B7eBdD52A4813B9D262386dfDAB69c9bA)
* Moonriver: [0xB6Fb58eea08b5539f371A744bb9Ef86283F1B3c2](https://moonriver.moonscan.io/address/0xb6fb58eea08b5539f371a744bb9ef86283f1b3c2)
* Polygon PoS: [0x09EF0e7b555599A9F810789FfF68Db8DBF4c51a0](https://polygonscan.com/address/0x09ef0e7b555599a9f810789fff68db8dbf4c51a0)
* zkSync: [0x8cE3fE8b9Ec8Ab80967c9771909385E3e3A272fA](https://explorer.zksync.io/address/0x8ce3fe8b9ec8ab80967c9771909385e3e3a272fa)

## Treasury Management

Management of Beefy's Treasury has also evolved over time, to reflect the changing needs of the protocol and the DAO. Operating on so many chains, each with their own sets of vaults, infrastructure and MultiSig wallets makes it a complicated process to actively manage the Treasury. Instead, a number of overarching principles have emerged to guide current best practices.

First and foremost, Beefy's contributor team have opted to operate the Treasury on each major chain primarily in stablecoins, to mitigate the downside risk of holding volatile assets. This allows Beefy to make clear and deliberate decisions about how to use its funds, free from the risks of current market condition. As such, the Fee Batcher on each major chain swaps all Beefy's vault fees into a designated currency for that chain, as detailed in [#inflow-currencies](treasury.md#inflow-currencies "mention") below.

Secondly, it was decided that investing a portion of treasury assets in Beefy Vaults to generate passive income would be a sensible and smart use of funds. Generally speaking, only a small proportion of the Treasury held on our major chains is ever invested in Beefy Vaults, and they are always allocated to stablecoin-only vaults. Though returns on invested funds are generally relatively small, this mechanism does help to mitigate the inflationary nature of stablecoin valuations.

Finally, to facilitate liquidity for our tokens across the different chains, Beefy also invests in and maintains liquidity positions in our tokens, including both our [bifi-token](../ecosystem/bifi-token/ "mention"), and our [beefy-escrowed-tokens](../beefy-products/beefy-escrowed-tokens/ "mention"). Our $BIFI token is typically paired with native or gas tokens on the relevant chain, to provide the easiest route into the token for new arrivals on the chain. Once the bridged $BIFI token contract is deployed on a new chain, the contract is connected to the Beefy Bridge and our partners at Multichain, so that more $BIFI can be bridged onto the chain and so that an initial LP can be created.

Live summary details of the current state of the Beefy Treasury, including all liquid, staked/invested and locked tokens and liquidity positions, are available in the [Treasury Dashboard ](https://app.beefy.finance/treasury)page of the Beefy App.

<figure><img src="../.gitbook/assets/Treasury Dashboard.png" alt=""><figcaption><p>The Beefy Treasury Dashboard was introduced in January 2023 to provide immediate summary insights into the current state of the Beefy Treasury.</p></figcaption></figure>

## Inflow Currencies

As described above in [#treasury-management](treasury.md#treasury-management "mention"), inflows on our key blockchains are swapped into stablecoins for treasury management purposes, with each chain's [revenue-bridge.md](../ecosystem/protocol/revenue-bridge.md "mention") contract adopting a key stablecoin for its operations. The following chains have the following nominated currencies:

* Arbitrum: USDC
* Avalanche: USDT
* Base: WETH
* BSC: BUSD
* Canto: USDC
* Cronos: USDC
* Ethereum: USDC
* Ethereum Validator: WETH (retained in validator)
* Fantom: USDC
* Fantom Validator: WBTC (gradually bridged to Ethereum)
* Fuse: WFUSE
* Fuse Validator: Fuse (retained in validator)
* Kava: USDC
* Metis: USDC
* Moonbeam: MAI
* Moonriver: USDC
* Optimism: USDC
* Polygon PoS: USDC
* Polygon zkEVM: WETH
* zkSync: WETH

Volumes and liquidity on Aurora, Celo, Emerald, Harmony and HECO are all currently too small to warrant stablecoin management, so vault fee inflows are typically swapped into the relevant native chain token instead.

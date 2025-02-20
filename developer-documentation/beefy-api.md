---
description: 'Last Update: August 2023'
---

# Beefy API

This page provides further details about the functionality and operation of Beefy's REST API, which powers our web application, dashboard and pages on third party sites.&#x20;

You can access the API at [https://api.beefy.finance/](https://api.beefy.finance/), and the public repository is available on [the Beefy GitHub](https://github.com/beefyfinance/beefy-api). The API is maintained under the MIT license, with further details available on the [GitHub repo](https://github.com/beefyfinance/beefy-api/blob/master/LICENSE).

## Endpoints

Our API offers a range of public endpoints covering the full selection of data required for our web app, backend and dashboard, as well as some third party services.&#x20;

### Beefy Vault Endpoints

Endpoints developed for use by [the Beefy Application](https://app.beefy.finance/) to display vaults' live characteristics and performance to our users.&#x20;

<details>

<summary>GET /vaults </summary>

Provides live information about each Beefy vault, including retired (eol) vaults.

The information includes fields for the relevant vault's name/ID, chain, token, underlying assets, related contracts and current status. It also includes the "risks" field, which lists the vault's features taken from the matrix of risk factors used to calculate a vault's safety score.

{% code overflow="wrap" %}
```json
// Sample response for the /vaults endpoint (e.g. Polygon aTriCrypto3 vault)

{
  "id": "curve-poly-atricrypto3",
  "name": "aTriCrypto3",
  "token": "crvUSDBTCETH3",
  "tokenAddress": "0xdAD97F7713Ae9437fa9249920eC8507e5FbB23d3",
  "tokenDecimals": 18,
  "tokenProviderId": "curve",
  "earnedToken": "mooCurveATriCrypto3",
  "earnedTokenAddress": "0x5A0801BAd20B6c62d86C566ca90688A6b9ea1d3f",
  "earnContractAddress": "0x5A0801BAd20B6c62d86C566ca90688A6b9ea1d3f",
  "oracle": "lps",
  "oracleId": "curve-poly-atricrypto3",
  "status": "active",
  "platformId": "curve",
  "assets": [
    "DAI",
    "USDC",
    "USDT",
    "WBTC",
    "ETH"
  ],
  "strategyTypeId": "multi-lp",
  "risks": [
    "COMPLEXITY_LOW",
    "BATTLE_TESTED",
    "IL_LOW",
    "MCAP_LARGE",
    "PLATFORM_ESTABLISHED",
    "AUDIT",
    "CONTRACTS_VERIFIED",
    "OVER_COLLAT_ALGO_STABLECOIN"
  ],
  "addLiquidityUrl": "https://polygon.curve.fi/atricrypto3/deposit",
  "network": "polygon",
  "createdAt": 1652662923,
  "chain": "polygon",
  "strategy": "0x41D7529b4C9245a50ca6A169d39719DFF117f6CA",
  "lastHarvest": 1664612723,
  "pricePerFullShare": "1178961451902175914"
},
```
{% endcode %}

#### Field Notes:

* **id** - the unique identifying string assigned to each vault, including separate versions of the same vault.
* **tokenAddress** - the contract address for the main deposit asset, typically an LP token.
* **earnedTokenAddress** - the contract of the token which is earned by the strategy used by the vault. For most Beefy vaults, this is the same as the vault contract, because the strategy is autocompounding. For earnings pool vaults (which don't autocompound), this will be the native token of the chain or protocol that the vault relates to.
* **earnContractAddress** - the address of the Beefy vault contract which handles deposits and withdrawals and issues the mooVault token to users.
* **status** - shows whether a vault is live ("active") or retired ("eol").
* **assets** - the underlying assets at the base of the relevant vault's stack (typically the assets included in the LP that the vault is built on).
* **strategyTypeID** - indicates what type of strategy is being utilised by the vault (e.g. "single" asset, "lp", "multi-lp", etc).
* **risks** - a list of the vault's applicable features taken from the matrix of factors used to calculate a vault's safety score.
* **network** - the relevant blockchain that the vault resides on.
* **createdAt** - the block of the relevant blockchain where the vault was created.
* **strategy** - the address of the strategy contract currently in use by the vault.
* **lastHarvest** - the block of the relevant blockchain where the vault was last harvested - i.e. where profits were collected from the strategy (and autocompounded, if applicable).
* **pricePerFullShare** - the current average price (denominated in the deposit asset, e.g. the underlying LP token) for each whole share of the vault's total issued share capital, reflecting the total value invested into the vault over its life divided by the number of shares of the vault issued.

</details>

<details>

<summary>GET /apy</summary>

Provides the current and live annual percentage yield of each Beefy vault.

{% code overflow="wrap" %}
```json
// Sample response for the /apy endpoint

{
  ...
  "balancer-usdc-link-eth-bal-aave": 0.03705509745347668,
  "balancer-matic-usdc-eth-bal": 0.052770609595836904,
  "baby-wbnb-busd": 0.1612595689122669,
  "baby-usdc-wbnb": 0.16031283171896837,
  "balancer-vst-dai-usdt-usdc": 0.029489187277781825,
  "balancer-bal-eth": 0.024578537703132453,
  "curve-matic-stmatic": 0.08866966650936048,
  "sushi-poly-weth-sx": 0.7135292677781775,
  "sushi-poly-bct-klima": 0.0007036903322936716,
}
```
{% endcode %}

**Field Notes:**

* **Vault APY** - Each field reflects the unique id string of a vault, and returns a value which represents the live APY as a decimal. For instance, "0.037" represents 3.7% APY.

</details>

<details>

<summary>GET /apy/breakdown</summary>

Provides more detailed information relating to the yield of each Beefy vault, which is required to assess the expected APY based on factors like the APR, rate of compounding and applicable fees.

{% code overflow="wrap" %}
```json
// Sample response from the /apy/breakdown endpoint (e.g. Polygon Cometh UST-ETH LP)

{
  "bifi-maxi": {
    "totalApy": 0.07598675804818633
  },
  "cometh-must-eth": {
    "vaultApr": 1.186973388240745,
    "compoundingsPerYear": 2190,
    "beefyPerformanceFee": 0.045,
    "vaultApy": 2.1057844292858614,
    "lpFee": 0.005,
    "tradingApr": 0.22324214039526927,
    "totalApy": 2.8825691266420788
  }
}
```
{% endcode %}

#### Field Notes

* **vaultApr** - the annual percentage return of the vault, calculated from the expected yearly rewards of the vault, denominated in $USD, divided by the total amount invested in the vault, also in $USD.
* **compoundingsPerYear** - the estimated current number of compounding events ("harvest" calls) per year.
* **beefyPerformanceFee** - the flat Beefy performance fee included in the calculation.&#x20;
* **vaultApy** - the annual percentage yield (APY) of the vault, calculated by compounding the vaultApr detailed above, using the compoundingsPerYear figure, and adjusting for the beefyPerformanceFee.
* **lpFee** - the Liquidity Provider (LP) fee charged for each trade.
* **tradingApr** - the annual interest received from trading fees, without applying or account for any compounding effect.
* **totalApy** - the known total APY, calculated as totalApy = (1 + vaultApy) \* (1 + tradingApr) - 1.

</details>

<details>

<summary>GET /tvl</summary>

Provides the current and live total value locked of each Beefy vault, which is the sum of the current market capitalisation of all of the assets currently held by the relevant vault, denominated in $USD.

```json
// Sample response from the /tvl endpoint

{
    ...
    "optimism-bifi-maxi": 37679.65,
    "velodrome-wsteth-weth": 295597.74,
    "beets-lido-shuffle": 101185.39,
    "beets-yellow-submarine": 5828.15,
    "beets-its-mai-life": 178994.42,
    "velodrome-usdc-mim": 488943.72,
    "velodrome-weth-bifi": 133635.5,
    ...
}
```

</details>

<details>

<summary>GET /fees</summary>

Provides a detailed breakdown of the current fee structure for each Beefy vault.

```json
// Sample response from the /fees endpoint (e.g. Celo BIFI Maxi vault)

{
  "celo-bifi-maxi": {
    "performance": {
      "total": 0.0005,
      "strategist": 0,
      "call": 0.0005,
      "treasury": 0,
      "stakers": 0
    },
    "withdraw": 0,
    "lastUpdated": 1665603844026
  },
  ...
}
```

**Field Notes:**

* **performance** - a list of the fee settings which together constitute the performance fee charged on every compounding event ("harvest") for each vault.
* **total** - the total performance fee charged, being the sum of the other facts in the "performance" list.
* **strategist** - the fee payable to the strategist that deploys the vault, as a form of incentive to encourage community contributions.
* **call** - the fee payable to the caller of the harvest function which gives rise to the compounding of the vault.
* **treasury** - the fee payable to the Beefy treasury to support the protocol.
* **stakers** - the fee payable to holders and stakers of the BIFI token, which is pay out to our BIFI Earnings Pool vaults or to buy back BIFI tokens for our BIFI Maxi vaults.
* **withdraw** - the fee charged on the value of your deposit upon withdrawal from the vault, to protect against attacks against and abuse of our vaults.
* **lastUpdated** - the block of the relevant blockchain for the vault from which the data in the API was last updated.

</details>

### External Asset Endpoints

Endpoints developed for use by [the Beefy Application](https://app.beefy.finance/) to display information about the assets underlying our Beefy vaults to our users.

<details>

<summary>GET /lps</summary>

Provides the current live prices of underlying liquidity pools used by each Beefy vaults.

{% code overflow="wrap" %}
```json
// Sample respones from the /lps endpoint

{
  ...
  "crow-crow-bnb": 17.913780228255288,
  "crow-crow-busd": 1.1650429579716788,
  "czf-czf-bnb": 0.0025782563297118174,
  "czf-czf-busd": 0.00013385738163789002,
  "dark-dark-cro": 0.07756021296662909,
  "dark-sky-cro": 1.6261613868777973,
  "dfx-nzds-usdc": 0.5422606115320028,
  "dfyn-aave-dfyn": 2.878265077862883,
  "dfyn-bifi-dfyn": 6.083434553784047,
  ...
}
```
{% endcode %}

**Field Notes:**

* **LP Price** - each field reflects the unique oracleId string of an LP vault, and returns a value which represents the live price in USD. For instance, "1.165" represents a price of $1.17.

</details>

<details>

<summary>GET /lps/breakdown</summary>

Provides more detailed information relating to the liquidity pool used by each Beefy vault.

{% code overflow="wrap" %}
```json
// Sample response from the /lps/breakdown endpoint (eg. 2omb 2omb-2share LP)

{
  "2omb-2omb-2share": {
    "price": 0.29050984564246707,
    "tokens": [
      "0x7a6e4E3CC2ac9924605DCa4bA31d1831c84b44aE",
      "0xc54A1684fD1bef1f077a336E6be4Bd9a3096a6Ca"
    ],
    "balances": [
      "114463.728388652710537014",
      "391.331589320557497638"
    ],
    "totalSupply": "5873.360029904692639438"
  },
```
{% endcode %}

**Field Notes:**

* **price** - the current and live price per full share of the LP token, denominated in $USD.
* **tokens** - a list of the contract addresses of each of the underlying assets/tokens included in the LP.
* **balances** - a list of the current balances of each of the tokens in the vault, as listed in the previous field, denominated in the underlying token.
* **totalSupply** - the current and live number of LP tokens issued.&#x20;

</details>

<details>

<summary>GET /tokens</summary>

Provides information on all of the tokens utilised by Beefy, including individual assets and currencies, staked assets and LPs, sorted by the blockchain each is deployed on.

```
// Sample response for /tokens endpoint (e.g. polygon spUSDC LP token)

{
  "polygon": {
    "spUSDC": {
      "name": "Stargate USD Coin LP",
      "symbol": "spUSDC",
      "address": "0x1205f31718499dBf1fCa446663B532Ef87481fe1",
      "decimals": 6
    },
    ...
}
```

**Field Notes:**

* **name** - a string showing the full name of the token associated with the relevant ID.
* **symbol** - a string showing the symbol assigned to the token by the issuer.
* **address** - the contract address for the relevant token.
* **decimals** - the number of decimal permitted for the token by the issuer, representing how divisible it is on chain.

**GET /tokens/{blockchain}**

For further specificity, you can add a {blockchain} parameter to the /tokens endpoint to return only tokens on a given blockchain (e.g. /tokens/polygon returns only tokens issued on the Polygon blockchain).

</details>

### Other Beefy App Endpoints

Endpoints developed for use by [the Beefy Application](https://app.beefy.finance/) to display other information not relating to individual vaults.

<details>

<summary>GET /config</summary>

Provides information on the addresses of the current configuration of wallets used to operate each blockchain used by the [the Beefy Application](https://app.beefy.finance/).

<pre><code>// Sample response from /config endpoint (e.g. Polygon blockchain)
<strong>
</strong><strong>{
</strong>  "polygon": {
    "devMultisig": "0x09dc95959978800E57464E962724a34Bb4Ac1253",
    "treasuryMultisig": "0xe37dD9A535c1D3c9fC33e3295B7e08bD1C42218D",
    "strategyOwner": "0x6fd13191539e0e13B381e1a3770F28D96705ce91",
    "vaultOwner": "0x94A9D4d38385C7bD5715A2068D69B87FF81F4BF3",
    "keeper": "0x4fED5491693007f0CD49f4614FFC38Ab6A04B619",
    "treasurer": "0xe37dD9A535c1D3c9fC33e3295B7e08bD1C42218D",
    "launchpoolOwner": "0x09dc95959978800E57464E962724a34Bb4Ac1253",
    "rewardPool": "0xDeB0a777ba6f59C78c654B8c92F80238c8002DD2",
    "treasury": "0x09EF0e7b555599A9F810789FfF68Db8DBF4c51a0",
    "beefyFeeRecipient": "0x7313533ed72D2678bFD9393480D0A30f9AC45c1f",
    "bifiMaxiStrategy": "0xD126BA764D2fA052Fc14Ae012Aef590Bc6aE0C4f",
    "voter": "0x5e1caC103F943Cd84A1E92dAde4145664ebf692A",
    "beefyFeeConfig": "0x8E98004FE65A2eAdA63AD1DE0F5ff76d845f14E7"
  },
...
</code></pre>

**Field Notes:**

* **devMultisig** - the address of the Beefy developer multisignature wallet used to manage development updates on the chain.
* **treasuryMultisig** - the address of the Beefy treasury multisignature wallet used to manage Beefy's core treasury of funds on the chain.
* **strategyOwner** - the address of the standard Beefy wallet that acts as owner of strategy contracts on the chain.
* **vaultOwner** - the address of the standard Beefy wallet that acts as owner of vault contracts on the chain.
* **keeper** - the address of the standard Beefy wallet that acts as keeper of vault contracts on the chain. This includes managing the whitelist of strategies used by the vault, and pausing or panicking the vault if required.
* **treasurer** - the address of the standard Beefy wallet that acts as the treasurer on the chain. This includes managing payments from the treasury for various reasons, and is often the same wallet as the treasuryMultisig.
* **launchpoolOwner** - the address of the standard Beefy wallet that acts as owner of the launchpool/boost contracts deployed on the chain. This is often the same wallet as the devMultisig.
* **rewardPool** - the address of the standard Beefy wallet that holds the rewards allocated for boosts on the chain.
* **treasury** - the address of the standard Beefy wallet that acts as the treasury on the chain, and is managed by the treasurer and treasuryMultisig.
* **beefyFeeRecipient** - the address of the standard Beefy wallet that acts receives performance fees charged on harvests from all Beefy vaults on the chain.
* **bifiMaxiStrategy** - the address of the strategy attached to the native $BIFI Maxi vault on the chain.&#x20;
* **voter** - the address of the standard Beefy wallet that is used to direct Beefy's voting power on various third party protocols.
* **beefyFeeConfig** - address of the upgradeable proxy contract used to set the configuration of performance fees charged for vaults on the chain.

**GET /config/{blockchain}**

For further specificity, you can add a {blockchain} parameter to the /config endpoint to return the configuration details of a given blockchain (e.g. /config/polygon returns only the details for the Polygon blockchain).

</details>

<details>

<summary>GET /boosts</summary>

Provides information on all [Launchpool Boosts](../beefy-products/boost.md) hosted by Beefy on the application, including live and historic boosts.

```
// Sample response from /boosts endpoint (e.g. Optimism BIFI-WETH LP token)

{
  "id": "moo_velodrome-weth-bifi-beefy",
  "poolId": "velodrome-weth-bifi",
  "name": "Beefy",
  "assets": [
    "BIFI",
    "ETH"
  ],
  "tokenAddress": "0x3532b6f723948eF39d5DCf44C16855239aF81082",
  "earnedToken": "OP",
  "earnedTokenDecimals": 18,
  "earnedTokenAddress": "0x4200000000000000000000000000000000000042",
  "earnContractAddress": "0x8F755873546F4D0EDf7d41fF8604C8A632113eB7",
  "earnedOracle": "tokens",
  "earnedOracleId": "OP",
  "partnership": true,
  "status": "active",
  "isMooStaked": true,
  "partners": [
    "beefy"
  ],
  "chain": "optimism",
  "periodFinish": 1667843632
},
...
```

**Field Notes:**

* **id** - the unique identifying string assigned to each vault, including separate versions of the same vault.
* **poolId** - the unique identifying string assigned to each LP that Beefy has vaulted, including separate versions of the same LP.
* **name** - the full name of the partner(s) which have funded the boost.
* **assets** - a list of the underlying assets used for the vault or any underlying LP.&#x20;
* **tokenAddress** - the address of the Beefy vault contract which handles deposits and withdrawals and issues the mooVault token to users.
* **earnedToken** - the name of the boost reward token earned by boost participants.
* **earnedTokenDecimals** - the number of decimal places assigned and used for the earnedToken from its creation.
* **earnTokenAddress** - the contract address of the earnedToken.
* **earnContractAddress** - the contract address of the boost contract, which holds the assigned boost rewards and distributes them to boost participants.
* **isMooStaked** - whether the boost requires users to stake their mooTokens in a further contract with Beefy to receive the boost.
* **partners** - shorthand label for the partner(s) which have funded the boost.
* **periodFinish** - the block of the hosted blockchain where the boost ends.

**GET /boosts/{blockchain}**

For further specificity, you can add a {blockchain} parameter to the /boosts endpoint to return only boosts on a given blockchain (e.g. /boosts/polygon returns only boosts hosted on the Polygon blockchain).

</details>

<details>

<summary>GET /bifibuyback</summary>

Provides details of the daily amount of BIFI buyback carried out on each blockchain.

{% code overflow="wrap" %}
```json
// Sample response from the /bifibuyback endpoint (e.g. BSC data)

{
  "bsc": {
    "buybackTokenAmount": "0.377849674473987141",
    "buybackUsdAmount": "121.1485184178464957989921757592912"
  },
  ...
}
```
{% endcode %}

**Field Notes:**

* **buybackTokenAmount** - shows the current daily amount of $BIFI tokens bought back by the protocol on the relevant chain.
* **buybackUsdAmount** - shows the current value of the above in USD.

</details>

### Dashboard Endpoints

Endpoints developed for [the Beefy Dashboard](https://dashboard.beefy.finance/) to display overarching information about the protocol.

{% hint style="info" %}
Please note that the Dashboard site and the /earnings endpoint are both no longer actively maintained by Beefy. Though the Dashboard site remains live, it does not reflect every vault that has been implemented and every chain that Beefy has deployed to.
{% endhint %}

### Databarn Endpoints

Endpoints related to databarn, our historical data indexer. These endpoints are rate limited to maximum 5 requests per seconds. You may also want to try the [interactive swagger ui](https://databarn.beefy.com/api/v1/documentation) for these endpoints.

{% swagger src="../.gitbook/assets/json.json" path="/api/v1/beefy/timeline" method="get" %}
[json.json](../.gitbook/assets/json.json)
{% endswagger %}

{% swagger src="../.gitbook/assets/json.json" path="/api/v1/beefy/product/{chain}" method="get" %}
[json.json](../.gitbook/assets/json.json)
{% endswagger %}

{% swagger src="../.gitbook/assets/json.json" path="/api/v1/beefy/product/{chain}/{contract_address}" method="get" %}
[json.json](../.gitbook/assets/json.json)
{% endswagger %}

{% swagger src="../.gitbook/assets/json.json" path="/api/v1/beefy/product/{chain}/{contract_address}/tvl" method="get" %}
[json.json](../.gitbook/assets/json.json)
{% endswagger %}

{% swagger src="../.gitbook/assets/json.json" path="/api/v1/price/" method="get" %}
[json.json](../.gitbook/assets/json.json)
{% endswagger %}

{% swagger src="../.gitbook/assets/json.json" path="/api/v1/price/raw" method="get" %}
[json.json](../.gitbook/assets/json.json)
{% endswagger %}

### Third Party Endpoints

Endpoints required or utilised by third party platforms to display information about Beefy or its products on their sites.

<details>

<summary>GET /cmc</summary>

Provides information required by [CoinMarketCap](https://coinmarketcap.com/) in order to display Beefy vaults in their yield farming section.

{% code overflow="wrap" %}
```json
// Sample response for the /cmc endpoint

{
  "provider": "Beefy",
  "provider_logo": "https://beefy.finance/img/beefy.svg",
  "links": [
    {
      "title": "Twitter",
      "link": "https://x.com/beefyfinance"
    },
    {
      "title": "Telegram",
      "link": "https://t.me/beefyfinance"
    },
    {
      "title": "Discord",
      "link": "https://discord.gg/yq8wfHd"
    },
    {
      "title": "Medium",
      "link": "https://medium.com/beefyfinance"
    },
    {
      "title": "Github",
      "link": "https://github.com/beefyfinance"
    }
  ],
  "pools": [
    {
      "name": "BIFI Maxi",
      "pair": "BIFI",
      "pairLink": "https://app.beefy.finance/",
      "logo": "https://beefy.finance/vaults/bifi/BIFI.png",
      "poolRewards": [
        "BIFI"
      ],
      "apyId": "bifi-maxi",
      "contract": "0xf7069e41C57EcC5F122093811d8c75bdB5f7c14e",
      "oracle": "tokens",
      "oracleId": "BIFI"
    },
    ...
  ]
}
```
{% endcode %}

</details>

<details>

<summary>GET /supply</summary>

Provides information required by [Coingecko](https://coingecko.com/) in order to display BIFI's total supply and circulating supply on its site.

{% code overflow="wrap" %}
```json
// Sample response for the /supply endpoint

{
  "total": 80000,
  "circulating": 80000
}
```
{% endcode %}

</details>

## Subgraph

Please note that Beefy does not currently operate or maintain any subgraphs for our protocol.&#x20;

Our friends at Messari have developed a subgraph for our presence on BSC chain, which is available at [https://api.thegraph.com/subgraphs/name/messari/beefy-finance-bsc](https://api.thegraph.com/subgraphs/name/messari/beefy-finance-bsc), and on The Graph's [website](https://thegraph.com/hosted-service/subgraph/messari/beefy-finance-bsc) (ID: QmfEtMEgjik9FSZdqAmp2DkNFG4M9TK4Go8uyCUj8EVxY6). Beefy has had no role in the development or maintenance of this subgraph. Please direct any questions or requests for assistance in relation to this subgraph directly to Messari.

## Other Data

For any readers seeking further information about Beefy and our protocol's performance, please head to the #📊-beefy-data channel in our [Discord server](https://discord.gg/yq8wfHd). We'll be happy to answer any questions you may have there and you're welcome to inspect the history of our discussions in that channel for further background into our data work.&#x20;

You'll also find in that channel a collection of weekly reports on the breakdown of our $BIFI token across our different chains and vaults, which are lovingly prepared by core contributor EPETE.

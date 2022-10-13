---
description: 'Last Update: October 2022'
---

# Beefy API

This page provides further details about the functionality and operation of Beefy's REST API, which powers our web application, dashboard and pages on third party sites.&#x20;

You can access the API at [https://api.beefy.finance/](https://api.beefy.finance/), and the public repository is available on [the Beefy GitHub](https://github.com/beefyfinance/beefy-api). The API is maintained under the MIT license, with further details available on the [GitHub repo](https://github.com/beefyfinance/beefy-api/blob/master/LICENSE).

## Endpoints

Our API offers a range of public endpoints covering the full selection of data required for our web app, backend and dashboard, as well as some third party services.&#x20;

### Beefy Vault Endpoints

Endpoints developed for use by [the Beefy Application](https://app.beefy.finance/) to display vaults' live characteristics and performance to our users.

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
* **earnContractAddress** - the Beefy vault contract which handles deposits and withdrawals and issues the mooVault token to users.
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
* **totalApy** - the known total APY, calculated as totalApy = (1 + vaultApr) \* (1 + (compounded tradingApr)) - 1.

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

### Dashboard Endpoints

Endpoints developed for [the Beefy Dashboard](https://dashboard.beefy.finance/) to display overarching information about the protocol.

{% hint style="info" %}
Please note that the Dashboard site and the /earnings endpoint are both no longer actively maintained by Beefy. Though the Dashboard site remains live, it does not reflect every vault that has been implemented and every chain that Beefy has deployed to.
{% endhint %}

<details>

<summary>GET /holders</summary>

Provides the specific number of current holders of the $BIFI token.

```json
// Sample respones from the /holders endpoint

{
  "holderCount": 36882
}
```

</details>

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
      "link": "https://twitter.com/beefyfinance"
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

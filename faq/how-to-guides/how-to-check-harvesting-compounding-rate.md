---
description: >-
  In this guide you will find the required steps to check on your vault's harvesting and compounding rate.
---

# How to check your vault's reward harvesting and compounding rate

Beefy Finance's [vaults](../../faq/products/vaults.md), or more specifically the investment strategy tied to the vault, will automatically increase your deposited token amount by compounding arbitrary yield farm reward tokens back into your initially deposited asset. This constant cycle of harvesting rewards, and compounding, happens multiple times a day, and in this How-To we walk you through steps to check precisely how often this process occurs.

## Walkthrough

### The Binance Smart Chain example

No matter which chain you choose, you can easily use Beefy Finance's <A HREF="../../developers/deployed-contract-registry.md" TARGET="_blank">Deployed Contract Registry</A>. As an example, we will pick the CAKE-BNB LP vault on the Binance Smart Chain to demonstrate the process:

![Screenshot taken 5 May 2021](../../.gitbook/assets/cake-bnb-lp-2-5-2021.png)

#### 1. Go to [dashboard.beefy.finance](https://dashboard.beefy.finance)

#### 2. Find the contract for the vault you are looking at, and click on it, opening a page in BscScan

![](../../.gitbook/assets/cake-bnb-lp-vault-address.png)

#### 3. Now on BscScan, open the "Contract" tab and subsequently the "Read Contract" tab

![](../../.gitbook/assets/cake-bnb-lp-read-contract-tab.png)

#### 4. Scroll down to find the strategy contract, and click on it

![](../../.gitbook/assets/cake-bnb-lp-strategy-address.png)

#### 5. Look at the strategy contract transactions

![](../../.gitbook/assets/cake-bnb-lp-rate.png)

All these transactions are from the vault harvesting rewards which in turn also trigger the yield compounding into the initial deposited asset. The CAKE-BNB LP vault of this example compounds roughly every hour.

Each of the chains supported by Beefy may be queried using this method. The only difference will be the block explorer opened. For example on Polygon, PolygonScan will be opened instead.

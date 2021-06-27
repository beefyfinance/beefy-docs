---
description: >-
  In this guide you will find the required steps to check on your vault's harvesting and compounding rate.
---

# How to check your vault's reward harvesting and compounding rate

Beefy Finance's [vaults](../../faq/products/vaults.md), or more specifically the investment strategy tied to the vault, will automatically increase the amount of your deposited asset by compounding arbitrary yield-farm rewards back into more of that asset. This constant cycle of harvesting rewards, and compounding, happens usually multiple times per day.  In this How-To we walk you through steps to check precisely how often the compounding occurs.

## Walkthrough

NOTE: No matter which chain you choose, you can use Beefy's [dashboard.beefy.finance](https://dashboard.beefy.finance) to launch your investigation.

### Binance Smart Chain (BSC) example

As an example, let's choose the CAKE-BNB LP vault on the Binance Smart Chain to demonstrate:

![Screenshot taken 5 May 2021](../../.gitbook/assets/cake-bnb-lp-2-5-2021.png)

#### 1. Go to [dashboard.beefy.finance](https://dashboard.beefy.finance)

This dashboard chooses which statistics and vaults to show based on which blockchain network your connected wallet (e.g. MetaMask) is currently using. So if that's not now BSC, just switch networks to it and the dashboard page will refresh to show Beefy's BSC statistics and vaults.

#### 2. Find the contract for the vault you are looking at, and click on it, opening a page in BscScan

![](../../.gitbook/assets/cake-bnb-lp-vault-address.png)

#### 3. On the BscScan page, open the "Contract" tab and subsequently the "Read Contract" tab

![](../../.gitbook/assets/cake-bnb-lp-read-contract-tab.png)

#### 4. Scroll down to find the strategy contract, and click on it

![](../../.gitbook/assets/cake-bnb-lp-strategy-address.png)

#### 5. Look at the strategy contract transactions

![](../../.gitbook/assets/cake-bnb-lp-rate.png)

All these transactions are from the vault harvesting rewards which in turn also trigger the yield compounding into the initial deposited asset. The CAKE-BNB LP vault of this example compounds roughly every hour.

Each of the chains supported by Beefy may be queried using this method. The only difference will be the block explorer opened. For example on Polygon, PolygonScan will be opened instead.

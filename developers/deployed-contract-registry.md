# Deployed Contract Registry

All Beefy Finance deployed vault contracts on Binance Smart Chain can be viewed on [dashboard.beefy.finance](https://dashboard.beefy.finance).

#### On BSC, one can use this dashboard to check when the last harvest and vault compound has been:

1. Find the contract for the vault you are looking at, and click on it.
2. Now on BscScan, open the "Contract" tab and subsequently the "Read Contract" tab.
3. Scroll down to the 11th box to find the strategy contract, and click on it.
4. Look at the strategy contract transactions. All these transactions are from the vault harvesting rewards which in turn also trigger the yield compounding into the initial deposited asset.

#### On Avalanche, the method for checking how often your vault harvests and compounds is slightly different:

1. You will need the Avalanche block explorer for the C chain: [https://cchain.explorer.avax.network/](https://cchain.explorer.avax.network/)
2. Find the contract for the vault you are looking at. A quick hack is to search for the [mooToken](https://docs.beefy.finance/beefyfinance/faq/products/vaults#what-are-mootokens) the vault gave you. For example for SNOB-AVAX LP you will just search for mooSnowballSNOB-AVAX.
3. Now, you have the vault contract, go to the "Read Contract" tab in the CChain Explorer and scroll down to find the "Strategy". 
4. Last step: click on the Strategy contract address and look at the transactions listed there. All these transactions are again from the vault harvesting rewards which in turn trigger the compounding.
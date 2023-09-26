---
description: 'Last Update: September 2023'
---

# Fee Batch

{% hint style="info" %}
Note that the $BIFI migration discussed in these documents is ongoing, and so information in this page may be liable to change in the final implementation. This page has been released early for informational purposes, to assist users and tokenholders to understand the details of the planned migration.
{% endhint %}

The Beefy Fee Batch is another core component of the [.](./ "mention") which distributes vault fees to our Ethereum [governance-pools.md](governance-pools.md "mention") and [treasury.md](../../dao/treasury.md "mention"). As with the [revenue-bridge.md](revenue-bridge.md "mention") which delivers fees to the Fee Batch, the Fee Batch acts in one direct only, helping to move earnings from vaults to the Beefy DAO and its tokenholders.

## What does the Fee Batch do?

Beefy's Fee Batch contracts were designed and implemented to improve gas efficiency across the protocol in its management of vault fees. Forwarding fees immediately in small values may increase the speed of Beefy's cashflow, but in practice also depletes that cashflow with a corresponding increase in gas costs.

When preparing to send out fees, the Fee Batch's outflow transaction is a multicall, which sends $WETH to the [governance-pools.md](governance-pools.md "mention") and to a router liquidity pool, to swap for a stablecoin (e.g. $USDC), which is sent onwards to the [treasury.md](../../dao/treasury.md "mention"). The breakdown of fees into these categories reflects the [beefy-finance-fees-breakdown.md](../beefy-bulletins/beefy-finance-fees-breakdown.md "mention").&#x20;

Following the migration of the [bifi-token](../bifi-token/ "mention") to Ethereum in 2023, the protocol relied on Fee Batch contracts on each chain to aggregate fees from that chain's strategies, before transferring into the treasury and governance pools on that chain. See [here](https://optimistic.etherscan.io/address/0x2bbf9cfbda4293fa446e915aa12adc52ea8d5d53#code) for an example Fee Batch contract on Optimism, which often handled around 500 inflows and 2 outflows of $WETH per day, and [here](https://optimistic.etherscan.io/tx/0x8c8a31d0ff4e66fe55d5e55e2670ccf8015614cdd5bc78bd51ced42845bb6587) for an example outflow transaction.

Post-migration, most chains now use their [revenue-bridge.md](revenue-bridge.md "mention") contracts to batch fees before bridging, as explained in [#what-does-the-revenue-bridge-do](revenue-bridge.md#what-does-the-revenue-bridge-do "mention"). The obvious exception to this is Ethereum.

## Ethereum Fee Batch

Post-migration, the Ethereum Fee Batch contract has taken on the role of batching **all** revenue from the protocol's vaults after the [revenue-bridge.md](revenue-bridge.md "mention") has returned the funds to Ethereum. This covers inflows from all of the hub chains across different bridges and assets.

Once received by the fee batch, and a sufficient amount has accumulated, the fees are split as previously between the [governance-pools.md](governance-pools.md "mention") and the [treasury.md](../../dao/treasury.md "mention"), in accordance with the allocation detailed in the [beefy-finance-fees-breakdown.md](../beefy-bulletins/beefy-finance-fees-breakdown.md "mention"). Unlike under the previous fee batch, as the fees are received in stablecoins, the Treasury inflows do not need to be swapped, but incentives for the Governance Pools must first be swapped back to $WETH.

---
description: >-
  Anyone familiar with the fee structures typical of traditional finance will
  tell you fees matter.
---

# Beefy Fees Breakdown

![](../../.gitbook/assets/bulletin-beefy-finance-fees-breakdown.png)

**How much do fees matter?**

The answer can be hard to wrap your head around.

* $1M invested for 30 years at 8% with a 1% management fee yields $7.62 million.
* $1M invested for 30 years at 8% with a 2% management fee yields $5.74 million.
* $1M invested for 30 years at 8% with a 3% management fee yields $4.32 million.

**Now, let's throw out modesty for a minute.**

Unlike some platforms flashing their APYs for your attention, there are no catches on Beefy.Finance. For example, they'll promote an APY, but won't mention there's a penalty fee if you withdraw early.

Or the APY is given as a spectacular headline number, but the small print is that you have to _manually_ compound every single day to get that number.

**At Beefy we're proud to be doing things a little more transparently.**

_With our vaults, performance fees are included in the APY._

**So what you see is exactly what you get.**

Our vaults on Beefy charge a fixed performance fee structure on their harvest rewards. As described in [#what-is-the-vault-fee-structure](../../beefy-products/vaults.md#what-is-the-vault-fee-structure "mention"), these fees are distributed back to $BIFI tokenholders, the Beefy [treasury.md](../../dao/treasury.md "mention"), our strategists and the user that harvests the vault. They are the main source of revenue for the platform.

**Here's what a typical vault looks like:**

* 3.0% is distributed back to $BIFI tokenholders who participate in the protocol's governance incentives program;
* 0.5% is allocated to the Beefy treasury;
* 0.5% is awarded to the vault strategist; and
* 0.05% is awarded to the one calling the harvest function.

Following the passage of [\[BIP:45\]](https://snapshot.org/#/beefydao.eth/proposal/0xb070348f6c2cc229f2bcdc0c042077ee8eab4307a307b89537f8a78089b0c2eb), Beefy has introduced a maximum performance fee structure of up to 9.5%. Where this is applied to new vaults, here's what it typically looks like:

* c. 3.06-3.24% is distributed back to $BIFI tokenholders who participate in the protocol's governance incentives program;
* c. 5.44-5.75% is allocated to the Beefy treasury;
* 0.5% is awarded to the vault strategist; and
* 0.01-0.5% is awarded to the one calling the [#harvest](../../developer-documentation/strategy-contract/#harvest "mention") function.

For the rare vaults which do not [Harvest on Deposit](https://docs.beefy.finance/ecosystem/products/vaults#what-is-harvesting-on-deposit), we assign a withdrawal fee of up to 0.1% to each vault to protect bad actors from abusing the vaults with too much flipping. We share this amongst all the other users participating in the vault.

Finally, for users of our Beefy ZAP V2 tool, we charge a 0.05% zap fee on your deposited amounts when entering or exiting a vault. These fees are returned to the Beefy treasury by way of a intermediate batching treasury, which allows fees to be aggregated and swapped into stables before being deposited. See [how-to-beefy-zap.md](../../faq/how-to-guides/how-to-beefy-zap.md "mention") for more details on the ZAP V2 tool.

Apart from the fees fully listed above, anyone using Beefy should also remember the network transaction fees when adding or removing funds. These small fees go to the operators keeping the blockchain running, not Beefy.

**Bottom line: fees matter.**

When a Beefy vault offers you an investment with 14.46% APY, that's always with fees already factored in...

$1M invested for 30 years at 14.46 % APY yields…

$57,492,639 million

**With Beefy, what you see is what you get.**

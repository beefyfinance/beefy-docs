---
description: 'Last Update: August 2024'
---

# CLM

### What is CLM?

CLM stands for _"cowcentrated liquidity manager"_, which is Beefy's liquidity management product for concentrated liquidity (_**"CL"**_) pools. In essence, CLM allows day-to-day users to access the enormous opportunities of CL technology, without the effort and user-error risks that come from managing their own positions. The CLM contract issues depositors with an ERC-20 _"Cow Token",_ [_"Reward Cow Token"_ ](clm.md#how-does-the-clm-reward-pool-work) or [_"Moo Beefy Token"_](clm.md#how-does-the-clm-vault-work), reflecting their share of the pooled CLM funds being deposited into the CL position.

As with all other Beefy products, CLM automates complex onchain activities and aggregates scale across users to bring down the average cost for everyone. This means users get higher rates of return with far less effort when compared with handling the process yourself.&#x20;

_What's in it for Beefy?_ A share of all earnings generated are retained as fees for the DAO, the $BIFI tokenholders, the product's creator and the account harvesting the earnings. This means that all of the stakeholders involved in compounding user yields share a small proportion of the total rewards, whilst the user is always earning. It's a win-win-win-win-win.

CLM is a form of _"active"_ or _"automated"_ liquidity management (**"ALM"**) technology, and stands in contrast to a number of other ALM products currently on the market. CLM brings a unique approach to maximizing utilization, which is aimed squarely at delivering optimal yields for our users.

### What is Concentrated Liquidity?

Concentrated liquidity is a mature form of onchain liquidity that offers higher yields and better availability than traditional liquidity. Instead of having to provide liquidity for swaps at any price range (as with traditional liquidity pools, like [Uniswap V2](https://docs.uniswap.org/contracts/v2/overview)), users can tailor the range at which they are willing to provide their own liquidity. The Trade-off is receiving a greater share of trading fees within the selected range, in exchange for the risk of no fees when their position falls out of range. CL technology was first popularised by Uniswap's v3 protocol, and has since blossomed across many different iterations and protocols. The [UniV3 documentation](https://docs.uniswap.org/concepts/protocol/concentrated-liquidity) is the best place to start learning about the specifics of how concentrated liquidity works.

CL products introduce more features to the onchain liquidity process, but also add more complexity. As prices are constantly moving, managing CL positions requires constant evaluation of the appropriate range to supply liquidity, which was not a concern with earlier generations of liquidity pools (like [Uniswap v2](https://docs.uniswap.org/contracts/v2/overview)). CL positions are also typically represented by non-fungible tokens rather than fungible ERC-20s, meaning they require an entirely different set of functions and interfaces to interact with the smart contract position.

Though Beefy has [found ways](https://beefy.com/articles/beefy-cl/) to autocompound CL positions using other liquidity managers,  our traditional yield farming products were not designed to interface directly with CL pools. Beefy's CLM products help to bridge that gap.

### What's the difference between CLM and yield farming strategies?

CLM represents an expansion of Beefy's automation products to a different level of the supply chain. Unlike our yield farming [strategies.md](strategies.md "mention"), CLM directly creates and manages liquidity positions, with no need for intermediate farms or incentives. The below table provides a quick and simple breakdown of the differences between these two core products:

<table><thead><tr><th width="179"></th><th>Yield Farming / CLM Vaults</th><th>CLMs / CLM Pools</th></tr></thead><tbody><tr><td>Built on Liquidity Pools</td><td>Yes - indirectly through farms</td><td>Yes - directly</td></tr><tr><td>Requires Farm Rewards</td><td>Yes</td><td>No</td></tr><tr><td>Trading Fees</td><td>Compounded in underlying products</td><td>Compounded by Beefy</td></tr><tr><td>Rewards</td><td>Compounded by Beefy</td><td>Accrued/Distributed by Beefy</td></tr><tr><td>Concentrated Liquidity</td><td>Indirect only with CL managers</td><td>Directly manages CL positions</td></tr><tr><td>Range Management</td><td>Depends on provider</td><td>Yes</td></tr><tr><td>Harvest Process</td><td>Claim rewards, swap and redeposit into the principal</td><td>Claim fees/rewards and resets position(s)</td></tr><tr><td>Token Name</td><td>mooTokens or mooBeefy Tokens</td><td>cowTokens or rcowTokens</td></tr></tbody></table>

As the two products sit at different levels of the supply chain, Beefy's yield farming strategies can actually be built on top of Beefy's CLM products where there are rewards to compound into the CL position. CLM has been designed from the ground up to offer an optimal approach to automated liquidity management, in a way that unlocks optimal autocompounding of incentives through our ordinary strategies.

### How does CLM work?

Beefy's CLM products are laser focused on ensuring that the maximum amount of user capital in the product is deployed, in range and earning (or _"fully active"_). This includes not only the deposited funds, but also any trading fees accruing on the current investment and all past trading fees which have already been compounded back into the position. Where trading fees are constantly reinvested, we unlock the magic of compounding, leading to significantly increased returns. Where rewards are paid in place of trading fees, the rewards accrue for users to claim on the Beefy app.

The CLM method is extremely simple. Every time a CLM product either receives a user deposit or is _"harvested"_, Beefy automatically: (1) withdraws all deposits and trading fees to reset the position; (2) redeposits all of one token and most of the other into a precise 50/50 position; and (3) redeposits all other tokens into a single-side position (a.k.a. the _**"alt"**_). Where the quantity of deposited tokens doesn't match the current ratio of the liquidity pool, the correct ratio of tokens will be deposited and the remainder will be returned to the user.

To ensure the position stays within range, the range is reassessed and reset every 6 hours by way of automated onchain calls of the privileged _moveTicks()_ function in the strategy contract. This facilitates smooth, consistent and predictable maintenance of range, without the risk of manipulation by third parties.

In some cases such as Solidly forks, a pool may not pay trading fees but instead provide rewards in other tokens not included in the pool. In those circumstances, Beefy will distribute these to holders in the same manner as other forms of rewards - i.e. as a linearly-accruing claimable reward.&#x20;

As trading fees or rewards accrue and price changes in the pool impact on the position's range, the position's effectiveness will change over time until the next harvest. However, Beefy routinely harvests all products with any rewards every day (on all chains except Ethereum).&#x20;

#### Alt Position

The _"alt"_ position exists to ensure that the user's entire position remains fully active, and all tokens are deployed in range. The advantage of the alt approach is that there is no need to _"rebalance"_ the position (i.e. sell the outperforming token to buy the underperforming). ALM products which regularly rebalance by selling tokens immediately realize impermanent loss, which can significantly dampen profitability in products which rebalance regularly (e.g. narrow-range CL products).&#x20;

As shown by the dotted line in the graph below, the alt is positioned differently from the main position to take full advantage of the provided liquidity. Instead of using the main position's range, the alt is provided in a smaller range set between (i) the upper or lower boundary of the main position (depending on which token is overweighted); and (ii) the nearest valid _"tick"_ (or fixed boundaries between discrete areas in price space) between the adopted boundary and main position's other boundary. &#x20;

In the example below, the alt position is being set in the range between the dotted line and the bottom blue line, whereas the main position is being set between the two blue lines, which are set equidistant from the current price (i.e. the white line).

<figure><img src="../.gitbook/assets/range-graphic (2).png" alt=""><figcaption><p>The <em>"Alt"</em> position works by counterbalancing the main 50/50 position with a single-side position configured to a smaller range than the main position. Together the two ensure full deployment of assets and maximal earnings without rebalancing.</p></figcaption></figure>

#### Calmness Check

A wider general issue with many forms of concentrated liquidity products is that prices can be manipulated by attackers, for instance using flash loans. To protect against this, CLM incorporates checks on deposit to ensure that deposits are only made in _"calm"_ periods, meaning periods where the relative change of the current price arising from the deposit is not large relative to the time-weighted average price (or **"TWAP"**) of the pool.&#x20;

The _"calm zone"_ is shown in the blue area of the diagram below, and is bound by the pool's TWAP over the last 60 seconds. Where in some cases the current price exits the blue _"calm zone"_, the contract's logic has identified large relative changes and the deposit transaction will be reverted to safeguard against attacks aimed at stealing part of the user's deposit funds.

<figure><img src="../.gitbook/assets/calm-zone-graphic (3).png" alt=""><figcaption><p>The <em>"calm zone"</em> ensures deposits are only possible when the current price sits within a reasonable margin of the time-weighted average price. This ensures users won't lose funds through deposits during times of high volatility.</p></figcaption></figure>

### How does the CLM Pool work?

All CLM products are designed to handle rewards - i.e. additional tokens paid out to liquidity providers beyond trading fees - natively, so that users never need to exit their CLM position to benefit from additional incentives.&#x20;

Rewards can be distributed by Beefy using our CLM Pool contracts, or through third party services like [Merkl](https://merkl.xyz/) by Angle. The CLM Pool contract accepts the standard CLM _"cowToken"_ as a deposit and then issues a corresponding _"rcowToken"_ at a 1:1 ratio. Once deposited, the position benefits from a share of any rewards currently being paid out by the CLM Pool, and will automatically participate in any future rewards. Rewards can be claimed on the relevant product page on the Beefy UI, or manually direct from the smart contract.

By default, the Beefy UI (including our ZAP tooling) now automatically deposits user funds into the CLM Pool contract, so no additional work is needed to benefit from rewards. Where for any reason a user continues to hold a standard _"cowToken"_, this can be deposited into the CLM Pool using the UI. Likewise, the withdrawal workflow now automatically bypasses the standard _"cowToken"_ working primarily with the CLM Pool version.&#x20;

### How does the CLM Vault work?

Beefy can also build its classic autocompounding [vaults.md](vaults.md "mention") on top of CLM products, which automatically claim all incentives being paid out, swap them back into the principle assets and redeposit into the CLM product. As ever, this results in a compounding effect, unlocking the higher exponential rewards that Beefy is known for. This is by far the easiest way to access all the benefits of concentrated liquidity with minimal effort and maximal rewards.

Like our standard vaults, the CLM Vaults are ERC-20 compliant, so issue a _"Moo Beefy"_ token (with ticker prefix _"mooBeefy..."_) to users who deposit them. And as with vaults, the amount of underlying _"cowTokens"_ or _"rcowTokens"_ being handled by the strategy will increase over time, meaning _"mooBeefy"_ tokens are not 1:1 with the underlying assets. As many concentrated liquidity designs do not involve issuing an LP token like classic UniV2 liquidity (often using NFTs instead), it is the underlying CLM tokens that increase, rather than an LP token.

In addition to compounding all underlying rewards, Beefy's CLM Vaults also have the ability to host [boost.md](boost.md "mention") incentives on top. To access, users simply deposit their _"mooBeefy"_ tokens into the boost contract to begin accruing rewards in a linear fashion. This is necessary for rewards which Beefy agrees not to sell/compound, such as grant-funded tokens.&#x20;

### Do CLM products suffer from impermanent loss?

CLM's novel design results in a different approach to impermanent loss (**"IL"**)). However, IL itself remains a feature of generally all forms of DeFi liquidity, and does occur within CLM products (as with all other ALM products). It is important to develop an understanding of how IL operates and the risks it presents before investing in any CL products.

The key difference with Beefy CLM is that, while the the position is in range, IL not realized because assets are promptly returned into range either in the main or alt positions without selling any assets. In other ALM products, the act of rebalancing the position (i.e. selling tokens) within range range causes IL within the position to become realized during its ordinary life, whilst also incurring additional fees in selling the token. Where price oscillates heavily, this can mean IL is repeatedly realized where the range is somewhat too narrow and the position frequently rebalances.

### How does impermanent loss work in concentrated liquidity?

Impermanent loss in concentrated liquidity products can be divided into two types:

1. **Range IL** - where the provided liquidity is in range and being traded, so both the quantity and value of assets attributable to the user's position changes over time when compared with not providing liquidity at all; and
2. **Out-of-range IL** - where the provided liquidity is out of range and not being traded, so the quantity of assets attributable to the user's position remains static, and only the value of assets changes over time when compared with no providing liquidity at all. In these circumstances, the balance is always overweighted in the underperforming asset.

Range IL is natural to all CL positions, and is a necessary consequence of a position being able to earn trading fees or rewards. The core determinant of the size of any Range IL is the size of the range selected for the pool. For example, the IL users experience in ordinary non-concentrated liquidity (e.g. [Uniswap V2](https://docs.uniswap.org/contracts/v2/overview)) is effectively the same as the Range IL from a CL position with a range covering all prices. In all narrower ranges, the amount of Range IL suffered from the same price movement is relatively larger in CL pools than traditional pools. At extremely narrow ranges, a minuscule move in price can significantly imbalance a position, meaning very high levels of Range IL.

We can think of basic CL positions as imposing limits on the possible Range IL of a position. Where a position is left to operate within a single fixed range, the amount of Range IL it can suffer is naturally limited on both sides by the end of its range. However, where the range on the position is later reset by selling tokens, the potential Range IL from the new range will be cumulative (i.e. in addition to) any Range IL that was realized by resetting the original position. This means that there is no limit on the possible aggregate Range IL that users can suffer through actively managing CL positions. Poorly managed positions can easily lose value through Range IL over time.

The other side of this natural limit on Range IL is Out-of-range IL, which kicks in when the position moves our of range and Range IL stops. Out-of-range IL is a generally undesirable phenomenon, because the user is not earning anything by providing liquidity but is bearing increased exposure to the underperforming asset. The benefit of Out-of-range IL is that it limits the amount of IL a position can suffer by fixing the quantity of tokens entirely in the undervalued token. In a situation where two assets are oscillating in price against one another, some temporary exposure to Out-of-range IL may be tolerable where the user expects the position to come back into range in a reasonable period of time. However, where the position is expected to be out of range for some time or even permanently, there is nothing to be gained from the CL position, and so it's often best to just realize the Out-of-range IL and move on.

### How do I evaluate impermanent loss in a concentrated liquidity position?

Though it is necessary to consider both types of IL to evaluate CL positions and realize the benefit of ALM products, in practice the two types interoperate over the life of a position. When a position falls out of range, the current Range IL is translated into Out-of-range IL, so the difference in token quantities is crystalized and only the difference in price continues to cause IL. When that same position comes back into range, the Out-of-range IL is dissolved back into the Range IL, so Out-of-range IL no longer needs to be considered.

However, most CL users will be focused on the net profit of their position, which is the sum of all earned trading fees and all realized and unrealized IL. For in-range positions, net profit offsets trading fee earnings against changes in both price and quantity giving rise to Range IL.  For out-of-range positions, net profit only considers price changes for Out-of-range IL, but also factors in the lack of trading fee or reward earnings. And finally, where a positions moves into and out of range over time, a calculation of net profit requires a consideration of the cumulative realized and unrealized Range IL and Out-of-range IL as well as the net earnings arising from the stop-start trading fees/rewards being earned on the product.&#x20;

The undesirability of out-of-range positions and IL is the core reason for developing and using ALM products, such as Beefy CLM.

### How does impermanent loss work in ALM products and CLM?

All CLM and ALM products will suffer Range IL as prices change. As described above, individual concentrated liquidity positions naturally limit Range IL by imposing a single range for trading. However, when an ALM position (including CLM products) falls out of range and is reset, the IL from the previous setting is then realized within the position, meaning the quantity of the assets held in the position can decrease when compared to what was deposited. ALM products, including CLM, accept the risk of Range IL in the expectation that the trading fees or rewards earned from staying in range should exceed the Range IL in the long term.

Where the range is continually changed over time in an ALM product that rebalances by selling tokens, IL from every reset will be aggregated over time and can easily exceed the IL a user would have suffered by comparison in a normal unmanaged position. By contrast, CLM does not sell tokens, meaning Range IL is not realized until the position is exited or moves out of range, meaning the aggregate IL of CLM products tends to be lower than with other ALM products.

The real value of Beefy's CLM product is how it handles Out-of-range IL. Much like all ALM products, CLM is designed to tackle positions falling out of range and failing to earn trading fees or rewards. However, unlike most other ALM products, CLM achieves this by naturally balancing the user's asset exposure with its _"alt"_ position.

By contrast, many other ALM products seek to "rebalance" their position, meaning they will sell the overperforming asset to purchase more of the underperforming asset, and fully reset the position to an equal balance. The impact of this is that all IL affecting the position at the point of rebalancing is fully realized whenever the product is rebalanced, and what's reinvested is the sum of the deposited assets, the trading fee earnings and the cumulative IL to date. All too often, the cumulative IL in traditional ALM products will far exceed earnings, meaning users walk away with less than they deposit.

By effectively avoiding realizing Range IL and handling Out-of-range IL, Beefy's CLM products avoid much of the IL that other ALM products will be unavoidably affected by. This means a CLM position is less likely to suffer a net loss because of IL than other ALM products. In situations where two assets oscillate in price against one another, traditional ALM products may frequently rebalance, thereby realizing and aggregating a far greater amount of IL. Meanwhile, CLM calmly resets the alt balance holding IL at bay until the user chooses to exit.&#x20;

### In what situations does CLM perform best?

CLM is designed to capture maximal trading fee yield for those who are comfortable earning either of the assets in the underlying liquidity pool. The product aims for that sweet spot between maximal asset utilization without the need to constantly rebalance the position by selling assets. The net impact will often be higher APYs than most other ALM product designs on the exact same pool.

The trade-off for CLM users is that the position does sustain asset imbalances reflective of Range IL. Overtime, the alt can become the larger or even dominant portion of the position, which is not suited to users who are uncomfortable holding an imbalanced proportion of the underperforming asset. The key determinant of the speed and likelihood of the alt dominating the position is the size of the position's range: very narrow ranges can be quickly imbalanced by Range IL, leading to a very large alt position and a significant amount of unrealized IL.

### Are any situations still risky for CLM?

Absolutely. It's a simple fact that all concentrated liquidity products present additional risks of falling out of range, which result in all assets being traded into the undervalued token in the pair. Ordinarily, this risk can be mitigated by widening the range of the position; however, CLMs aim for an effective range setting that will always earn attractive trading fees (e.g. sufficient in-range liquidity for aggregators to route through for large transactions). This means that CLM products will always be vulnerable to the risks of Out-of-range IL where the market corrects sharply and quickly. This is the same for all concentrated liquidity products where the range is narrower than the full range of prices.

For example,  let's imagine depositing into a new WETH-USDC CLM product at a precise 50/50 balance. The range of the product is set at c. 20% of the relevant price range, meaning 10% either side of current price. Assume that a correction in the price of $ETH means the pool's price dips 16% within the 6 hours between range resets. This would (i) take the CLM product out of range into 100% $WETH; (ii) thereby realize Out-of-range IL;  and (iii) on reset, would create a large $WETH single-side position. Now imagine in the next 6 hours the price recovers by 11% of the original 16% dip, again taking the position out of range, but in the opposite direction. Again, this: (i) takes the CLM product to 100% $USDC; (ii) realizes Out-of-range IL; and (iii) lead to a large $USDC single-side position. The price then gradually recovers to the original prices, and the position naturally returns to a 50/50 balance.

The impact of the above scenario is that Out-of-range IL is being realized on both sides of the pool:&#x20;

* First, the 50% $USDC has effectively been traded for $WETH in the first 10% range, which is at prices lower than the deposit, meaning more $WETH, no $USDC, and lower USD value. At 100% $WETH, the position then suffers all the loss in the remaining 6% dip in $ETH's price.  After being reset after 6 hours, the range of the position will be 10% either side of the lower price (e.g. 10% of 84% (=100%-16%), so 8.4% relative to the original deposit).&#x20;
* Second, after the price moves in the opposite direction by 8.4%, all of that $WETH will have been traded for $USDC at lower averages prices than the $ETH was obtained for. As $ETH continues to increase in price up to the full 11%, the position won't participate in those increases as the position is 100% stable. This means the 100% $USDC position will have a firmly lower USD value than the initial deposit, and the decrease will be greater than the net change in prices (16% decrease - 11% increase = 5% net change) as it incorporates the realized Out-of-range IL on both sides.
* Finally, as the position promptly returns to the normal price, more deposits and/or trading will naturally return the position to a 50/50 balance at the same price. The 100% $USDC will be used to buy back $ETH at the lower prices, but with less overall assets. Upon returning to the starting prices, the original depositor would notice that they have less of both assets, coming from realized Out-of-range IL losses, despite the assets and prices being returned to the same position as at the start. They may also consider that they would have had zero loss for just [holding](clm.md#what-does-the-hold-statistic-show) the assets.&#x20;

The above risks factor into any ALM product, and involve natural risks to consider in all concentrated liquidity scenarios. No product is able to completely avoid these facets of concentrated liquidity without some kind of trade-off elsewhere. Here, CLM is performing as intended - assets are promptly returned to range and continue earning trading fees throughout these spikes (which are often significant as trading increases with the price volatility). The position is regularly reset to avoid the risk of going out of range early in the scenario and missing all trading fees. And towards the end, the saner market allows the position to recover a natural 50/50 balance and the users to continue earning in a normal fashion quickly and consistently.

With that said, users should be aware that CLM still bears IL risk in these extraordinary scenarios, as do all concentrated liquidity products. The value proposition for long-term users is that extreme scenarios may happen for a day or two each year, but the rest of the time their CLM position is safely generating the consistently higher returns that concentrated liquidity offers at minimal effort.

### How does CLM optimize my yield?

CLM's innovative formula for managing concentrated liquidity positions aim to bring users far superior yield with a number of improvements:

* Earnings are harvested automatically to reduce the time users need to invest in managing their positions;
* Any trading fees are reinvested to establish a compounding effect within the product, i.e. by earning more from previously reinvested earnings;
* Any trading fees are harvested regularly to increase the rate of compounding in the product;
* Deposits are aggregated, meaning a single set of gas fees split across many users rather than each user incurring the same gas fees separately;
* The aggregate volume of deposits means less time is needed to build up to a profitable harvest, which can also increase the rate of compounding in the product;
* The range is reset with each deposit and harvest, minimizing the amount of time spent out of range and not earning trading fees;
* Excess assets arising from the gradual imbalance of the pool are placed in range through a single-side position, meaning they still earn fees;&#x20;
* No rebalancing takes place, meaning out-or-range IL is not realized in the product; and
* CLM positions are automatically added to the Beefy CLM Pool to benefit from a range of different rewards without any action by the user.

### What is the displayed yield on CLM products?

The displayed yield on Beefy CLM products reflects: (1) the current trading fees being compounded from the CL pool, extrapolated out for the next year; (2) the current simple rate of any rewards being paid out by the CLM Pool; and (3) the current simple rate of any rewards being paid out by Merkl.&#x20;

All additional rewards accrue in the Beefy app to be claimed by users, and are not automatically reinvested by the CLM product. Only the yield from trading fees reflects compounded _"annual percentage yield"_ or APY; all additional rewards are displayed as an _"annual percentage return"_ or APR. Where a Beefy yield farming strategy is built on top of a Beefy CLM product, the additional rewards will also be compounded, giving a total APY across the entire position.

Past and current performance is no indication of future yield, so users are advised to review the volatility of yield in any CLM product and the likelihood of future demand for the pool's liquidity before investing. &#x20;

### What is the percentage displayed in the title of my CLM product?

All CLM products include a percentage figure as part of their CLM labelling, which denotes the pool fee tier for the underlying CL pool. A CLM product with a percentage of _"0.30%"_ charges buyers and sellers using the pool a 0.3% fee on their transaction, which is deducted from the balance of tokens they receive from a trade with the pool. A _"0.05%"_ pool charges a far lower fee.

In the case of CLM, fee tiers reflect the amount that Beefy depositors will be benefitting from as the pool is traded through by other parties. They are not to be confused with the Beefy fees charged on earnings. For example, a higher fee tier reflects a higher amount of earnings for the same volume. Higher fees are typically charged on more volatile pools and lower liquidity, which typically means lower volume.

### What does the "HOLD" statistic show?

The Position Performance module for CLM Pools shows a _"HOLD"_ statisti&#x63;_,_ which expands to show a _"CLM vs Hold"_ figure. These figures are intended to give an impression of what impermanent gain or loss exists within the position, relative to if the user had simply held onto the deposit value in 50% allocations to each pool token with no other activity. The base figure next to the _"HOLD"_ is what the current value of the user's funds would be for holding both 50% allocations, so reflects the change in market value only. The _"CLM vs Hold"_ figure reflects the difference between the current value of the user's position, and the _"HOLD"_ figure. A negative value means the user would have retained more USD value by simply holding the tokens. A positive value means the user has gained more in USD value by using the CLM product.&#x20;

### What fees are charged on CLM?

Beefy's fee structure for CLM products is exactly the same as for our yield farming strategies, as set out in [beefy-finance-fees-breakdown.md](../ecosystem/beefy-bulletins/beefy-finance-fees-breakdown.md "mention"). The total fee is capped at a maximum of 9.5% of all trading fees earned in the product. More specifically:

* c. 3.06-3.24% is distributed back to $BIFI tokenholders participating in the protocol's governance incentives program;
* c. 5.44-5.75% is returned to the Beefy treasury to operate the Beefy DAO;
* 0.5% is awarded to the creator of the CLM product; and
* 0.01-0.5% is awarded to the party that calls the [Broken link](broken-reference "mention") function on the specific CLM product to claim trading fees and reset the position.

For CLM Pools, this fee is charged on all trading fees claimed by the position in the underlying protocol (as opposed to claims made by the user through Beefy). For CLM Vaults, a separate vault fee is also charged on the amount of each harvest - i.e. the rewards/incentives being claimed and reinvested by Beefy on top of the CLM Pool.&#x20;

In addition, Beefy charges a small swap fee on deposits into an imbalanced CLM product, which is distributed to other users of the same product. This fee exists solely to protect against users taking advantage of the imbalance to swap their single deposit token into a balanced proportion of both tokens, by depositing less than is required to rebalance the pool and then immediately exiting. The fee scales depending on the size of the deposit and the imbalance, but for practical purposes it is capped at no more than 50% of the pool fee level.&#x20;

As an example of a swap fee, imagine a user depositing into a ETH-USDC CLM product which charges a 0.05% pool fee and is overweighted in $ETH (meaning the user would need to deposit more $USDC). Imagine the imbalance amounts to 1,000 $USDC. A user wanting to deposit $5,000 would first deposit 1,000 $USDC, before depositing a 50/50 balance of $USDC and $ETH from the remaining funds. The swap fee is only charged on the imbalanced deposit, so just on the 1,000 $USDC and not the whole $5,000. As the pool fee is 0.05%, the maximum swap fee is half of that, so 0.025% of 1,000 $USDC, or around $0.25. The fee is immediately distributed among the other user positions in the vault. As others later enter the product, the depositor in this example then also benefits from swap fees arising from the other depositors.

### How do I deposit into CLM?

Underneath the hood, Beefy CLM products accepts deposits that rebalance the existing position, which is effectively the inverse proportion of the current position's balance. This means users seeking to deposit a 50/50 quantity of tokens would use all of their underweighted token, but less than all of the overweighted tokens (e.g. 48/50), with the remaining tokens being retained by the user. This means the product will only accept the underweighted token up to the point of a 50/50 position, at which point it can only add equal values of both tokens.

To improve the user experience, Beefy's popular ZAP tooling has been brought to CLM to allow users to provide a single deposit of any of their favourite tokens, which will then be automatically swapped using DEX aggregators into the necessary proportionate of the relevant deposit tokens. Given that the balance of deposit tokens required to enter a CLM product can change at a moment's notice, a simple ZAP transaction is the optimal way to access the product.&#x20;

{% hint style="warning" %}
**Single-side Deposits:** Because the CLM deposit tokens you receive on deposit reflect a proportional share of all tokens in the vault that's the same proportion for all users, a user who deposits only one token directly (i.e. not through ZAP) would instantly gain entitlement to a proportionate share of the other token in exchange for part of their deposit. This allows single-side deposits to effectively swap freely into the other asset, taking from the other depositors in the vault who are left with more of the single-side deposit asset. In extreme cases, excessive single-side deposits can deprive ordinary depositors of their alternative asset, leading to excessive and unintended exposure to the single-side asset for everyone.
{% endhint %}

### What happens when I withdraw from CLM?

The CLM withdraw workflow involves the vault contract taking back the deposit tokens that the user received for their deposit (meaning users need to approve access to the token from their wallet). Because of this, it's vital that users do not incidentally move or manipulate their cow or reward cow tokens for the duration of their deposit. Once the tokens are returned, they are immediately burned and exchanged for a proportional share of the tokens held by the CLM product which are sent back to the user.&#x20;

For example, if a user has 1 cow token, from a total of 10 tokens issued, the user is entitled to 10% (= 1/10) of the tokens in the CLM product. If the product currently has 1 $ETH and 10,000 $USDC, the user will receive roughly 0.1 $ETH and 1,000 $USDC. This can be a totally different quantity to the user's original deposit; for instance, the user could have deposited 0.15 $ETH and 500 $USDC, in which case appreciation in the price of $ETH has significantly impacted the final tokens received.&#x20;

With ZAP tooling, users can also withdraw into any token of their choice, using DEX aggregators to automatically swap out the different tokens included into the position.

### Who is in control of the CLM products?

As with our yield farming strategies, each CLM product is generally designed to be immutable, meaning they cannot be altered after deployment. However, as with our ordinary strategies, CLM products rely on the standard set out in EIP-1167 known as ["minimal proxy" contracts](https://blog.openzeppelin.com/deep-dive-into-the-minimal-proxy-contract), meaning identical CLM products can be deployed easily with reconfigured settings. The CLM vault contract then has functionality to change the strategy it is using to the reconfigured strategy, meaning Beefy's contributors are able to switch strategies where issues arise. All strategy updates are timelocked and operated by the Beefy Development Council's multi-signature wallet.

For more information, see the equivalent comments for yield farming strategies at [#who-is-in-control-of-the-strategies](strategies.md#who-is-in-control-of-the-strategies "mention").

### Has CLM been audited?

Of course! As a brand new product with an innovative new design, Beefy's contributor team have worked closely with a series of leading auditors to tackle all conceivable security and operational risks. You can find copies of their various reports here:

* [Audit 1](https://github.com/beefyfinance/beefy-audits/blob/master/2024-02-28-Beefy-Zellic-CLM-Audit.pdf) by Zellic dated 28 February 2024;
* [Audit 2](https://github.com/beefyfinance/beefy-audits/blob/master/2024-04-06-Beefy-Cyfrin-CLM-Audit.pdf) by Cyfrin dated 6 April 2024;
* [Audit 3](https://github.com/beefyfinance/beefy-audits/blob/master/2024-06-30-Beefy-Certora-CLM-Audit.pdf) by Certora dated 30 June 2024; and
* [Audit 4](https://github.com/beefyfinance/beefy-audits/blob/master/2024-07-02-Beefy-Sherlock-CLM-Audit.pdf) by Sherlock dated 2 July 2024.

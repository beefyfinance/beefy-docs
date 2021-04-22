# Vaults

## What is a Vault?

Vaults are investment instruments that employ a specific set of strategies for yield farming. They make use of automation to continually invest and reinvest deposited funds, which help to achieve high levels of compounded interest. Vaults are the core of the Beefy.Finance ecosystem. In a Beefy vault, you earn more of the asset you stake in it regardless if this is an liquidity pool \(LP\) token or a single asset. For example, vaults where one can stake BTC-BNB LP will result in more BTC-BNB LP over time, effectively growing your share in the vault and thus allowing for more and more rewards over time.

Despite the name 'Vault' suggests, user funds are never locked in any vault on Beefy.Finance. One could always withdraw from a vault at any moment in time. Beefy.Finance also does not own user funds staked in vaults. However, it is generally best to view vaults as investment tools to store funds for the medium to long term in order to have the effects of compounding really kick in.

When browsing the vaults on the platform, you will see the annual percentage yield \(APY\), which takes the frequent compounding into consideration compared to annual percentage rate \(APR\) which does not. You will also see daily interest percentages and the total amount invested in a vault by all users \(TVL\). Furthermore, one can see what underlying platform the vault is using as a source of revenue.

Each vault can either refer to a pair of tokens invested in liquidity pools, such as CAKE-BNB LP tokens within the Binance Smart Chain ecosystem, or a single token invested in lending platforms or single stake reward pools. After depositing tokens to a vault, the user is supplied with vault specific mooTokens which represent their share in the vault. We will elaborate on mooTokens in the next section.

Anyone in the Cowmunity can work together to build new strategies and submit them to governance for voting. We look at vault requests via our official forum where anyone is free to submit [vault requests](https://forum.beefy.finance/c/vault-requests).

Summarizing, vaults can:

* Efficiently execute yield farming strategies.
* Compound rewards into the initially deposited token amount.
* Use any asset as liquidity.
* Provide one asset as collateral for another.
* Manage collateral at a safe level to mitigate liquidation.
* Put any asset to work to generate a yield.
* Reinvest earned profits.

## **What are mooTokens?**

A mooToken can be seen as a receipt that you get when depositing into any Beefy vault. This is a fully automatic process. For example, you receive mooBifi tokens from depositing $BIFI into the Beefy Maxi vault. These mooTokens do not 1:1 represent the token amount initially deposited but it does represent the value of your share in the vault. As a vault generates profit, the amount of mooTokens in your wallet remain constant while the underlying invested token amount in the vault increases. Whenever you want to withdraw the tokens that are staked for you in the vault, you need your receipt \(mooTokens\) which you hand in to redeem the deposited tokens + yield. Beefy.Finance users should hold on tightly to the mooTokens i.e. deposit receipts and not sell or exchange them to strangers or you will lose ownership of your staked assets in the vault.

## **How often do the vaults harvest their profits and reinvest?**

Vaults are normally harvested multiple times daily and profits are automatically reinvested \(compounded\). Larger vaults, such as our BSC $CAKE vault, are harvested even more frequently.

## Why can't someone just do this themselves?

They could, but vaults help you save on personal time and transaction fees, maintain healthy collateral to debt ratios, self-optimize for the best possible yields, and automatically reinvest earnings. Attempting to do this manually would result in large inefficiencies. At Beefy we like to say: "Sit back and relax, the vault does all the work for you."

## **What is the vault fee structure?**

Most vaults have a performance fee structure, taking 4.5% of harvest rewards. This 4.5% on profits is again split up: 3% is distributed back to the reward pool and to $BIFI stakers, 0.5% is allocated to treasury, 0.5% is for the strategist that developed the vault and 0.5% for the one calling the harvest function. These fees are already built into the APY of each vault and daily rate. You do not need to calculate these yourself.

The performance fee on additional yield i.e. vault profits is largely distributed back to $BIFI stakers and is the main source of Beefy.Finance's platform revenue. A part of it also funds the treasury which is used to further fund platform development and security and other initiatives. The performance fee was also implemented to promote community engagement and governance participation. A successful and engaged community is critical for our future growth, which in-turn rewards platform users even more.

Furthermore, vaults have a withdrawal fee. The main purpose of this fee is to prevent possible exploits from bad-faith actors. Without the fee, somebody could deposit just before the harvest\(\) function execution and withdraw straight after that event, taking a % of the gains generated by legitimate stakers. Withdrawal fees stay in the vault and are shared amongst vault funds. 

## **Does the performance fee get taken out when I withdraw my funds?**

* No, the fees are taken every time someone calls the harvest\(\) function.

## Does the vault page show the APY?

Yes. Our displayed APY values reflect the predicted rate earned on a vault in a year. This rate is determined by the underlying platform it uses, the strategy that it is interacting with at the time, the total amount of funds in the vault and also takes into account the effect of compounding. As a unique feature, we have also included all vault fees in the APY calculation. What you see is what you get!

## What risks do the vaults have?

To date, there has never been a Beefy vault incident. This does however not mean that a vault is entirely risk free. Below are some of the general vault risks:

* Assets deposited into the vault have no risk of decreasing in quantity but can decrease in monetary value.
* As with any smart contract, the ultimate risk is that an investor's funds can end up stolen or unable to be withdrawn. The team does take steps to quantify the security risks of smart contracts and only will interact with ones that meet a specific set of requirements after excessive testing to make sure the underlying platform does not contain so called 'rug-pull' functions. 

## **What are the different vaults?**

* **Money Market :** Utilizes lending platforms, such as Venus on BSC, to generate the highest possible yield for these coins \(e.g. BUSD, BNB, LINK, DOT, DAI, USDT, ETH, or BTCB\). 
* **Native Token Farming :** Takes advantage of the high yield on popular farms by depositing another asset to earn, sell and compound profits of the native reward token.

## What will I get out when I make a vault withdrawal?

You will always withdraw the token type that you deposited, because at Beefy you earn what you stake. You will get the amount you deposited plus the yield generated minus the vault withdrawal fees.

## **How do LP vaults work?**

Liquidity pool \(LP\) vaults work by reinvesting the fees awarded to LP participants. In return for providing liquidity to the pool, many platforms reward investors with tokens. Our vaults regularly harvest these rewards, sell it, buy more of the LP’s underlying assets, and then reinvest to complete the cycle.

This compounds the rewards gained from a liquidity pool. Beefy.Finance creates strategies that automate this process, saving you time and gas fees in comparison to farming manually. This is all done for a tiny fee that is distributed back to those how stake in Beefy's governance pool or in the BIFI Maxi vault. A small percentage also goes to the Beefy Finance treasury.

## **How often are balances updated in the vaults?**

* Pending rewards are not reflected in the balance until they are swapped for the initial deposited token. This can vary depending on the strategy running. 

## **Why do I have less mooToken than the amount of tokens I deposited?**

* The mooTokens represent the share of the Vault the user has. As the vaults generate profit, the amount of shares \(mooToken\) remain constant, and the underlying token amount increases. 
* There generally are no deposit fees, so the amount of tokens you deposit is maintained the second after you deposited. That amount should increase over time as the strategy generates profit.

## **How do vaults get added to Beefy.Finance?**

New potential vaults can be discussed in our Discord in the \#whiteboard channel. Our strategists then add the potential investment strategy to our strategy list. A priority is assigned to each new, potential strategy based on its APY, TVL and sustainability. Our developers/strategists then attack the list from top priority to bottom. The official forum is used for submitting actual [vault requests](https://forum.beefy.finance/c/vault-requests).

## **What’s your vault naming process?**

Each vault on the platform is named after the token that users can deposit in it. For example, the CAKE-BNB LP vault uses CAKE-BNB LP tokens for its investment strategy. A BTC vault uses the BTC token, etc.

Underneath the vault name, you can find the platform used for investing the token and farming its yields. For example, Uses: Venus means that that particular vault invests the token in Venus, a DeFi algorithmic money market and synthetic stablecoin protocol.

## **How do Venus vaults work?**

Venus is a decentralized marketplace for lenders and borrowers. By depositing your initial asset in the vault, Beefy deposits it into Venus and borrows against your token. This is done at a safe level of collateral. 

The borrowed tokens are then redeposited into the platform, and once again used as collateral to borrow more tokens. This cycle is repeated multiple times and $XVS \(the Venus platform token\) is farmed and sold to purchase more of your originally deposited assets. It is noteworthy that this "leveraged" multi lending and multi borrowing is only with the native token, so there is no liquidation risk due to price swings. Also, because it has to withdraw through the multi supply/borrow cycle, the transaction fee for Venus vaults is also almost 4x as high compared to other vaults. Venus vault APY's are mainly depended on Venus interest rates and the $XVS price.


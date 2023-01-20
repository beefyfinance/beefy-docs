---
description: One-click Beefy Vault Investing!
---

# How to use Beefy ZAP

<figure><img src="../../.gitbook/assets/1_click (1).png" alt=""><figcaption></figcaption></figure>

Beefy ZAP lets you create liquidity pool tokens and deposit into Beefy vaults with just one transaction. You no longer need to [manually add and remove liquidity](how-to-add-remove-liquidity.md)! Our ZAP tooling is a simple, quick and safe solution that eliminates the need for you to handle complicated LP tokens or obscure tokens, and even saves you from needing to leave the comfy environs of the Beefy app.

This page sets out a short tutorial on depositing and withdrawing into Beefy vaults with our different ZAP tools. For a higher-level conceptual explanation of our ZAP tooling, see the [#beefy-zap](../infographics.md#beefy-zap "mention") infographics section.&#x20;

{% hint style="info" %}
When using ZAP, always check your quote! While ZAP does protect you against market slippage (price changes between the time of order and time of fulfillment), it does **not** protect you against price impact (how much your transaction will change the price of the tokens in the liquidity pool). As a general rule, the smaller the liquidity of the asset, the larger the risk of price impact.
{% endhint %}

## Example Vault

{% hint style="info" %}
Last Update: January 2023. As the site is under constant development, the interface that you see may vary slightly from the below screenshots over time.
{% endhint %}

For the purposes of these tutorials, we will use Beefy's stMATIC-MATIC sLP vault for the Dystopia DEX on the Polygon blockchain. This vault supports both ZAP V1 and ZAP V2.&#x20;

<figure><img src="../../.gitbook/assets/Example Vault.png" alt=""><figcaption><p>The first step is to navigate to the relevant page for the vault you want to enter. For this tutorial, we will use the stMATIC-MATIC sLP vault for the Dystopia DEX on the Polygon blockchain.</p></figcaption></figure>

For those following along with this tutorial, just navigate to the relevant page for the vault you would like to enter. However, be aware that our ZAP tools are not available for every vault on every blockchain, so you should check at this stage whether the deposit token dropdown menu under _"Select token"_ does permit deposits with different assets. Make sure to also _"Connect Wallet"_ before trying to deposit.&#x20;

<figure><img src="../../.gitbook/assets/Example Select Token.png" alt=""><figcaption><p>The second step is to check which tokens you can use for the deposit. Without ZAP, you can only deposit the vault asset (e.g. the LP token at the top of the list). For V1, you can deposit the underlying assets of the vault (e.g. WMATIC, stMATIC or MATIC). For V2, you can deposit from a broader range of other assets (e.g. USDC, USDT, DAI, etc).</p></figcaption></figure>

Where ZAP V2 is available and you select a token that can be used for either V1 or V2, you will also be able to decide which tool to use. To switch between the two, look for the side arrow on the _"Beefy"_ header at the top of the _"Zap Route"_ box.

<figure><img src="../../.gitbook/assets/V2 - Provider Choice.png" alt=""><figcaption><p>Where both ZAP V1 and ZAP V2 are available for your chosen deposit asset, the Zap Route box allows you to select your preferred tool/provide to use. Click the side arrow on the "Beefy" header.</p></figcaption></figure>

The interface will then offer you to _"Select provider"_ and show all available ZAP providers and tools that you can use. In this case, you can select between ZAP V1 (or _"Beefy"_ shown below) or ZAP V2 (or _"Beefy x 1inch"_ shown below).

<figure><img src="../../.gitbook/assets/V2 - Select a provider.png" alt=""><figcaption><p>The interface allows you to select between using Beefy's own tool (using ZAP V1) or alternatively a swap aggregator like 1inch (using ZAP v2).</p></figcaption></figure>

## ZAP V1: Entering Vaults

To use ZAP V1 for deposits, ensure you've selected the _"Deposit"_ tab at the top of the box shown at the right hand side in the image below. Use the _"Select token"_ dropdown to select one of the underlying assets for the vault (e.g. WMATIC, stMATIC or MATIC), but not the main deposit token (e.g. stMATIC-MATIC sLP). You can then enter the amount of the token you wish to deposit from your wallet, or hit _"MAX"_ to deposit all of your tokens at once.

The UI will then display an estimate for how much of the main deposit token (e.g. stMATIC-MATIC sLP) you will receive and then deposit through the ZAP V1 workflow. Below, the _"Zap Route"_ box shows the different steps of the workflow and estimates for how much of each token will be received and used in each part of the transaction. Please note that it is impossible to know in advance exactly how much you will receive for the swaps in a ZAP workflow, so the final amounts may vary slightly from the estimates.

<figure><img src="../../.gitbook/assets/V1 - Deposit.png" alt=""><figcaption><p>For the ZAP V1 deposit workflow, select one of the underlying assets in the vault and input the quantity of that token you wish to deposit into the vault.</p></figcaption></figure>

To execute the proposed transaction, click on _"Deposit"_ or _"Deposit All"_, and your chosen wallet will trigger a transaction (possibly including an approval transaction first, if your allowance for the chosen asset is insufficient). Once you've executed the transaction, you will receive confirmation that the transaction has been submitted to the blockchain and that confirmation is pending. Once the transaction is validated on the blockchain, you will then receive confirmation that the transaction was completed, meaning the vault tokens will now be in your wallet.

And that's it! Deposit complete. Beefy ZAP V1 automatically created liquidity with Dystopia and deposited that liquidity into the Beefy vault. You can check [this guide](how-to-check-harvesting-compounding-rate.md) to see when our vaults will harvest rewards and compound for more LP tokens.

## ZAP V1: Exiting Vaults

In the reverse, you can withdraw by selecting the _"Withdraw"_ tab instead of _"Deposit"_. Use the _"Select token"_ dropdown to select one of the underlying assets of the vault (WMATIC, stMATIC, MATIC). You can then select the quantity of LP tokens that you wish to withdraw, or use the _"MAX"_ button to select all. Please note that the number of LP tokens is ordinarily different to the number of mooTokens or the number of underlying asset tokens you will receive, so the figure displayed can cause confusion.

The UI will then display an estimate for how much of the chosen withdrawal token (e.g. MATIC) you will receive through the ZAP V1 workflow. Below, the _"Zap Route"_ box shows the different steps and estimates for how much of each token will be received and used in each subtransaction. As with deposits, it is impossible to know in advance exactly how much you will receive for the swaps in a ZAP workflow, so the final amounts may vary slightly from the estimates.

<figure><img src="../../.gitbook/assets/V1 - Withdraw.png" alt=""><figcaption><p>For the ZAP V1 withdrawal workflow, select one of the underlying assets in the vault and input the number of LP tokens you wish to withdraw from the vault.</p></figcaption></figure>

To execute the proposed transaction, click on _"Withdraw"_ or _"Withdraw All"_, and your wallet will trigger another transaction (including approvals if needed). Once you've executed the transaction, you will receive confirmation that the transaction has been submitted to the blockchain and confirmation is pending. Once the transaction is validated on the blockchain, you will then receive confirmation that the transaction was completed, meaning the withdrawal tokens will now be in your wallet.

There you go! Withdrawal complete. Beefy ZAP V1 took all the steps to exit the vault, break the liquidity position and swap back to your chosen asset.

## ZAP V2: Entering Vaults

The ZAP V2 workflow is nearly identical to V1 from a user perspective. You can select any of the available tokens in the _"Select token"_ dropdown menu, and input the amount to deposit in the box to the right. Again the UI will show you estimates to the number of LP tokens you will receive for depositing into the vault, and each of the steps in the workflow (including the initial swaps to the underlying vault assets).

<figure><img src="../../.gitbook/assets/V2 - Deposit.png" alt=""><figcaption><p>For the ZAP V1 deposit workflow, select any of the available assets in the dropdown menu and input the quantity of that token you wish to deposit into the vault.</p></figcaption></figure>

As with the V1 process detailed above, simply hit _"Deposit"_ or _"Deposit All"_, run through the transaction on your wallet, and watch the transaction complete on the blockchain. Deposit complete! Beefy ZAP V2 took you from your chosen assets into the underlying vault assets, and then ran the same workflow as ZAP V1.&#x20;

## ZAP V2: Exiting Vaults

Similarly, the ZAP V2 withdrawal workflow is also near identical to V1 for users. As with deposits, you can now select any of the available tokens in the _"Select token"_ dropdown menu, and input the amount to deposit in the box to the right. Again the UI will show you estimates for how much of the chosen withdrawal token (e.g. ETH) you will receive, and how much of each token will be received for each step in the process.

<figure><img src="../../.gitbook/assets/V2 - Withdraw.png" alt=""><figcaption><p>For the ZAP V2 withdrawal workflow, select any of the available assets in the dropdown menu and input the number of LP tokens you wish to withdraw from the vault.</p></figcaption></figure>

As with the V1 process detailed above, simply hit _"Withdraw"_ or _"Withdraw All"_, run through the transaction on your wallet, and watch the transaction complete on the blockchain. Withdraw complete! Beefy ZAP V2 took you through all the steps in V1 to exit the vault and break the liquidity position, before swapping back to your chosen asset with V2.&#x20;

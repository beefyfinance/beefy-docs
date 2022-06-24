# Strategies

### What is a Vault Strategy?

Beefy's vault strategies are modular smart contracts that tell it what assets to farm, and where it should sell the farmed assets. Rewards are regularly harvested, swapped for the original vault asset, and deposited again for compound farming.

### How do LP Vaults work?

![](../../.gitbook/assets/Flow\_LP.png)

### How do Lending Vaults work?

![](../../.gitbook/assets/Flow\_single\_asset\_lending.png)

### **Who is in control of the strategies?**

Each vault and strategy link is hardcoded, and the code has been built to be immutable, so once they are released, they become unstoppable. No one can modify the vaults and strategies.

To release a new strategy on any asset, a new vault and strategy smart contract must be built.

### **How can I make a strategy?**

For now you can post and discuss your strategy in Beefy’s Discord in the #strategies channel. Detailing what it should buy/sell/farm and what the current APY is. There will be a template to help you get started.

### **What is APR and APY?**

APR reflects the simple interest rate over a year’s time, while APY describes the rate with the effect of compounding**.**

### **Is APY/365 the right way to determine daily gains?**

No, the effect of compounded interest is exponential, not linear. A daily compounded interest of 1% would yield 3678.34% a year.

### **How does Beefy optimize APY?**

Beefy automates the whole compounding process, making it close to optimal as possible. The compounding frequency depends on different variables in the system, like TVL, APR and strategy fees.

---
description: >-
  在本指南中，您将找到检查金库收获率和复合率所需的步骤。
---

# 如何检查金库的收获和复利率

Beefy Finance's [金库](../products/vaults.md), 或更具体地说，与金库相关的投资策略, 将通过将任意收益农场的奖励复合回更多该资产来自动增加您存入的资产数额。 这种收获奖励和复合的持续循环过程通常每天发生多次。 在本操作指南中，我们将引导您完成准确检查复利发生频率的步骤。

## 导览

注意：无论您选择哪条链，都可以使用 Beefy's [dashboard.beefy.finance](https://dashboard.beefy.finance) 来启动您的调查。

### 币安智能链 \(BSC\) 示例

让我们选择币安智能链上的 CAKE-BNB LP 金库来演示：

![截图摄于2021年5月5日](../../.gitbook/assets/cake-bnb-lp-2-5-2021.png)

#### 1. 前往 [dashboard.beefy.finance](https://dashboard.beefy.finance)

该仪表板会根据您的钱包 \(例如 MetaMask\) 所连接到的区块链网络来选择显示哪些统计数据和金库。 因此，如果它现在不在 BSC 上，只需将网络切换到该网络，仪表盘页面就会刷新，以显示 Beefy 在 BSC 上的统计数据和金库。

#### 2. 找到您想检查的金库合约，然后点击它，在 BscScan 区块浏览器中打开一个页面

![](../../.gitbook/assets/cake-bnb-lp-vault-address.png)

#### 3. 在 BscScan 页面上，打开 “Contract” 选项卡，然后打开 “Read Contract” 选项卡

![](../../.gitbook/assets/cake-bnb-lp-read-contract-tab.png)

#### 4. 向下滑动，找到策略合约，并点击它

![](../../.gitbook/assets/cake-bnb-lp-strategy-address.png)

#### 5. 点击 “Events” 选项卡查看已触发的策略事件

![](../../.gitbook/assets/harvest%20events%20inspection.png)

在 “StratHarvest” 事件中，LP 收益奖励被剔除，并复合到更多基础 LP（初始存入资产）中，然后重新存入 Beefy 金库。 正如时间戳记所反映的那样，这个 CAKE-BNB 金库大约每小时复合一次。

### 其他链 \(除了 Avalanche\)

Beefy 支持的每条链都可以通过与上述 BSC 相同的方法进行调查。 唯一的区别是不同的区块浏览器会被使用。 例如在 Polygon 上，PolygonScan 将打开（而不是BscScan)。

### Avalanche

上述 BSC 例子中显示的基本方法仍然适用，除了最后的关键步骤5。这要归功于 Avalanche 使用了不同的区块浏览器软件。在Avalanche的情况下，步骤5请切换到 “Transactions” 选项卡以查看触发的策略事件，如下图所示

![](../../.gitbook/assets/Avalanche-harvest-events.png)


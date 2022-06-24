---
description: >-
  Neste guia, você encontrará as etapas necessárias para verificar a taxa de
  colheita e composição de um cofre.
---

# Como verificar a taxa de colheita e composição de um cofre

Os cofres da Beefy Finance, ou mais especificamente a estratégia de investimento vinculada ao cofre, aumentarão automaticamente a quantidade de seu ativo depositado, compondo recompensas arbitrárias de fazenda de volta em mais desse ativo. Esse ciclo constante de coleta de recompensas e composição geralmente acontece várias vezes por dia. Neste How-To, orientamos você pelas etapas para verificar com precisão a frequência com que a composição ocorre.

## Walkthrough

NOTA: Não importa qual cadeia você escolha, você pode usar o dashboard.beefy.finance do Beefy para iniciar sua investigação.

### Binance Smart Chain (BSC) example

Vamos escolher o cofre CAKE-BNB LP na Binance Smart Chain para demonstrar:

![Screenshot taken 5 May 2021](../../.gitbook/assets/cake-bnb-lp-2-5-2021.png)

#### 1. Go to [dashboard.beefy.finance](https://dashboard.beefy.finance)

Este painel escolhe quais estatísticas e cofres serão exibidos com base na rede blockchain à qual sua carteira (por exemplo, MetaMask) está conectada. Portanto, se não estiver agora no BSC, basta alternar as redes para isso e a página do painel será atualizada para exibir as estatísticas e os cofres do Beefy no BSC.

#### 2. Encontre o contrato para o cofre que você deseja inspecionar e clique nele, abrindo uma página no explorador de blocos BscScan

![](../../.gitbook/assets/cake-bnb-lp-vault-address.png)

#### 3. Na página do BscScan, abra a guia "Contrato" e, posteriormente, a guia "Ler Contrato"

![](../../.gitbook/assets/cake-bnb-lp-read-contract-tab.png)

#### 4. Scroll down to find the strategy contract, and click on it

![](../../.gitbook/assets/cake-bnb-lp-strategy-address.png)

#### 5. Click on the Events tab to view the strategy events that have fired

![](<../../.gitbook/assets/harvest events inspection.png>)

The "StratHarvest" events are where LP-farming rewards are culled and in turn compounded into more of the underlying LPs, the initial deposited asset, and then redeposited into the Beefy vault. As the timestamps reflect, this CAKE-BNB vault compounds roughly once per hour.

### Other Chains (except Harmony, Celo, Cronos)

Each of the chains supported by Beefy may be investigated via the same method shown above for BSC. The only difference will be the block explorer opened. For example on Polygon, PolygonScan will open.

### Harmony, Celo, Cronos

The basic method shown in the BSC example above still applies, except for the last, key step 5. This owes to these chains using different block-explorer softwares. In these cases, step 5 switches to the Transactions tab to view the strategy events fired, as exemplified below

![](../../.gitbook/assets/Avalanche-harvest-events.png)

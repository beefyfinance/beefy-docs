---
description: >-
  Neste guia, você encontrará as etapas necessárias para verificar a taxa de
  colheita e composição de um cofre.
---

# Como verificar o ritmo de coleta e reinvestimento de um cofre

{% hint style="warning" %}
Este guia requer atualização. A interface atual da Beefy já apresenta na página de cada cofre quando que a última coleta foi feita, assim como um link para o contrato de estratégia do respectivo cofre.
{% endhint %}

Os cofres da Beefy, ou mais especificamente a estratégia de investimento vinculada ao cofre, aumentarão automaticamente a quantidade de seu ativo depositado, compondo recompensas arbitrárias de fazenda de volta em mais desse ativo. Esse ciclo constante de coleta de recompensas e composição geralmente acontece várias vezes por dia. Neste Guia Prático, orientamos você pelas etapas para verificar com precisão a frequência com que a composição ocorre.

## Guia passo-a-passo

NOTA: Não importa qual cadeia você escolha, você pode usar o [dashboard.beefy.finance](https://dashboard.beefy.finance/) da Beefy para iniciar sua investigação.

### Binance Smart Chain (BSC) example

Vamos escolher o cofre CAKE-BNB LP na Binance Smart Chain para demonstrar:

![Screenshot taken 5 May 2021](../../.gitbook/assets/cake-bnb-lp-2-5-2021.png)

#### 1. Go to [dashboard.beefy.finance](https://dashboard.beefy.finance)

Este painel escolhe quais estatísticas e cofres serão exibidos com base na rede blockchain à qual sua carteira (por exemplo, MetaMask) está conectada. Portanto, se não estiver agora na BSC, basta alternar as redes para isso e a página do painel será atualizada para exibir as estatísticas e os cofres da Beefy no BSC.

#### 2. Encontre o contrato para o cofre que você deseja inspecionar e clique nele, abrindo uma página no explorador de blocos BscScan

![](../../.gitbook/assets/cake-bnb-lp-vault-address.png)

#### 3. Na página do BscScan, abra a guia "Contrato" e, posteriormente, a guia "Ler Contrato"

![](../../.gitbook/assets/cake-bnb-lp-read-contract-tab.png)

#### 4. Desça a página para encontrar o contrato de estratégia e clique nele

![](../../.gitbook/assets/cake-bnb-lp-strategy-address.png)

#### 5. Clique na aba de Eventos para ver os eventos que a estratégia tem lançado

![](<../../.gitbook/assets/harvest events inspection.png>)

Os eventos "StratHarvest" são onde os rendimentos da LP são coletados e, por sua vez, compostos em mais das LPs subjacentes, o ativo inicialmente depositado, e depois depositado novamente no cofre da Beefy. Como as datas refletem, este cofre CAKE-BNB se compõe aproximadamente uma vez por hora.

### Outras Redes (exceto Harmony, Celo, Cronos)

Cada uma das redes apoiadas pela Beefy pode ser investigada através do mesmo método mostrado acima para a BSC. A única diferença será o _block explorer_ aberto. Por exemplo, na Polygon, o PolygonScan será aberto.

### Harmony, Celo, Cronos

O método básico mostrado no exemplo da BSC acima ainda se aplica, exceto para a última etapa-chave 5. Isto se deve a estas redes utilizando diferentes softwares de _block explorer_. Nestes casos, a etapa 5 muda para a guia _Transactions_ para visualizar os eventos estratégicos iniciados, como exemplificado abaixo:

![](../../.gitbook/assets/Avalanche-harvest-events.png)

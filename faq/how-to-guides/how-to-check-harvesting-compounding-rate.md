# Comment vérifier le rythme de collecte et de composition d'un coffre ?

Les [coffres](../../products/vaults.md) de Beefy Finance, ou plus précisément la stratégie d'investissement liée au coffre, augmentera automatiquement le montant de votre actif déposé en combinant les récompenses de la ferme de rendement pour obtenir plus de cet actif. Ce cycle constant de collecte de récompenses et de capitalisation se produit généralement plusieurs fois par jour. Dans ce mode d'emploi, nous vous expliquons comment vérifier précisément le rythme de composition.

## Cheminement

NOTE : Quelle que soit la chaîne que vous choisissez, vous pouvez utiliser le tableau de bord de Beefy [dashboard.beefy.finance](https://dashboard.beefy.finance) pour lancer votre démarche.

### Exemple de la Binance Smart Chain (BSC)

Choisissons le coffre CAKE-BNB LP sur la Smart Chain de Binance pour faire la démonstration :

![Capture d'écran prise le 5 mai 2021](../../.gitbook/assets/cake-bnb-lp-2-5-2021.png)

#### 1. Aller sur [dashboard.beefy.finance](https://dashboard.beefy.finance)

Ce tableau de bord choisit les statistiques et les coffres à afficher en fonction du réseau blockchain auquel votre portefeuille (par exemple MetaMask) est connecté. Donc, s'il n'est pas actuellement sur BSC, il suffit de changer de réseau pour que la page du tableau de bord se rafraîchisse et affiche les statistiques et les coffres de Beefy sur BSC.

#### 2. Trouvez le contrat pour le coffre que vous souhaitez inspecter, et cliquez dessus, ouvrant une page dans l'explorateur de blocs BscScan.

![](../../.gitbook/assets/cake-bnb-lp-vault-address.png)

#### 3. Sur la page BscScan, ouvrez l'onglet "Contract", puis l'onglet "Read Contract".

![](../../.gitbook/assets/cake-bnb-lp-read-contract-tab.png)

#### 4. Faites défiler l'écran pour trouver le contrat de la stratégie et cliquez dessus.

![](../../.gitbook/assets/cake-bnb-lp-strategy-address.png)

#### 5. Cliquez sur l'onglet Événements pour afficher les événements de la stratégie qui ont été déclenchés.

![](<../../.gitbook/assets/harvest events inspection.png>)

Les événements "StratHarvest" sont ceux où les récompenses des LP-farming sont récoltées et à leur tour composées en plus de LP sous-jacents, l'actif initial déposé, puis redéposées dans le coffre Beefy. Comme le montre l'horodatage, ce coffre CAKE-BNB est composé environ une fois par heure.

### Autres chaînes (sauf Harmony, Celo, Cronos)

Chacune des chaînes supportées par Beefy peut être étudiée en utilisant la même méthode que celle présentée ci-dessus pour BSC. La seule différence sera l'explorateur de bloc ouvert. Par exemple sur Polygon, PolygonScan s'ouvrira.

### Harmony, Celo, Cronos

La méthode de base présentée dans l'exemple BSC ci-dessus s'applique toujours, à l'exception de la dernière étape clé, la 5. Ceci est dû au fait que ces chaînes utilisent des logiciels d'exploration de blocs différents. Dans ces cas, l'étape 5 passe à l'onglet Transactions pour visualiser les événements de stratégie déclenchés, comme illustré ci-dessous :

![](../../.gitbook/assets/Avalanche-harvest-events.png)

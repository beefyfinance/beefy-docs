---
description: >-
  Dans ce guide, vous trouverez les étapes requises pour vérifier la fréquence
  de récolte et les intérêts composés d'un vault
---

# Comment vérifier la fréquence de récolte et les intérêts composés d'un vault

[Les vaults Beefy Finance](../../ecosystem-1/vaults.md), ou plus spécifiquement les stratégies d'investissement qui leur sont rattachées, augmenteront automatiquement le montant de l'actif déposé en transformant les récompenses de la ferme en ledit actif et en l'ajoutant au montant déposé par l'utilisateur. Ce cycle constant de récolte de récompenses, de composition des intérêts, se réalise habituellement plusieurs fois par jour. Dans ce guide, nous vous accompagnerons à travers les étapes à réaliser pour vérifier précisément la fréquence de ce processus.

## Guide

NOTE: Peu importe la chaine que vous choisissez, vous pouvez utiliser le [dashboard.beefy.finance](https://dashboard.beefy.finance) pour débuter votre recherche.

### Exemple sur la Binance Smart Chain (BSC)&#x20;

Nous utiliserons le vault CAKE-BNB LP sur la Binance Smart Chain pour la démonstration:

![Capture d'écran prise le 5 Mai 2021](../../.gitbook/assets/cake-bnb-lp-2-5-2021.png)

#### 1. Allez sur [dashboard.beefy.finance](https://dashboard.beefy.finance)

Ce tableau détermine quels vaults et statistiques à afficher en fonction du réseau sur lequel votre portefeuille est connecté. De ce fait, si votre portefeuille n'est pas connecté à la BSC actuellement, connectez-le et le tableau de bord se mettra à jour et affichera les statistiques et les vaults Beefy sur la BSC.

#### 2. Trouvez le contrat pour le vault qui vous intéresse, et cliquez dessus, afin d'ouvrir une page sur l'explorateur de blocs BscScan.

![](../../.gitbook/assets/cake-bnb-lp-vault-address.png)

#### 3. Sur la page BscScan, Ouvrez l'onglet "Contract" puis le sous-onglet "Read Contract"&#x20;

![](../../.gitbook/assets/cake-bnb-lp-read-contract-tab.png)

#### 4. Défilez vers le bas jusqu'à trouver le contrat  de la stratégie, et cliquez dessus

![](../../.gitbook/assets/cake-bnb-lp-strategy-address.png)

#### 5. Cliquez sur l'onglet "Events" pour voir les actions réalisées par la stratégie en place

![](<../../.gitbook/assets/harvest events inspection.png>)

Les "StratHarvest" sont les évènements où les intérêts sont récupérés, composés en plus de jetons de la Réserve de Liquidité (LP) sous-jacente, et ajoutés à votre dépôt initial.\
Comme nous le montre les dernières occurrences, ce processus se réalise approximativement une fois par heure sur ce vault.

### Les autres Chaines (à l'exception de Harmony, Celo et Cronos)

Toutes les chaînes supportées par Beefy peuvent être examinées de la même manière que celle présentée ci-dessus pour BSC. La seule différence sera l'explorateur de bloc ouvert. Par exemple, sur Polygon, PolygonScan s'ouvrira.

### Harmony, Celo, Cronos

La méthode présentée dans l'exemple BSC ci-dessus s'applique toujours, à l'exception de la dernière étape, la numéro 5. Ceci est dû au fait que ces chaînes utilisent des logiciels d'exploration de blocs différents. Ici, l'étape 5 requiert de cliquer sur l'onglet "Transactions" au lieu de "Events" afin de visualiser les événements stratégiques déclenchés, comme illustré ci-dessous:

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

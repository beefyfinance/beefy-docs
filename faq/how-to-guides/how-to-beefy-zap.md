# Comment utiliser Beefy Zap

Beefy ZAP vous permet de créer des jetons de fonds communs de liquidité et de faire des dépôts dans les coffres de Beefy en une seule transaction. Vous n'avez plus besoin [d'ajouter et de retirer manuellement des liquidités] (how-to-add-remove-liquidity.md) ! Beefy ZAP est une solution simple, rapide, bon marché et sûre qui élimine le besoin de manipuler les adresses des contrats de jetons ou même de quitter l'environnement confortable de l'application Beefy.

{% hint style="info" %}
Lorsque vous utilisez Zap, vérifiez toujours votre estimation ! Bien que Zap vous protège contre le glissement du marché (les changements de prix au moment de la commande et au moment de l'exécution), il ne vous protège **pas** contre l'impact du prix (dans quelle mesure votre transaction changera le prix des jetons dans le pool de liquidité).
{% endhint %}

## Entrer dans un coffre LP

Nous allons présenter Beefy ZAP pour le [BIFI-BNB LP vault](https://app.beefy.finance/#/bsc/vault/cakev2-bifi-bnb) de PancakeSwap :

![Capture d'écran réalisée le 30 mai 2021](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-rate.png)

En utilisant uniquement BNB comme actif d'entrée, nous laisserons Beefy ZAP créer les jetons BIFI-BNB LP et effectuer le dépôt dans le coffre.

### 1. Agrandir le coffre

Cliquez sur [BIFI-BNB LP](https://app.beefy.finance/vault/cakev2-bifi-bnb) ou n'importe où dans le champ du coffre pour le développer et voir les options de dépôt et de retrait.

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-dropdown.png)

### 2. Sélectionnez "BNB" dans le menu déroulant des dépôts.

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-zap-dropdown-menu.png)

BNB ne nécessite pas d'approbation pour être dépensé, car il s'agit de la monnaie native de la Smart Chain de Binance.

### 3. Entrez le montant de BNB et cliquez sur "Dépôt" (Deposit).

Nous avons actuellement 4,0685 BNB, et afin d'avoir assez pour payer les frais de transaction, nous utiliserons 4 BNB maximum.

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-deposit.png)

Et c'est tout ! Dépôt terminé :

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-deposit-done.png)

Beefy ZAP a automatiquement créé des liquidités chez Pancakeswap et a déposé des BIFI-BNB LP dans le coffre. Vous pouvez consulter [ce guide](how-to-check-harvesting-compounding-rate.md) pour savoir quand le coffre récoltera des récompenses et les composera pour obtenir plus de jetons BIFI-BNB LP.

## Sortie du coffre LP

Beefy ZAP permet également de retirer et d'enlever des jetons LP d'un coffre. Nous allons montrer comment retirer des jetons LP du coffre de BIFI-BNB et recevoir uniquement des BIFI.

### 1. Sélectionnez "BIFI" dans le menu déroulant des retraits.

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-bifi-withdraw.png)

### 2. Cliquez sur "Approuver" (Approve).

et confirmer la transaction.

### 3. Sélectionnez le montant de BIFI que vous souhaitez recevoir, ou utilisez tous les jetons déposés.

Cliquez sur le montant du jeton déposé, et retirez-le.

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-bifi-withdraw-all.png)

Et c'est tout ! Beefy ZAP a retourné 1,4794 BIFI dans notre portefeuille, que nous pouvons mettre en jeu dans le [BIFI Maxi vault](https://app.beefy.finance/#/bsc/vault/bifi-maxi) par exemple :

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-bifi-proof.png)

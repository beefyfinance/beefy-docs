# beJOE

### Qu'est-ce que JOE ?

JOE est le token natif de Trader Joe, une plateforme d'échange décentralisée native de la blockchain Avalanche. Il récompense ses détenteurs par une part des revenus de la plateforme et fait également office de jeton de gouvernance. JOE a un modèle de fourniture fixe et d'émissions décroissantes.

Les utilisateurs peuvent miser des JOE pour gagner des veJOE et recevoir des récompenses JOE boostées dans des Trader Joe Farms sélectionnés ainsi qu'un droit de vote au sein de la gouvernance.

## Qu'est-ce que beJOE ?

beJOE est une version Beefy de JOE qui permet de gagner des veJOE, en maximisant les émissions des coffres Beefy. Les détenteurs de beJOE gagnent 5% des émissions de ces coffres boostés ;

Le jeton est entièrement garanti 1:1 par JOE et peut être échangé contre des JOE en réserve. Cette réserve ne se remplit que lorsqu'un nouvel utilisateur dépose.

## Comment obtenir des beJOE ?

Vous pouvez échanger des beJOE sur le [ coffre ](https://app.beefy.finance/#/vault/beefy-beJoe) ou la [pool de gains](https://app.beefy.finance/#/vault/beefy-beJoe-earnings) de beJOE à un ratio de 1:1. Il n'y a pas de liquidité incitative pour les beJOE, mais une réserve de retrait.

![beJOE est miné et brûlé à un taux 1:1 avec JOE](<../../../.gitbook/assets/image (3) (1).png>)

## Comment fonctionne beJOE ?

Lorsque vous miné du beJOE, le contrat va immédiatement essayer de staker les JOE déposés en veJOE, sous réserve de deux conditions : (1) la réserve requise doit être maintenue ; et (2) le staking doit déclencher un bonus "Speed Up".

Si les réserves de JOE du contrat au moment de la création de la monnaie dépassent le montant de la réserve requise (qui est actuellement de 20% des JOE du contrat déjà placés dans le réseau veJOE), le contrat peut placer les JOE excédentaires dans le réseau veJOE. Si les réserves de JOE sont inférieures au montant de réserve requis, les JOE déposés seront ajoutés à la réserve pour couvrir le déficit actuel.

Le bonus "Speed Up" sur Trader Joe double le taux d'accumulation des veJOE pendant 14 jours après que les JOE ont été mis en jeu, à condition que le montant des JOE mis en jeu ajoute 5% (ou plus) au montant total des JOE déjà mis en jeu dans veJOE. Le contrat vérifie donc avant d'engager le solde disponible (comprenant à la fois le dépôt et tout excédent préexistant par rapport à la réserve obligatoire) si le seuil de 5% est atteint ou dépassé, et n'engage le solde disponible que si c'est le cas. Dans le cas contraire, il attend que d'autres dépôts de JOE augmentent le solde disponible avant de staker.

Une fois que le JOE du contrat est placé dans veJOE, il accumule automatiquement des récompenses veJOE. veJOE offre deux avantages : (1) des récompenses accrues dans certaines fermes Trader Joe ; et (2) des droits de vote (futurs) dans la gouvernance de Trader Joe. Le montant de chaque avantage est proportionnel au solde de veJOE détenu par le contrat, l'objectif étant donc d'accumuler le plus de veJOE possible.

Bien que les récompenses veJOE s'accumulent constamment sur les JOE misés par le contrat, les récompenses doivent être récoltées pour être ajoutées au solde de veJOE du contrat. Les récompenses sont automatiquement récoltées chaque fois qu'un JOE est placé en veJOE, ou manuellement par le contrat lorsque de nouveaux beJOE sont créés mais que les conditions de placement ne sont pas remplies.

## Comment puis-je gagner de l'argent avec mes beJOE ?

Une fois que vous détenez des beJOE, plusieurs options s'offrent à vous. Vous pouvez soit :

1. Placez-le dans le coffre du beJOE pour gagner plus de beJOE.
2. Placez-le dans le pool de gains beJOE pour gagner des JOE.

Dans chaque coffre Beefy d'une ferme Trader Joe qui est boosté pour les détenteurs de veJOE, 5% de la valeur de chaque récolte sera détournée vers le pool de récompense beJOE pour être versée aux détenteurs de beJOE. Cela reflète la valeur ajoutée par le contrat beJOE, qui rassemble les veJOE nécessaires pour booster ces coffres.

Comme les récompenses boostées dans les fermes Trader Joe sont payées en JOE, elles peuvent être reversées aux détenteurs de beJOE soit directement en JOE (par le biais du pool de gains), soit en composant des beJOE (par le biais du coffre) en produisant plus de beJOE avec les récompenses JOE.

## Comment fonctionne la stratégie beJOE ?

![](../../../.gitbook/assets/Flow\_beJOE.png)

## Mais qu'en est-il des frais ? 

Beefy s'efforce de maintenir des frais d'optimisation de rendement parmi les plus bas, et facture des frais standards sur ses coffres beJOE, plus un supplément de 5% livré directement aux stakers beJOE.

## Comment beJOE maintient-il sa parité ?

Il n'y a pas de liquidité fournie pour beJOE, donc il sera toujours à 1:1 avec JOE. Les utilisateurs peuvent brûler beJOE pour JOE tant que la réserve dure. Cette réserve ne se remplit que lorsqu'un nouvel utilisateur dépose.

Dans un scénario de dernier recours, tous les JOE verrouillés dans beJOE peuvent être déverrouillés et libérés dans la réserve. Les concurrents de Beefy n'ont pas cette possibilité. Cependant, cela mettrait également fin aux boosts disponibles pour les coffres de Beefy et aux récompenses versées dans le pool de récompenses de beJOE, et il est donc peu probable que cela soit déclenché.

### Puis-je voter avec beJOE ? 

Pas encore, mais beJOE implémente l'EIP-1271 (validation de signature pour les contrats), donc la future gouvernance/les pots-de-vin avec TraderJoe peuvent être organisés.
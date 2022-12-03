# beQI

## Qu'est-ce que le Qi ?

Qi est le token natif de Mai Finance, un protocole de dette collatéralisée natif de la blockchain Polygon. Mai Finance est régie par QiDao, pour lequel Qi est le token de gouvernance. Qi peut également être utilisé pour participer à une part des revenus du protocole. Qi a un modèle d'approvisionnement fixe et d'émissions décroissantes.

Les utilisateurs peuvent miser Qi pour gagner eQi et recevoir une part jusqu'à 4 fois plus élevée des revenus du protocole et du pouvoir de vote de la gouvernance.

## Qu'est-ce que le beQI ?

beQI est une version de Qi mise en jeu par Beefy pour gagner des eQi, pour augmenter la proportion des revenus du protocole Mai Finance que Beefy gagne et pour participer aux votes de la jauge d'incitation de la voûte.

Le jeton est entièrement soutenu 1:1 par des Qi et peut être échangé contre des Qi détenus en réserve. Cette réserve se remplit lorsque de nouveaux utilisateurs déposent (s'ils sont en dessous du montant de réserve requis à ce moment-là), ou le montant de réserve requis diminue progressivement au fur et à mesure que l'eQi du contrat diminue et se débloque.

## Comment obtient-on le beQI ?

Vous pouvez échanger des beQI sur le [coffre](https://app.beefy.finance/#/vault/beefy-beqi) ou les [earnings pools] (https://app.beefy.finance/#/vault/beefy-beqi-earnings) du beQI à un ratio de 1:1. Il n'y a pas de liquidité incitative pour les beQI, mais une réserve de retrait.

![Le beQI est fabriqué et brûlé à un taux de 1:1 avec le Qi](../../../.gitbook/assets/FSRYcQfXoAE2pL4.jpg)

## Comment fonctionne le beQI ?

Lorsque vous minez du beQI, le contrat va immédiatement essayer de miser et de verrouiller les Qi déposés en eQi, sous réserve que la réserve requise soit maintenue.

Si les réserves de Qi du contrat au moment de la fabrication dépassent le montant de la réserve requise (qui est actuellement de 20 % des eQi du contrat), le contrat peut miser tout Qi excédentaire en eQi. Si les réserves de Qi sont inférieures au montant de réserve requis, les Qi déposés seront ajoutés à la réserve pour couvrir le déficit actuel.

Une fois que les Qi du contrat sont mis en jeu et bloqués dans eQi, il reçoit deux avantages : (1) des récompenses accrues en termes de revenus hebdomadaires du protocole ; et (2) des droits de vote dans la gouvernance de QiDao et des votes de la jauge d'incitation du coffre. L'approche de Beefy pour voter pour beQI est détaillée [ci-dessous](beqi.md#je-peux-voter-avec-beqi).

Les revenus du protocole Mai Finance sont versés chaque semaine et comprennent actuellement 100% de toutes les récompenses d'exploitation provenant des revenus des frais de dépôt du protocole, qui sont utilisés pour l'exploitation de Qi-MATIC, ainsi que 30% des frais de remboursement de la dette pour tous les types de garanties (plus un bonus hebdomadaire de 25%). Les récompenses individuelles peuvent être multipliées par 4 lorsqu'un utilisateur possède le montant maximum d'eQi (c'est-à-dire qu'il a bloqué son Qi pendant 4 ans).

Comme le contrat beQI reverrouille perpétuellement ses dépôts de Qi, il s'efforce toujours d'obtenir le montant maximum de boost. Toutes les récompenses reçues sont ensuite distribuées à notre coffre Beefy beQI et à notre cagnotte pour le bénéfice des détenteurs de beQI.

## Comment puis-je gagner de l'argent avec mon beQI ?

Une fois que vous êtes en possession du beQI, vous avez plusieurs possibilités. Vous pouvez soit :

1. Placer votre argent dans le coffre de beQI pour gagner plus de beQI ; ou
2. L'investir dans le pool de gains beQI pour gagner des Qi.

Comme les revenus du protocole boosté par l'eQi sont payés en jetons Qi, ceux-ci peuvent être remboursés aux détenteurs de beQI soit directement en Qi (par le biais du earnings pool), soit en composant des beQI (par le biais du coffre) en produisant plus de beQI avec les récompenses Qi.

![Les beQI peuvent être composés automatiquement ou bloqués pour gagner des Qi](../../../.gitbook/assets/FQ-Hh7gWYAIJlEU.jpg)

## Comment fonctionne la stratégie beQI ?

![](../../../.gitbook/assets/Flow\_beQI.png)

## Mais qu'en est-il des frais ?

Beefy s'efforce de maintenir des frais d'optimisation de rendement parmi les plus bas, et facture des frais standards sur ses coffres beQI.

## Comment le beQI maintient-il sa parité ?

Il n'y a pas de liquidité fournie pour le beQI, donc il sera toujours à 1:1 avec le Qi. Les utilisateurs peuvent brûler des beQI pour des Qi tant que la réserve dure sans affecter la parité.

## Comment puis-je récupérer mon Qi ?

Tant que des jetons Qi sont disponibles dans la réserve, vous pourrez brûler vos jetons beQI existants (jusqu'au montant de la réserve) pour récupérer un montant équivalent de Qi.

Si la réserve ne contient pas suffisamment de jetons Qi pour faciliter le retrait demandé, vous ne pourrez retirer que jusqu'au montant de la réserve. Malheureusement, le verrouillage eQi ne comprend pas non plus de mécanisme de libération d'urgence. Dans ce cas, les détenteurs devront attendre que la réserve soit reconstituée.

Comme le montant de la réserve requise est lié à la quantité d'eQi détenue par le contrat, et que tous les soldes d'eQi diminuent au fil du temps à mesure que le temps restant jusqu'au déverrouillage diminue, le montant de la réserve requise diminuera aussi naturellement au fil du temps jusqu'à ce que le verrouillage des eQi soit prolongé. En tant que tel, et en supposant qu'aucun autre dépôt de Qi ne soit effectué pour reconstituer la réserve, le montant de la réserve requise diminuera progressivement au fil du temps, ce qui signifie que la quantité de Qi disponible pour le retrait augmentera constamment.

### Je peux voter avec beQI ?

Pas pour le moment. Tout le pouvoir de vote Qi est actuellement utilisé par Beefy pour voter dans la jauge d'incitation hebdomadaire des coffres. Les votes seront généralement dirigés vers les types de garanties Beefy (par exemple, mooBIFI Fantom), qui récompensent nos utilisateurs qui déposent leurs actifs Beefy comme garantie sur Mai Finance.

Lorsque nos types de garanties privilégiés ont peu de chances de se qualifier pour la jauge des incitations, nous pouvons également choisir d'accepter des pots-de-vin de parties externes. Le produit de tous les pots-de-vin est alors distribué directement à nos détenteurs de beQI. Si vous souhaitez proposer un pot-de-vin à Beefy, veuillez contacter l'équipe centrale sur Discord, Telegram ou Twitter pour en savoir plus.

![Le pouvoir de vote Qi de Beefy peut également être utilisé pour les pots-de-vin, qui sont directement versés aux détenteurs](../../../.gitbook/assets/beQI\_LIGHT.png)

# beJOE

{% hint style="info" %}
Le beJOE a été déprécié le 6 janvier 2023. Tous les beJOE peuvent être burn à 1 pour 1 pour du JOE, et Beefy ne charge plus de frais.
{% endhint %}

## Qu'est-ce que le JOE ? <a href="#what-is-joe" id="what-is-joe"></a>

Le JOE est le jeton natif de Trader Joe, un échangeur décentralisé sur la blockchain Avalanche. Il récompense ses détenteurs avec une part des revenus de la plateforme et sert également comme un jeton de gouvernance. Le JOE a une supply fixe et un modèle d'émission de jetons décroissant.

Les utilisateurs peuvent staker leurs JOE pour gagner du veJOE et recevoir des récompenses boostées en JOE dans certaines fermes sur la plateforme ainsi qu'un pouvoir de vote de gouvernance.

## Et le beJOE, qu'est ce que c'est ?

\-------------------------

Le beJOE est une version en escrow du jeton JOE créée par Beefy, staké pour accumuler du veJOE, maximisant les récompenses sur les vaults Beefy grâce au boost accordé par le veJOE. Les utilisateurs stakant du beJOE gagnent 5% des récompenses de ces vaults boostés.\
\
Le beJOE est entièrement backé à 1:1 en JOE et peut être échangé contre du JOE détenu en réserve. Cette réserve ne se remplit que lorsqu'un nouvel utilisateur dépose des JOE pour créer de nouveaux beJOE.\
\
\
beJOE is a Beefy-wrapped version of JOE staked to earn veJOE, maximizing emissions on boosted Beefy vaults. beJOE stakers earn 5% of emissions from those boosted vaults.

The token is fully backed 1:1 by JOE and can be redeemed for JOE held in reserve. This reserve only fills up when a new user deposits.\
\-------------------------

## Comment avoir du beJOE ?

Vous pouvez mint du beJOE en échange de jetons JOE sur la page du [vault beJOE](https://app.beefy.finance/vault/beefy-beJoe) ou du [Earnings Pool beJOE](https://app.beefy.finance/vault/beefy-beJoe-earnings) à un ratio de 1:1. Il n'y aura pas de prime de liquidité mise en place pour le beJOE, il y aura donc à la place une réserve de retrait.

DOC FROM ILLUST

![Le beJOE est minté et brûlé à 1:1 avec le JOE](broken-reference)

## Comment fonctionne le beJOE ?

Lorsque vous mintez du beJOE, le contrat intelligent tentera de staker les JOE déposés pour les transformer en veJOE, sous réserve de deux conditions :&#x20;

\----------------

* 1 - La réserve est alimentée
* 2 - Le staking de ces JOE doit déclencher le bonus "Speed Up"

(1) La réserve est alimentée ; et (2) Le staking de ces JOE doit déclencher le bonus  "Speed Up".

\----------------\
Au moment du mint de beJOE, si la réserve de JOE dépasse le montant requis (actuellement, 20% de la valeur totale dans le contrat déjà stakée en veJOE), le contrat peut staker le montant total de JOE déposé en veJOE. En revanche, si la réserve n'atteint pas le montant requis, le JOE déposé sera ajouté à celle-ci pour couvrir le déficit.

Le bonus "Speed ​​Up" sur Trader Joe double l'accumulation de veJOE pendant 14 jours après le staking de JOE, à condition que le montant de JOE staké ajoute 5% supplémentaires (ou plus) au montant total de JOE déjà staké en veJOE. Le contrat vérifie donc avant de staker les JOE déposés si le solde disponible (en prenant en compte le dépôt et tout excédent préexistant sur la réserve) atteindrait ou dépasserait les 5% supplémentaires, et ne stakera celui-ci que si tel est le cas. Sinon, il attend que d'autres dépôts de JOE viennent augmenter le solde disponible afin d'atteindre les 5% du montant total avant de les staker.

\-------------------

Une fois que le JOE du contrat est staké en veJOE, les récompenses en veJOE augmentent automatiquement. Par ailleurs, le veJOE offre 2 avantages :&#x20;

* 1 - Les récompenses sont améliorées sur certaines fermes de la plateforme Trader Joe
* 2 - Le droit de vote (dans un futur proche) pour la gouvernance du projet\
  \
  (1) Les récompenses sont améliorées sur certaines fermes de la plateforme Trader Joe ; et (2) le droit de vote (dans un futur proche) dans la gouvernance de Trader Joe.&#x20;

Le montant de chaque avantage est proportionnel au montant de veJOE détenu dans le contrat, l'objectif est donc d'accumuler autant de veJOE que possible.

\-------------------

Bien que le montant de veJOE augmente constamment grâce au JOE staké dans le contrat, les récompenses doivent être récoltées pour elles aussi être ajoutées au solde total de veJOE du contrat. Les récompenses sont automatiquement récoltées chaque fois que du JOE est staké en veJOE, ou lorsque du beJOE est minté mais que les conditions de staking citées ci-dessus ne sont pas remplies.

## Que faire avec mon beJOE? <a href="#what-can-i-do-with-bejoe" id="what-can-i-do-with-bejoe"></a>

Une fois en possession de beJOE, il existe plusieurs possibilités. Vous pouvez soit:

* 1 - Le staker dans le vault beJOE pour gagner plus de beJOE;
* 2 - Le staker dans le Earnings Pool beJOE pour recevoir du JOE.

Dans chaque vault Beefy en lien avec une ferme Trader Joe qui est boosté pour les possesseurs de veJOE, 5% de chaque récolte sera envoyé vers le pool de récompenses beJOE afin d'être distribué aux possesseurs de beJOE. Il s'agit là de la valeur ajoutée du contrat beJOE, qui permet de rassembler les veJOE nécessaires pour booster ces vaults.

Les récompenses boostées sur ces fermes Trader Joe étant payées en JOE, elles peuvent être versées aux possesseurs de beJOE soit directement en JOE (via le Earnings Pool), soit en beJOE (via le vault beJOE) en mintant plus de beJOE avec les JOE initiaux.

## Comment fonctionne notre stratégie beJOE ?

DOC FROM ILLUST

![](broken-reference)

## Qu'en est-il des frais ? <a href="#but-what-about-fees" id="but-what-about-fees"></a>

Beefy s'efforce de maintenir des frais d'optimisation du rendement parmi les plus bas. Ils se résument à des frais de performance classiques sur les vaults beJOE plus 5% qui sont directement redistribués aux possesseurs de beJOE.

## Comment le beJOE garde-t-il son Peg ?

Aucune liquidité n'étant fournie pour le beJOE, celui-ci sera donc toujours égal à 1:1 JOE. Les utilisateurs peuvent brûler leur beJOE pour récupérer du JOE tant que la réserve est alimentée. Celle-ci ne se remplit que lorsqu'un nouvel utilisateur y dépose du JOE.

En dernier recours, tous les JOE verrouillés dans le contrat beJOE peuvent être déverrouillés et ajoutés à la réserve. Les concurrents de Beefy n'ont pas cette possibilité. Cependant, cela mettrait également fin aux boosts disponibles pour les vaults Beefy et aux récompenses du pool de récompenses beJOE, il est donc peu probable que ce recours soit utilisé.

## Puis-je voter avec mon beJOE? <a href="#vejoe-model" id="vejoe-model"></a>

Pas encore, mais le beJOE implémente l'EIP-1271 (validation de signature pour les contrats), afin que la future gouvernance/les bribes de TraderJoe puissent être organisés.

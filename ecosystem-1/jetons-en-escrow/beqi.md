# beQI

## Qu'est-ce que le Qi? <a href="#what-is-qi" id="what-is-qi"></a>

Le Qi est le jeton natif de Mai Finance, un protocole de dette collatéralisée créé sur Polygon. Mai Finance est régie par QiDao, le Qi en étant le jeton de gouvernance. Le Qi peut également être utilisé afin de toucher une part des revenus du protocole. Le jeton possède une supply fixe et un modèle d'émission de jetons décroissant.&#x20;

Les utilisateurs peuvent staker des Qi pour gagner des eQi et recevoir une part jusqu'à 4 fois plus élevée des revenus du protocole et du pouvoir de vote de la gouvernance.

## Et le beQI, qu'est ce que c'est ?

Le beQI est une version en escrow du jeton Qi créée par Beefy, qui est staké pour générer de l'eQi, afin d'augmenter la proportion des revenus du protocole Mai Finance que Beefy récupère et pour participer aux votes d'attributions des gauges pour son vault.&#x20;

Le jeton est entièrement backé à 1:1 par des Qi et peut être échangé contre des Qi gardés en réserve. Cette réserve se remplit lorsque de nouveaux utilisateurs déposent des jetons (si elle est en dessous du montant requis prévu à ce moment-là). Le montant de réserve requis diminue progressivement au fur et à mesure que l'eQi du contrat diminue et se débloque.

## Comment obtenir du beQI?

Vous pouvez mint des beQI sur la du [vault beQI](https://app.beefy.finance/#/vault/beefy-beqi) ou du [Earnings Pool beQI](https://app.beefy.finance/#/vault/beefy-beqi-earnings) à un ratio de 1:1. Il n'y aura pas de prime de liquidité pour les beQI, mais une réserve de retrait. Les Beni sont mintés et brûlés à un taux de 1:1 avec les Qi.

<figure><img src="https://1519541449-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MJZ0tXJc-hdgL-YTlPk-887967055%2Fuploads%2FkyqZbxUrF9R9jDD0kyan%2FFSRYcQfXoAE2pL4.jpg?alt=media&#x26;token=8a2c13d9-8817-49df-aa61-594a439c7d09" alt=""><figcaption><p>Le beQI est mint and burn à 1:1 rate avec le Qi</p></figcaption></figure>

## Comment fonctionne le beQI ? <a href="#how-does-beqi-work" id="how-does-beqi-work"></a>

Lorsque vous mintez du beQI, le contrat tente immédiatement de staker et de verrouiller les Qi déposés en eQi, à condition que la réserve minimum soit alimentée.\
\
Si les réserves de Qi du contrat au moment du mint dépassent le montant requis (qui est actuellement de 20 % des eQi du contrat), le contrat peut déposer tout Qi excédentaire en eQi. Si les réserves de Qi sont inférieures au montant de réserve requis, les Qi déposés seront ajoutés à la réserve pour couvrir le déficit actuel.\
\
Une fois que le Qi du contrat est staké et verrouillé en eQi, il reçoit deux avantages :&#x20;

\----------------

* 1 - Des récompenses accrues en termes de revenus hebdomadaires du protocole
* 2 - Du droit de vote dans la gouvernance de QiDao et sur l'attribution des gauges.

(1) des récompenses accrues en termes de revenus hebdomadaires du protocole ; et (2) Du droit de vote dans la gouvernance de QiDao et sur l'attribution des gauges.

\----------------

L'approche de Beefy quant à l'utilisation du pouvoir de vote disponible avec le beQI est détaillée [ci-dessous](beqi.md#can-i-vote-with-beqi).\
\
Le protocole Mai Finance verse des revenus hebdomadaires qui incluent actuellement 100% de toutes les récompenses de farming provenant des frais de dépôt du protocole, utilisés pour farm du Qi-MATIC, ainsi que 30% des frais de remboursement de la dette pour tous les types de collatéraux (plus un bonus hebdomadaire de 25%). Les récompenses individuelles peuvent être multipliées jusqu'à 4 fois lorsqu'un utilisateur possède la quantité maximale de eQi (c'est-à-dire qu'il a bloqué ses jetons Qi pour 4 ans).

Mai Finance protocol revenues are paid out weekly, and currently include 100% of all farming rewards from the protocol's deposit fee revenue, \
\-----which is used to farm Qi-MATIC,----- together with 30% of the debt repayment fees for all collateral types (plus a 25% weekly bonus). Individual rewards can be boosted by up to 4x where a user has the maximum amount of eQi (i.e. has locked their Qi for 4 years).&#x20;

Comme le contrat beQI renouvelle continuellement son dépôt et blocage de Qi, cela lui permet de toujours obtenir le boost maximum. Toutes les récompenses reçues sont ensuite redistribuées dans notre vault beQI et dans le Earnings Pool beQI pour les holders de beQI.

## Que faire avec mon beQI? <a href="#how-can-i-earn-with-my-beqi" id="how-can-i-earn-with-my-beqi"></a>

Une fois en possession de beQI, il existe plusieurs possibilités. Vous pouvez soit :

* 1 - Le staker dans le vault beQI pour gagner plus de beQI;
* 2 - Le staker dans le Earnings Pool beQI pour recevoir du Qi.

Comme les revenus boostés du protocole eQi sont payés en jetons Qi, ceux-ci peuvent être reversés aux détenteurs de beQI soit directement en Qi (par le biais du Earnings Pool), soit en composant des beQI (par le biais du vault beQI) en mintant plus de beQI avec les récompenses en Qi.

<figure><img src="https://1519541449-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MJZ0tXJc-hdgL-YTlPk-887967055%2Fuploads%2Fi4o7fgMyxF6N10pQLHux%2FFQ-Hh7gWYAIJlEU.jpg?alt=media&#x26;token=d59bc5b9-4565-4b45-84cc-bf61e59b0510" alt=""><figcaption></figcaption></figure>

## Comment fonctionne la stratégie beQI ? <a href="#how-does-the-beqi-strategy-work" id="how-does-the-beqi-strategy-work"></a>

<figure><img src="https://1519541449-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MJZ0tXJc-hdgL-YTlPk-887967055%2Fuploads%2Fy1FHQYjthQsWSHzQHcw2%2FFlow_beQI.png?alt=media&#x26;token=7aaf5ac7-d944-464c-a61b-39bde97d3b3c" alt=""><figcaption></figcaption></figure>

## Qu'en est-il des frais ? <a href="#but-what-about-fees" id="but-what-about-fees"></a>

Beefy s'efforce de maintenir des frais d'optimisation de rendement parmi les plus bas. Sur les vaults beQI, il s'agit uniquement de frais standard.

## Comment le beQI garde-t-il son Peg ? <a href="#how-does-beqi-keep-its-peg" id="how-does-beqi-keep-its-peg"></a>

Il n'y a pas de liquidité fournie pour le beQI, donc il sera toujours égal à 1:1 Qi. Les utilisateurs peuvent brûler leur beQI pour récupérer du Qi tant que la réserve est alimentée, sans en affecter le peg.

## Comment puis-je récupérer mon Qi ? <a href="#how-can-i-get-my-qi-back" id="how-can-i-get-my-qi-back"></a>

Tant que des jetons Qi seront disponibles dans la réserve, vous pourrez brûler vos jetons beQI existants (jusqu'au montant total de la réserve) pour récupérer une quantité équivalente de Qi.

Lorsque la réserve ne contient pas suffisamment de jetons Qi pour effectuer le retrait demandé, vous ne pourrez retirer que le montant disponible dans celle-ci. Malheureusement, le verrouillage des jetons eQi ne comprend pas non plus de mécanisme de libération d'urgence. Dans ce cas, les détenteurs devront attendre que la réserve soit réapprovisionnée.

Le montant minimum de la réserve étant lié à la quantité d'eQi détenue par le contrat, et que le solde d'eQi diminue au fil du temps à mesure que le temps restant jusqu'au déverrouillage diminue, le montant de la réserve requise diminuera aussi naturellement au fil du temps jusqu'à ce que le verrouillage des eQi soit prolongé. Ainsi, et en supposant qu'aucun autre dépôt de Qi ne soit effectué pour reconstituer la réserve, le montant de la réserve requise diminuera progressivement au fil du temps, ce qui signifie que la quantité de Qi disponible pour le retrait augmentera constamment.

## Puis-je voter avec mon beQI? <a href="#can-i-vote-with-beqi" id="can-i-vote-with-beqi"></a>

Pas pour le moment. Tout le pouvoir de vote Qi est actuellement utilisé par Beefy afin de voter pour l'attribution de la gauge hebdomadaire pour son vault. Les votes seront généralement dirigés vers les types de collatéraux Beefy (par exemple, le mooBIFI Fantom), qui récompensent nos utilisateurs qui déposent leurs actifs Beefy comme collatéral sur Mai Finance.&#x20;

Lorsque nos collatéraux privilégiés sont peu susceptibles de remporter le vote pour la gauge, nous pouvons également choisir d'accepter des bribes de groupes externes. Le montant de toutes les bribes est alors distribué directement à nos holders de beQI. Si vous souhaitez proposer une bribe à Beefy, veuillez contacter l'équipe Core sur Discord, Telegram ou Twitter pour en savoir plus.

<figure><img src="https://1519541449-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MJZ0tXJc-hdgL-YTlPk-887967055%2Fuploads%2FzF5iviArHtMFXLFHy2or%2FbeQI_LIGHT.png?alt=media&#x26;token=dc7ea0fe-e2d0-42eb-b0f2-924736b798d5" alt=""><figcaption><p>Le pouvoir de vote en Qi de Beefy peut également être utilisé pour des bribes, qui sont ensuite reversés aux stakers de beQI</p></figcaption></figure>

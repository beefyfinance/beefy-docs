# Gouvernance

Beefy est gérée comme une Organisation Autonome Décentralisée (DAO), ce qui signifie qu'elle est contrôlée et dirigée par un réseau décentralisé de contributeurs et de membres de la communauté, qui permettent à Beefy de fonctionner de manière autonome. Cette page décrit comment le processus de gouvernance derrière notre DAO fonctionne, et comment vous pouvez vous y impliquer.

## Comment est régi Beefy ?

En tant qu'organisation décentralisée, Beefy est fièrement régi par les holders du jeton $BIFI. Il s'agit de nos fondateurs, des contributeurs principaux et de l'ensemble de la Cowmunauté, ainsi que de quelques détenteurs externes. La plupart des décisions importantes que prend Beefy sont soumises au vote des possesseurs de $BIFI, y compris la fixation de nos frais, le financement du protocole et de ses contributeurs, la façon dont nous commercialisons Beefy et la direction que nous devrions prendre pour certaines décisions. Considérez nos holders de BIFI comme des membres de l'assemblée législative de Beefy.

Le mécanisme clé à cet égard est le vote de la gouvernance, qui s'effectue sur notre [page Snapshot](https://vote.beefy.finance/). Les détenteurs de BIFI ont le droit de soumettre des propositions (s'ils détiennent au moins 1 $BIFI) et de voter pour celles-ci. La discussion de toutes les propositions est activement encouragée sur nos canaux de médias sociaux. En particulier, nous vous encourageons à vous diriger vers les canaux #🏛-proposals et #🗣-proposal-discussion sur le serveur [Discord Beefy](https://discord.com/invite/yq8wfHd). Dans le canal #🏛-proposals, vous trouverez un espace dédié à la discussion de propositions individuelles, tandis que le canal #🗣-proposal-discussion sert de forum plus général.

En outre, les opérations quotidiennes de Beefy sont régies par notre équipe de contributeurs principaux, qui joue le rôle de l'aile exécutive et est chargée d'exécuter la volonté de nos holders. Comme pour toute organisation en pleine croissance, il est impossible de faire passer chaque décision par une gouvernance formelle, c'est pourquoi notre équipe Core s'est vue déléguer l'autorité nécessaire pour s'occuper du protocole. \
\----\
Cela dit, toute décision prise par l'équipe Core peut être remise en question par le biais d'un vote de gouvernance, afin de garantir que la communauté ait toujours le dernier mot sur la gestion de la DAO.\
\
That said, any area of Core's decision-making can instead be raised through governance voting, to ensure that they may be held to account.\
\----

## Comment prendre part à la gouvernance ?

En détenant simplement du $BIFI. même s'ils sont placés dans un Earnings Pool ou dans un vault BIFI Maxi, un utilisateur gagne le droit de créer des propositions et de voter pour celles-ci en possédant notre jeton. L'importance et la puissance de vote d'un participant sont dérivés du montant de $BIFI en sa possession. Le raisonnement derrière cela s'ensuit que ceux qui détiennent plus de $BIFI sont plus investis dans le projet et ont donc une plus grande motivation à ce que la plateforme elle-même réussisse et prospère.

Vous pouvez voir les propositions et y voter en vous rendant sur [vote.beefy.finance](https://vote.beefy.finance/#/).

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>La page de Snapshot présente nos propositions de gouvernance et de vote.</p></figcaption></figure>

## **Comment voter ?**

Pour voter, vous devez posséder du $BIFI, qu'il soit simplement dans votre portefeuille ou staké dans les Earnings Pools ou dans les BIFI Maxi. Vous n'avez pas besoin de déstaker pour voter. La puissance de vote est basé sur le montant de $BIFI détenu par chaque votant.

Pour soumettre votre vote, il vous suffit de vous rendre sur notre [page Snapshot](https://vote.beefy.finance/), de connecter votre portefeuille, puis de vous rendre sur une proposition ouverte sur laquelle vous souhaitez voter. Vous y trouverez une interface pour "voter" en sélectionnant vos options préférées et en cliquant sur "voter". Vous devrez ensuite signer une transaction via votre portefeuille pour soumettre officiellement votre vote.

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption><p>Recherchez la case "Cast your vote" sur une page de proposition ouverte pour y participer.</p></figcaption></figure>

## Comment puis-je déléguer mon vote ?

Vous pouvez déléguer votre vote sur la BNB Chain en interagissant directement avec [le contrat DelegateRegistry](../documentation-pour-les-developpeurs-anglais/contrats-tiers/contrat-delegateregistry.md). Un tutoriel complet sur la manière de déléguer est disponible [ici](../documentation-pour-les-developpeurs-anglais/contrats-tiers/contrat-delegateregistry.md#delegation-walkthrough). Veuillez noter que, en raison de notre outil de Snapshot sur mesure, vous devez déléguer sur la BNB Chain pour que votre délégation soit effective. Les délégations sur d'autres chaînes peuvent être enregistrées dans le contrat DelegateRegistry correspondant, mais ne seront pas reconnues par notre outil.

## Comment devenir un délégué ?

Si vous souhaitez représenter la Cowmunauté en devenant un délégué vers lequel les autres peuvent rediriger leur pouvoir de vote, vous pouvez le faire en nous contactant et en fournissant votre nom et votre adresse de portefeuille publique. Une liste complète des délégués actuels proposant de représenter vos intérêts est maintenue dans ce [Google Sheet](https://docs.google.com/spreadsheets/d/1sJH4jg3eEEJDpbws55qUmzPeLDiDuL\_5OAQobSn7m2Y/edit#gid=0). Nous recommandons aux personnes souhaitant devenir délégués de fournir le plus d'informations possible sur ce document, dans l'intérêt des utilisateurs souhaitant déléguer.

## Comment les votes sont-ils comptabilisés ?

Pour chaque proposition, un snapshot de la blockchain est pris au moment de sa publication et est utilisé pour calculer le nombre de jetons $BIFI détenus par chaque votant. Ce pouvoir de vote est verrouillé à partir du moment où la proposition est publiée, de sorte que vous ne pouvez pas acheter plus de $BIFI pour influencer un vote en cours.

Via notre page Snapshot, les propositions peuvent prendre un certain nombre de formats différents, et chacun d'entre eux prend en compte les votes à sa manière. Les différents formats sont :

* Le vote basique - les votants peuvent soit approuver, soit rejeter, soit s'abstenir. La majorité (en l'absence d'abstention) l'emporte.
* Le vote à choix unique - les votants peuvent choisir un choix parmi plusieurs. L'option ayant obtenu la plus grande proportion de votes l'emporte.
* Le vote pondéré - les votants peuvent répartir leur pouvoir de vote entre plusieurs choix.  L'option ayant obtenu le plus grand nombre de voix l'emporte.
* Vote quadratique - Comme le vote pondéré, mais avec un pouvoir de vote ajusté de manière logarithmique, de sorte que les petits votants ont plus de pouvoir de vote par jeton que les grands votants. L'option ayant la plus grande proportion de pouvoir de vote l'emporte.
* Le vote par ordre de préférence - les votants peuvent sélectionner plusieurs options par ordre de préférence, les votes étant ensuite comptabilisés en éliminant l'option ayant reçu le moins de votes de préférence, et en réaffectant ces votes à la préférence suivante, jusqu'à ce qu'il ne reste qu'une seule option.

{% hint style="info" %}
Veuillez noter que pour tous les votes de gouvernance Beefy qui incluent une option "abstention", un vote d'abstention sera compté pour le quorum (si applicable) pour cette proposition, mais sera interprété comme une voix pour le choix ayant le plus de votes lorsque les votes d'abstention sont ignorés. Lorsqu'un quorum est appliqué et qu'il n'est atteint que par l'inclusion des votes "abstention", cela reste une proposition valide et le résultat sera accepté.&#x20;

Le snapshot peut reconnaître le résultat d'un vote comme "abstention" s'il en reçoit le plus grand nombre de votes. Malgré cela, le résultat sera en fait l'option ayant reçu le plus de votes après l'abstention.

Par exemple, le résultat de la proposition de remboursement Permissionless 2022 ci-dessous.
{% endhint %}

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>Si l'abstention est l'option la plus votée, la deuxième option la plus votée après celle-ci sera adopté.</p></figcaption></figure>

## Quel est le quorum pour le vote ?

Pour s'assurer que les propositions qui ne suscitent pas beaucoup d'intérêt ne sont pas adoptées par défaut, le Snapshot inclut une option de quorum de vote, selon laquelle une proposition doit recevoir plus d'une proportion spécifique du total des votes disponibles pour être considérée comme valide.

Au moment de la rédaction de ce document, aucun quorum formel n'a été adopté par Beefy, bien que notre page Snapshot fasse référence à un quorum de 800 $BIFI (équivalent à 1% de l'offre totale de $BIFI) pour chaque proposition. Lorsqu'un vote n'atteint pas le quorum mentionné sur la page Snapshot, **il sera quand même adopté** si un quorum n'a pas été formellement mis en place.

## Comment puis-je créer une proposition ?

Les propositions peuvent être créées si le soumissionnaire détient ou stake au moins 1 $BIFI. Il suffit de se rendre sur le site [https://vote.beefy.finance/#/](https://vote.beefy.finance/#/) et de cliquer sur «Nouvelle proposition».

Chaque proposition est constituée d'une question à poser à la communauté, ainsi que de choix sur lesquels les autres peuvent voter en réponse à votre question. Il suffit ensuite de fixer une date de début et de fin pour votre proposition et de la publier.

## Quels types de propositions existe-t-il ?

Au fur et à mesure que notre processus de gouvernance s'est développé, nous avons adopté un certain nombre de formats de propositions à des fins différentes. En voici quelques-uns :

* Beefy Improvement Proposals - (BIP) - la forme de proposition par défaut, pour une question visant à améliorer le protocole d'une manière ou d'une autre.
  * Cela inclut maintenant des propositions pour les [paiements récurrents des contributeurs](https://docs.beefy.finance/community-governance/contributor-compensation#reoccurring-payments).
* Beefy Signally Proposals - (BSP) - une proposition alternative, non contraignante, visant à établir un consensus parmi les détenteurs de $BIFI, ou à démontrer leurs opinions/préférences.
* [Demandes de fonds / Paiements rétroactifs](https://docs.beefy.finance/community-governance/contributor-compensation#retroactive-payments) - une simple demande de financement auprès de la trésorerie de Beefy pour un axe de travail particulier ou des contributeurs. Il s'agit généralement d'une forme de dépense, plutôt que d'un investissement.
* [BeefyGrants ](https://docs.beefy.finance/community-governance/contributor-compensation#beefygrants)- une demande plus détaillée de financement de la trésorerie, généralement liée à un grand projet qui nécessite un financement et une contribution importants, mais qui vise à fournir des revenus futurs ou des économies de coûts à Beefy (il s'agit donc d'un investissement, plutôt que d'une dépense).

## Comment se protéger contre les votes malveillants ?

Ce n'est un secret pour personne, la gouvernance ouverte comporte une série de risques, notamment des votes malveillants visant à pirater le protocole ou à porter atteinte à notre Cowmunauté. Pour se protéger contre cette possibilité, notre équipe Core modère activement le processus de gouvernance, en cherchant à éliminer toute proposition potentiellement nuisible.

\----------------------------------------\
Cela inclut les propositions qui sont :&#x20;

* Clairement nuisibles ou malveillantes ;
* Injustes, impossibles ou fondamentalement irrationnelles ;
* Qui ne laissent pas suffisamment de temps pour voter ;
* Qui manquent de clarté ou de compréhensibilité pour être exécutées ;

(1) clairement nuisibles ou malveillantes ; (2) injustes, impossibles ou fondamentalement irrationnelles ; (3) qui ne laissent pas suffisamment de temps pour voter ; ou (4) qui manquent de clarté ou de compréhensibilité pour être exécutées. \
\----------------------------------------\
Il peut également s'agir de tentatives visant à forcer l'adoption d'une proposition en changeant le système de vote ou les paramètres en cas d'échec du vote (par exemple, en passant par le vote quadratique pour contourner les grands détenteurs de $BIFI).

## Où puis-je trouver les détails des précédents votes ?

Les votes récents sont stockés sur notre [page Snapshot](https://vote.beefy.finance/#/). À la fin de l'année 2021, Beefy est passé d'un fork Snapshot personnalisé fonctionnant exclusivement sur Binance Smart Chain (BSC) à une instance moderne de Snapshot, capable de supporter chacune des chaînes où Beefy est présent. En raison de cette transition, les propositions se terminant avant le début de l'année 2022 n'ont pas été reportées sur le nouveau site. Au lieu de cela, une copie archivée du site original a été préservée.

{% hint style="info" %}
Notez que l'accès au site archivé est disponible à l'adresse [https://vote-archive.beefy.finance/](https://vote-archive.beefy.finance/#/). Celui-ci nécessite que les utilisateurs connectent leur portefeuille à la fois au site et au réseau BSC Mainnet pour afficher les propositions historisées. Le site de vote actuel est disponible à l'adresse [https://vote.beefy.finance/#/](https://vote.beefy.finance/#/).
{% endhint %}

Alternativement, nous avons créé et maintenons un [référentiel de propositions](https://docs.beefy.finance/community-governance/proposal-repository) dans nos docs, où vous pouvez accéder rapidement à toutes les propositions majeures sur l'un ou l'autre site de vote à travers celui-ci.

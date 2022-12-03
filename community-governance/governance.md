# Gouvernance

Beefy est gérée comme une organisation autonome décentralisée (DAO : decentralised autonomous organisation), ce qui signifie qu'elle est contrôlée et dirigée par un réseau décentralisé de contributeurs et de membres de la communauté, qui permettent à Beefy de fonctionner de manière autonome. Cette page décrit comment le processus de gouvernance derrière notre DAO fonctionne, et comment vous pouvez vous impliquer.

## Comment est gouverné Beefy ?

En tant qu'organisation décentralisée, Beefy est fièrement gouverné par nos détenteurs de jetons $BIFI. Il s'agit de nos fondateurs, des contributeurs principaux et de l'ensemble de Cowmoonité, ainsi que de quelques détenteurs externes. La plupart des décisions importantes que prend Beefy sont soumises au vote de nos détenteurs de $BIFI, y compris la fixation de nos frais, le financement du protocole et de ses contributeurs, la façon dont nous commercialisons Beefy et la direction que nous devrions prendre pour certaines décisions. Considérez nos détenteurs de BIFI comme des membres de l'assemblée législative de Beefy.

Le mécanisme clé est le vote de la gouvernance, qui se déroule sur notre page [Snapshot](https://vote.beefy.finance/). Les détenteurs de BIFI ont le droit de soulever des propositions (s'ils détiennent au moins 1 $BIFI) et de voter sur celles-ci. La discussion de toutes les propositions est activement encouragée sur nos canaux de médias sociaux. En particulier, nous vous encourageons à vous rendre sur les canaux #🏛-proposals et #🗣-proposal-discussion sur le serveur [Beefy Discord](https://discord.gg/yq8wfHd). Dans les fils de discussion du canal #🏛-proposals, vous trouverez un espace dédié à la discussion de propositions individuelles, ou #🗣-proposal-discussion sert de forum plus général.

En outre, les opérations quotidiennes de Beefy sont régies par notre équipe de contributeurs Core, qui joue le rôle de l'aile exécutive et est chargée d'exécuter la volonté de nos détenteurs de BIFI. Comme pour toute organisation en pleine croissance, il est impossible de faire passer chaque décision par une gouvernance formelle, c'est pourquoi notre équipe Core s'est vue déléguer l'autorité nécessaire pour s'occuper du protocole. Cela dit, tout domaine de prise de décision du Core peut être soulevé par le biais d'un vote de gouvernance, afin de s'assurer qu'ils peuvent être tenus responsables.

## **Comment puis-je participer à la gouvernance?**

En détenant simplement des jetons $BIFI, même s'ils sont placés dans le pool de jetons natifs Earnings Pool ou dans le coffre BIFI Maxi, un utilisateur gagne le droit de créer des propositions et de voter. L'influence et le pouvoir de vote sont fonction du nombre de jetons $BIFI détenus par le participant. Le raisonnement est le suivant : ceux qui détiennent plus de jetons $BIFI sont plus investis dans le projet et ont donc plus intérêt à ce que la plateforme elle-même réussisse et prospère.

En plus de voter pour vous-même, vous pouvez également vous inscrire pour participer en tant que délégué, afin que d'autres personnes puissent vous déléguer leur pouvoir de vote et l'inclure dans votre propre vote. Grâce à ce mécanisme, les voix de confiance de la communauté peuvent renforcer leur soutien avec un petit effort de la part de leurs partisans. Il permet également à ceux qui manquent de temps de s'assurer que leur $BIFI participe à la gouvernance, sans avoir à s'engager dans chaque proposition. Voir ci-dessous et la page [delegateregistry-contract.md](../developer-documentation/third-party-contracts/delegateregistry-contract.md "mention") pour plus de détails.

Vous pouvez voir les propositions et voter vous-même en vous rendant sur [vote.beefy.finance](https://vote.beefy.finance/).

![La page de Snapshot de Beefy abrite nos propositions de gouvernance et le vote](<../.gitbook/assets/image (3).png>)

## **Comment puis-je voter?**

Pour voter, vous devez détenir des jetons $BIFI, que vous pouvez soit détenir simplement dans votre portefeuille, soit placer dans le Earnings Pool ou les coffres BIFI Maxi. Vous n'avez pas besoin de retirer votre mise pour voter. Le pouvoir de vote est basé directement sur le montant de jetons $BIFI que chaque votant détient.

Pour soumettre votre vote, il vous suffit de vous rendre sur notre [page Snapshot](https://vote.beefy.finance/), de connecter votre portefeuille à Snapshot, puis de vous rendre sur une proposition ouverte sur laquelle vous souhaitez voter. Vous y trouverez une interface pour "voter" en sélectionnant vos options préférées et en cliquant sur "voter". Vous devrez ensuite signer une transaction via votre portefeuille pour soumettre officiellement votre vote.

![Cherchez la case "Votez" sur une page de proposition ouverte pour participer](<../.gitbook/assets/image (2).png>)

## Comment puis-je déléguer mon vote ?

Vous pouvez déléguer votre vote sur n'importe quelle chaîne en interagissant directement avec le contrat DelegateRegistry de cette chaîne. Un tutoriel complet sur la manière de déléguer est disponible dans la page [delegateregistry-contract.md](../developer-documentation/third-party-contracts/delegateregistry-contract.md "mention") à l'adresse [#cheminement-de-la-delegation](../developer-documentation/third-party-contracts/delegateregistry-contract.md#cheminement-de-la-delegation "mention").

Veuillez noter que vous devez déléguer séparément pour chaque chaîne sur laquelle vous détenez $BIFI. Sinon, votre délégation ne sera effective que sur les chaînes sur lesquelles vous avez soumis votre/vos appel(s) de délégation.

## Comment puis-je devenir un délégué ?

Si vous souhaitez représenter la Cowmoonity en agissant en tant que délégué vers lequel les autres peuvent diriger leur pouvoir de vote, vous pouvez le faire en nous contactant et en fournissant votre nom et l'adresse de votre portefeuille public. Une liste complète des délégués actuels proposant de représenter vos intérêts est maintenue dans cette [Feuille Google](https://docs.google.com/spreadsheets/d/1sJH4jg3eEEJDpbws55qUmzPeLDiDuL\_5OAQobSn7m2Y/edit?usp=sharing). Nous recommandons aux délégués potentiels de fournir autant d'informations que possible sur cette feuille, dans l'intérêt des utilisateurs qui pourraient les déléguer.

### Comment les votes sont-ils comptés ?

Pour chaque proposition, un instantané de la blockchain est pris au moment de la publication et utilisé pour calculer combien de jetons $BIFI sont détenus par chaque votant. Ce pouvoir de vote est verrouillé à partir du moment où il est affiché, de sorte que vous ne pouvez pas acheter plus de jetons $BIFI pour influencer un vote en direct.

Grâce à notre page Snapshot, les propositions peuvent prendre un certain nombre de formes différentes, chacune d'entre elles pondérant les votes de manière légèrement différente. Les différentes options comprennent :

* Le vote de base - les électeurs peuvent soit approuver, soit rejeter, soit s'abstenir, la majorité (en l'absence d'abstentions) remportant le vote.
* Le vote à choix unique - les électeurs peuvent choisir un choix parmi plusieurs, l'option ayant obtenu la plus grande proportion de voix l'emportant.
* Le vote pondéré - les électeurs peuvent répartir leur pouvoir de vote entre plusieurs choix, l'option ayant la plus grande proportion de votes l'emportant.
* Vote quadratique - vote pondéré, mais avec un pouvoir de vote ajusté de façon logarithmique, de sorte que les petits électeurs ont plus de pouvoir de vote par jeton que les grands électeurs. L'option avec la plus grande proportion de pouvoir de vote gagne.
* Vote par ordre de préférence - les électeurs peuvent sélectionner plusieurs options par ordre de préférence, les votes étant ensuite comptés en éliminant l'option ayant reçu le moins de votes de préférence, et en réaffectant ces votes à la préférence suivante, jusqu'à ce qu'il ne reste qu'une seule option.

{% hint style="info" %}
Veuillez noter que pour tous les votes de gouvernance Beefy qui incluent une option "abstention", un vote d'abstention sera compté pour le quorum (si applicable) pour cette proposition, mais sera autrement interprété comme un vote pour le côté qui a le plus de votes, en ignorant les votes d'abstention. Lorsqu'un quorum est appliqué et qu'il n'est atteint que par l'inclusion des votes "abstention", cela reste une proposition valide et le résultat sera accepté.

Snapshot peut reconnaître le résultat d'un vote comme étant "abstention" lorsqu'il reçoit le plus de votes, bien que le résultat soit en fait l'option avec le plus de votes autrement. Voir par exemple le résultat de la proposition de remboursement de Permissionless 2022 ci-dessous.
{% endhint %}

<figure><img src="../.gitbook/assets/1.png" alt=""><figcaption><p>Si l'abstention est le résultat le plus voté, le résultat le plus voté sera adopté.</p></figcaption></figure>

## Quel est le quorum pour le vote ?

Pour s'assurer que les propositions qui ne suscitent pas beaucoup d'intérêt ne sont pas adoptées par défaut, Snapshot inclut une option de quorum de vote, où une proposition doit recevoir plus qu'une proportion spécifiée du total des votes disponibles dans n'importe quelle direction pour être considérée comme valide.

Au moment de la rédaction de cet article, aucun quorum formel n'a été adopté par Beefy, bien que notre page Snapshot fasse référence à un quorum de 800 $BIFI (équivalent à 1% de l'offre totale de $BIFI) pour chaque proposition. Lorsqu'un vote n'atteint pas le quorum mentionné dans le Snapshot, **il sera quand même adopté** à moins qu'un quorum ait été formellement mis en place.

## **Comment créer une proposition?**

Les propositions peuvent être créées si le déposant détient ou met en jeu au moins 1 $BIFI. Il suffit de se rendre sur le site [https://vote.beefy.finance/#/](https://vote.beefy.finance/#/) et de cliquer sur Nouvelle proposition.

Chaque proposition est composée d'une question à poser à la communauté, ainsi que de choix sur lesquels les autres peuvent voter en réponse à votre question. Il suffit de fixer une date de début et de fin pour votre proposition et de la publier.

## Quels types de propositions existe-t-il ?

Au fur et à mesure que notre processus de gouvernance s'est développé, nous avons adopté un certain nombre de formes de propositions différentes à des fins spécifiques. Il s'agit notamment de :

* Les propositions d'amélioration (BIP : Beefy Improvement Proposals) - la forme de proposition par défaut, pour une question visant à améliorer le protocole d'une certaine manière.
  * Cela inclut maintenant des propositions pour les [paiements récurrents des contributeurs](../community/contributor-compensation.md#reoccurring-payments).
* Propositions de signalement Beefy (BSP : Beefy Signally Proposals) - une proposition alternative, non contraignante, visant à établir un consensus parmi les détenteurs de jetons $BIFI, ou à démontrer leurs opinions/préférences.
* [Demandes de fonds / paiements rétroactifs](../community/contributor-compensation.md#retroactive-payments) - une simple demande de financement de la trésorerie de Beefy pour un travail particulier ou des contributeurs. Il s'agit généralement d'une forme de dépense, plutôt que d'un investissement.
* [Propositions de subventions](../community/contributor-compensation.md#beefygrants) - une demande plus détaillée de financement de la trésorerie, généralement liée à un grand projet qui nécessite un financement et une contribution importants, mais qui vise à fournir des revenus futurs ou des économies de coûts à Beefy (il s'agit donc d'un investissement, plutôt que d'une dépense).

## Comment se protéger contre les votes malveillants ?

Ce n'est un secret pour personne que la gouvernance ouverte comporte une série de risques, notamment des votes malveillants visant à attaquer le protocole ou à porter atteinte à notre Cowmoonité. Pour se protéger contre cette possibilité, notre équipe centrale modère activement le processus de gouvernance, en cherchant à supprimer toute proposition potentiellement nuisible.

Cela inclut les propositions qui sont : (1) clairement nuisibles ou malveillantes ; (2) injustes, impossibles ou fondamentalement irrationnelles ; (3) qui ne laissent pas suffisamment de temps pour voter ; ou (4) qui manquent de clarté ou de compréhensibilité pour être exécutées.  Il peut également s'agir de tentatives visant à forcer l'adoption d'une proposition en changeant le système de vote ou les paramètres en cas d'échec du vote (par exemple, en passant à un vote quadratique pour contourner les grands détenteurs de jetons $BIFI), ou en laissant trop peu de temps pour le vote.

## Où puis-je trouver les détails des votes passés ?

Les votes récents sont stockés sur notre [page Snapshot](https://vote.beefy.finance/). Fin 2021, Beefy est passé d'un fork Snapshot personnalisé fonctionnant exclusivement sur Binance Smart Chain (BSC) à une instance moderne de Snapshot, capable de supporter chacune des chaînes de Beefy. En raison de cette transition, les propositions se terminant avant le début de l'année 2022 n'ont pas été reportées sur le nouveau site. Au lieu de cela, une copie archivée du site original a été préservée.

{% hint style="info" %}
Notez que l'accès au site de vote archivé de Beefy est disponible sur [https://vote-archive.beefy.finance/](https://vote-archive.beefy.finance/). Le site archivé nécessite que les utilisateurs connectent leur portefeuille à la fois au site et au BSC Mainnet pour afficher les propositions historiques. Le site de vote actuel est disponible en direct à l'adresse [https://vote.beefy.finance/#/](https://vote.beefy.finance/#/).
{% endhint %}

Alternativement, nous avons préparé et maintenons un [dépôt de propositions](../community/proposal-repository.md) ici dans nos docs, où vous pouvez rapidement accéder à toutes les propositions majeures sur l'un ou l'autre site de vote à travers notre histoire.
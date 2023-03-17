# Jetons en Escrow

## Qu'est-ce qu'un jeton en Escrow?

Un mécanisme de dépôt en escrow est un système où une partie détient les droits ou les actifs d'une autre partie en costudy pour elle, en attendant la réalisation d'une condition spécifique (par exemple, la réception en toute sécurité des biens achetés avec ces actifs). Dans la DeFi, les mécanismes de dépôt en escrow impliquent de fournir vos jetons à une tierce partie (par exemple, Beefy) pour qu'elle puisse mettre en œuvre certaines fonctionnalités avec ces jetons en votre nom. Ainsi, les mécanismes de dépôt en escrow sont généralement construits autour d'une tokenomique spécifique aux jetons que vous possédez.

Pour illustrer cette définition, nous allons prendre le jeton FTM sur Fantom Opera, qui peut être staké pour sécuriser la blockchain en validant de manière équitable et sûre ses transactions. La tokenomique permet aux utilisateurs de staker leurs jetons afin de gagner des frais de transaction de la part des utilisateurs de la blockchain, donnant au jeton natif la capacité de générer de la valeur pour son détenteur. Cependant, le staking est complexe et comporte des inconvénients, tels que le verrouillage de vos jetons, qui vous empêche de les échanger. De ce fait, des solutions de dépôt en escrow ont été créées par des tiers (comme le beFTM de Beefy) pour vous permettre d'accéder aux avantages de la tokenomique (c'est-à-dire de pouvoir staker vos jetons FTM) sans avoir à gérer vous-même le staking, tout en pouvant échanger les intérêts touchés grâce aux jetons verrouillés.

## Qu'est-ce que le « Vote Escrow » ?

Un Vote Escrow (que l'on peut traduire par "Dépôt en escrow de vote") est une forme de tokenomique de dépôt en escrow qui vise à récompenser les holders long terme des jetons de gouvernance d'un protocole avec plus de pouvoir de vote, pour favoriser leurs intérêts en matière de gouvernance par rapport aux holders court terme. Pour cela, le protocole propose aux holders de staker et bloquer leurs jetons de gouvernance en échange d'un rendement provenant de ses revenus, limitant ainsi leur capacité à utiliser ou échanger ces jetons. En faisant cela, les holders débloquent les droits de vote (qui ne sont autrement pas disponibles pour les holders) ou augmentent leur pouvoir de vote existant, généralement en fonction de la durée pendant laquelle leurs jetons sont stakés/bloqués. Ce pouvoir de vote est souvent utilisé pour diriger l'économie du protocole correspondant, par exemple en faisant voter les utilisateurs sur la manière de distribuer les jetons émis en tant qu'incentives parmi les réserves de liquidité du protocole.

Le système de Vote Escrow a été introduit pour la première fois dans la DeFi par la conception des jetons CRV et veCRV de Curve Finance (sur Ethereum). Il existe d'autres projets qui utilisent des mécanismes de Vote Escrow comme le veCVX de Convex (sur Ethereum), le veBAL de Balancer (sur Ethereum), le veFXS de Frax (sur Ethereum), le eQI de Mai Finance (sur Polygon), le veJOE de Trader Joe (sur Avalanche), le vePTP de Platypus (sur Avalanche), ou bien le veVELO de Velodrome (sur Optimism).

## Qu'est-ce qu'un jeton « Vote-escrowed » ?

Dans la plupart des systèmes de Vote Escrow, le pouvoir de vote des utilisateurs n'est pas lié de manière linéaire au nombre de jetons de gouvernance possédés, mais dépend plutôt de facteurs tels que la durée de temps pendant laquelle les jetons sont bloqués. De ce fait, les jetons Vote-Escrowed (que l'on pourrait traduire par "jeton de dépôt en escrow de vote") ont été créés pour refléter la quantité de pouvoir de vote qu'un utilisateur a en fonction de ses jetons stakés/bloqués. Ces jetons se nomment les "**veTokens**". Les facteurs impactant le pouvoir de vote évoluant au fil du temps, la quantité de veTokens de l'utilisateur évoluera également, bien que le nombre de jetons de gouvernance possédés reste le même.

Il est important de noter que les veTokens ne sont pas toujours des jetons ERC20, et qu'ils ne sont \
donc pas nécessairement reçus et détenus par les utilisateurs dans leur portefeuille. Cela est dû à la conception des "**veTokenomics**" qui permet l'évolution constante du pouvoir de vote en fonction de différents facteurs (Comme par exemple la durée de blocage des jetons). Si les veTokens étaient émis aux utilisateurs, ils nécessiteraient une réévaluation constante pour maintenir un registre équitable, ce qui ajouterait beaucoup de frais et une complexité supplémentaire à leur fonctionnement. De plus, les veTokenomics ayant été conçus pour encourager la détention long terme de jetons de gouvernance en les récompensant d'une part des revenus du protocole, l'implémentation du pouvoir de vote dans un format ERC20 transférable pourrait compromettre cet objectif, car elle permettrait aux holders long terme d'échanger leurs récompenses de la même manière que les holders court terme.

<details>

<summary>Exemple de veTokenomics</summary>

Imaginons qu'un votant détienne un jeton EXMPL, émis par Example DAO et qui lui donne droit à une voix dans le processus de gouvernance existant de Example DAO.

Example DAO met ensuite en place un système de Vote Escrow, où le votant peut staker et bloquer ses jetons pendant une période allant jusqu'à 2 ans, et recevra un boost de pouvoir de vote égal au nombre d'années restantes de blocage.

Dans une situation classique, le jeton EXMPL du votant lui conférerait un pouvoir de vote pour la gouvernance égal à un veEXMPL, soit une voix dans le processus de gouvernance.

Le votant pourrait par la suite choisir de bloquer son jeton EXMPL pendant 2 ans et recevrait donc un total de 3 veEXMPL (1 pour le jeton EXMPL + 2 de bonus de blocage), ce qui lui donnerait 3 voix au lieu d'une.

Après un an de vote boosté, la période de blocage du votant ne sera plus que de 1 an, réduisant ainsi son nombre de veEXMPL à 2 et donc son pouvoir de vote pour la gouvernance à 2 voix. L'utilisateur peut décider à tout moment de prolonger son blocage jusqu'à 2 ans pour augmenter son nombre de veEXMPL, ou décider de sortir du blocage en attendant une année supplémentaire, puis de vendre ses jetons.

</details>

## Qu'est-ce qu'un jeton « Beefy-Escrowed » ?

Les jetons Beefy-Escrowed (en français, "jetons de dépôt en escrow de Beefy"), les "**beTokens**", sont des jetons wrap conçus et implémentés par Beefy pour permettre à nos utilisateurs d'accéder aux avantages des tokenomiques d'escrow tout en leur permettant d'échanger leurs récompenses perçues en jetons de gouvernance de nos partenaires. Pour cela, nous avons mis en place un contrat intelligent qui peut conserver les jetons de gouvernance, les bloquer avec le protocole partenaire pour la durée maximum possible et accéder aux avantages du modèle de dépôt en escrow. De plus, nous combinons ces fonctionnalités avec l'émission d'un nouveau jeton ERC20, nommé beToken, que les utilisateurs peuvent ensuite échanger pour sortir du blocage à tout moment.&#x20;

Chaque beToken est conçu de manière unique et inclus des fonctionnalités adaptées en fonction des différents modèles de veTokenomics de nos protocoles partenaires.&#x20;

\----

Ces fonctionnalités peuvent être :&#x20;

* Des réserves de retrait ;
* Une liquidité possible sur un échangeur décentralisé ;
* Un prix fixe ou fluctuant ;
* Un processus d'allocation de vote mis en place par Beefy sur le protocole sous-jacent ;
* La gestion de bribes par Beefy ou par ses utilisateurs ;
* Des boosts pour les vaults Beefy associés.

Ces fonctionnalités peuvent être : des réserves de retrait, une liquidité DEX soutenue, un prix fixe ou flottant, un processus de vote Beefy pour allouer des votes sur le protocole sous-jacent, des pots-de-vin dirigés par l'utilisateur ou par Beefy, Des boosts pour les vaults Beefy associés.

\----

Beefy soutient toujours les beTokens avec des vaults sur la plateforme, où vous pouvez staker vos beTokens pour obtenir un rendement. Cela peut prendre la forme d'un vault beToken autocomposant pour obtenir plus de beTokens ou d'un Earnings Pool pour obtenir plus de jetons de gouvernance sous-jacents. Dans tous les cas, vous pouvez retirer vos beTokens à tout moment puis les échanger pour sortir de votre position.

## Quels sont les différents jetons Beefy-Escrowed ?

Dans cette section, nous fournissons une page couvrant chacun des différents beTokens que nous opérons actuellement. Au moment de la rédaction de ce document, voici la liste des jetons disponibles :

{% content-ref url="beftm.md" %}
[beftm.md](beftm.md)
{% endcontent-ref %}

{% content-ref url="binspirit.md" %}
[binspirit.md](binspirit.md)
{% endcontent-ref %}

{% content-ref url="bejoe.md" %}
[bejoe.md](bejoe.md)
{% endcontent-ref %}

{% content-ref url="beqi.md" %}
[beqi.md](beqi.md)
{% endcontent-ref %}

{% content-ref url="bevelo.md" %}
[bevelo.md](bevelo.md)
{% endcontent-ref %}

{% content-ref url="beopx.md" %}
[beopx.md](beopx.md)
{% endcontent-ref %}

## Où puis-je en savoir plus ?

Cette section fournit des détails complets sur les designs de chacun de nos beTokens existants. Vous pouvez également poser des questions spécifiques sur nos beTokens en nous contactant sur [le serveur Discord de Beefy](https://discord.com/invite/yq8wfHd).

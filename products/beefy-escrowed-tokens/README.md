# Jeton Beefy-escrowed

## Qu'est-ce qu'un Escrow ?

Un escrowed est un mécanisme par lequel une partie détient les droits ou les actifs d'une autre partie en garde pour elle, en attendant la réalisation d'une condition spécifique (par exemple, la réception sûre des biens achetés avec ces actifs). Dans la DeFi, les escrowed impliquent que vous fournissiez vos jetons à un tiers (par exemple Beefy) pour lui permettre d'implémenter certaines fonctionnalités avec ces jetons en votre nom. En tant que tels, tous les escrowed sont typiquement construits autour d'une conception économique des jetons (**"tokenomic "**) dans les jetons que vous détenez.

Par exemple, le jeton natif d'une blockchain (ex. le FTM de Fantom) peut être utilisé à des fins de jalonnement pour sécuriser une blockchain en validant ses transactions de façon équitable et sécuritaire. La conception des jetons permet aux utilisateurs de bloquer leurs jetons afin de gagner des frais de transaction de la part des utilisateurs de la blockchain, ce qui donne au jeton natif la capacité de gagner ou de générer de la valeur pour le détenteur. Cependant, la mise en jeu est compliquée et comporte des inconvénients, comme le verrouillage de vos jetons et la limitation de votre capacité à les échanger. C'est pourquoi des solutions d'escrowed (par exemple Beefy's beFTM) ont été créées pour vous permettre d'accéder aux avantages de la tokenomique (c'est-à-dire le blocage de votre FTM) sans avoir à gérer vous-même le blocage, et tout en vous permettant de continuer à échanger vos intérêts dans les jetons bloqués.

## Qu'est-ce que le vote Escrow ?

Un mécanisme de vote escrow est une forme de conception de la séquestration des jetons qui vise à récompenser les détenteurs à long terme des jetons de gouvernance d'un protocole avec plus de pouvoir de vote, afin de favoriser leurs intérêts en matière de gouvernance par rapport aux détenteurs à court terme. Pour ce faire, les détenteurs investissent et verrouillent généralement leurs jetons de gouvernance avec le protocole (généralement pour un retour sur les bénéfices du protocole), limitant ainsi leur capacité à vendre leurs jetons. Ce faisant, le détenteur débloque des droits de vote (qui ne lui sont pas accessibles autrement) ou augmente son pouvoir de vote existant, généralement en fonction de la durée pendant laquelle ses jetons sont mis en réserve/verrouillés. Ce pouvoir de vote est souvent utilisé pour orienter l'économie du protocole concerné, par exemple en faisant voter les utilisateurs sur la manière de distribuer les jetons nouvellement émis comme incitations supplémentaires parmi les pools de liquidité du protocole.

Le système d'entiercement des votes a été introduit dans la DeFi par la conception des jetons CRV et veCRV de Curve Finance (hébergés sur Ethereum). Parmi les autres exemples notables de conception de vote escrow, citons veCVX de Convex (Ethereum), veBAL de Balancer (Ethereum), veFXS de Frax (Ethereum), eQI de Mai Finance (Polygon), veJOE de Trader Joe (Avalanche), vePTP de Platypus (Avalanche), veVELO de Velodrome (Optimism).

## Qu'est-ce qu'un jeton bloqué pour le vote Escrow ?

Dans la plupart des systèmes de vote escrow, le pouvoir de vote des utilisateurs n'est pas lié de façon linéaire au nombre de jetons de gouvernance détenus, mais dépend plutôt de facteurs tels que la durée de verrouillage des jetons. C'est pourquoi le concept de jetons verrouillés (**"veTokens "**) a été développé, afin de refléter la quantité de pouvoir de vote qu'un utilisateur détient grâce à ses jetons placés/verrouillés. Comme les facteurs qui ont un impact sur le pouvoir de vote évoluent dans le temps, le nombre de veTokens de l'utilisateur changera également, même si le nombre de jetons de gouvernance détenus reste le même.

Un point de confusion est que - malgré le nom - les veTokens ne sont pas toujours représentés par un jeton ERC20, et ne sont donc pas nécessairement reçus et détenus par les utilisateurs dans leur portefeuille. En effet, l'économie des veTokens ("**veTokenomics**") est conçue pour permettre au pouvoir de vote de changer constamment en fonction des facteurs d'entrée (par exemple, la durée de la période de blocage). Si les veTokens étaient délivrés aux utilisateurs, ils nécessiteraient un rebasage constant (ajustement de l'offre totale et des avoirs nominaux de tous les utilisateurs) afin de maintenir un registre équitable, ce qui ajouterait beaucoup de complexité et de coûts supplémentaires. En outre, les veTokenomics ayant été conçus pour encourager la détention à long terme de jetons de gouvernance, la mise en œuvre du pouvoir de vote dans un format ERC20 transférable pourrait compromettre cet objectif, car elle permettrait aux détenteurs à long terme d'échanger leurs intérêts de la même manière que les détenteurs à court terme.

<details>

<summary>Exemple de l'économie d'un veToken</summary>

Imaginons qu'un votant détienne 1 jeton EXMPL, émis par Example DAO et qui lui donne droit à un vote entier dans le processus de gouvernance existant de Example DAO.

Example DAO met ensuite en œuvre un concept de séquestre de vote, où l'électeur peut mettre en jeu et verrouiller ses jetons pour une durée allant jusqu'à 2 ans, et recevra une augmentation du pouvoir de vote égale au nombre d'années restantes dans son verrou.

Dans des circonstances normales, le jeton EXMPL de l'électeur lui conférerait un pouvoir de vote en matière de gouvernance égal à un veEXMPL standard, soit une voix entière dans le processus de gouvernance.

L'électeur peut alors choisir de verrouiller son jeton 1 EXMPL pendant 2 ans et recevoir 3 veEXMPL (1 base + 2 bonus), ce qui équivaut à 3 votes entiers.

Après un an de vote boosté, la période de blocage du détenteur aurait diminué à 1 an, réduisant ainsi son bonus et son veEXMPL de sorte qu'il ait droit à 2 votes. L'utilisateur peut décider à tout moment de prolonger son blocage jusqu'à 2 ans pour augmenter son veEXMPL, ou il peut décider de sortir du blocage en attendant une année supplémentaire, puis de vendre ses jetons.

</details>

## Que sont les jetons Beefy-escrowed ?

Les jetons Beefy-escrowed ("**beTokens**") sont des jetons intermédiaires, conçus et mis en place par Beefy pour débloquer les avantages de l’économie du jeton escrow tout en permettant à nos utilisateurs d'échanger leurs intérêts dans les jetons de gouvernance des partenaires. En effet, nous mettons en place un contrat intelligent provisoire qui peut détenir les jetons de gouvernance, les verrouiller avec le protocole du partenaire pour le verrouillage maximal possible et accéder aux avantages du modèle de séquestre. De plus, nous ajoutons une valeur supplémentaire en combinant ces caractéristiques avec l'émission d'un nouveau beToken ERC20 que vous pouvez ensuite échanger pour sortir du verrouillage à tout moment.

Chaque beToken est conçu de manière unique autour du modèle veTokenomique différent de nos protocoles partenaires, de sorte qu'ils viennent avec une gamme de différentes caractéristiques possibles. Il peut s'agir de réserves de retrait, de liquidité DEX, de cours indexés ou libres, d'un processus de vote Beefy pour l'attribution de votes sur le protocole sous-jacent, de pots-de-vin dirigés par l'utilisateur ou par Beefy, et d'augmentations des coffres Beefy associés.

Beefy soutient toujours ses beTokens avec des coffres sur la plateforme Beefy, où vous pouvez miser vos beTokens pour obtenir un retour. Cela peut être sous la forme d'un coffre de beTokens autocomposé (c'est-à-dire gagner plus de beTokens) ou d'un Earnings Pool (c'est-à-dire gagner plus du jeton de gouvernance sous-jacent). Dans les deux cas, vous êtes libre de vous retirer de votre mise à prix à tout moment, pour échanger vos beTokens et sortir de votre position.

## Quels sont les jetons beTokens existants ?

Dans cette section, nous fournissons une page couvrant chacun des différents jetons beTokens que nous exploitons actuellement. Au moment de la rédaction de ce document, il s'agit de :

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

### Où puis-je en savoir plus ?

Cette section fournit tous les détails sur le design de chacun de nos beTokens existants. Vous pouvez également poser des questions spécifiques sur nos beTokens en nous contactant sur le serveur [Beefy Discord](https://discord.gg/yq8wfHd).

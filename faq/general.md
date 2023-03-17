# Général

## Beefy est-il audité ?

Notre premier audit fut DefiYield, qui s'est occupé d'auditer le jeton $BIFI, la RewardPool (Réserve de récompense) et tous les timelocks.

Depuis, Beefy est audité par Certik, qui garanti la robustesse de nos contrats et la sécurité des fonds investi sur la plateforme Beefy.&#x20;

Certik à aussi audité les stratégies d'investissement les plus complexes et réutilisables de la plateforme, garantissant la sécurité et la robustesse des contrats intelligents avec lesquels la majorité de nos utilisateurs interagissent.

[Vous pouvez retrouver tous les audits Beefy ici.](https://github.com/beefyfinance/beefy-audits)

## Qu'est-ce qu'un Yield Optimizer (Optimiseur de rendement)?

Un _Yield Optimizer_ est un service automatisé qui cherche à apporter le rendement maximum possible sur un investissement, en appliquant des stratégies définies bien plus efficaces que de simples actions effectuées manuellement.

Chaque vault possède sa propre stratégie_,_ qui implique le réinvestissement des crypto-actifs staké dans les _Réserves de Liquidité_ (LP). Les intérêts sont ainsi composés, augmentant votre montant staké et donc la base sur laquelle sera calculée vos prochains intérêts. Un Optimiseur de Rendement peut répéter ce processus plusieurs milliers de fois par jour.

Cette méthode simple est la principale raison derrière le gros APY présent sur Beefy. \
Les frais de Composition sont partagés entre tous les participants au vault, ce qui réduit les coûts pour tous les utilisateurs.

## Quelle est la différence entre APR et APY?

L'APR est l'intérêt annuel, moins les frais potentiels. Il n'inclut pas les intérêts composés possibles en réinvestissant les profits générés tout au long de l'année. Si vous avez investi $100 avec un APR de 100%, vous aurez un profit de $100 à la fin de l'année 1.\


Si vous réinvestissez vos profits régulièrement, vous génèrerez des _Intérêts Composés_. L'APY prend en compte la composition de vos intérêts. Plus vous composerez vos intérêts souvent, plus la différence entre APR et APY sera grande.

## Comment fonctionne l'APY?

L'APY est le _Rendement Annuel en Pourcentage_ proposé sur un investissement précis. Il prend le compte les intérêts composés, afin de vous donner une idée précise de vos profits, comparés à un intérêt simple.\
Les APYs pouvant s'élever à plusieurs milliers de pour cent sont possibles avec des investissements qui prévoient des rendements journaliers de un pour cent, voir plus. Avec vos récompenses constamment récoltées et réinvesties, le montant de vos intérêts augmente de plus en plus, de manière exponentielle.

## Que signifient "Vault Daily" et "Trading Daily"?

![](../.gitbook/assets/vault-trading-daily.png)

Le "Trading Daily" représente la hausse en valeur du prix de vos Jetons de Liquidité. \
Les Réserves de Liquidité répartissent les frais d'échange entre tous les fournisseurs de liquidité, comme présenté dans le [Modèle de Liquidité Uniswap](https://uniswap.org/docs/v2/advanced-topics/fees/). Il est affecté par le volume d'échange et le pourcentage de frais alloué pour les fournisseurs de liquidité.

Le "Vault Daily" représente la hausse en quantité de vos Jetons de Liquidité.\
Le vault récoltant et réinvestissant constamment vos profits, votre nombre total de jetons déposés dans celui-ci va augmenter naturellement. Le "Vault Daily" est affecté par les récompenses de la Ferme de Rendement (s'il existe des primes additionnelles en plus des frais d'échange), comme le CAKE sur PancakeSwap.

Le "Trading Daily" et le "Vault Daily" peuvent être multipliés par 365 pour obtenir le "Trading APR" et le "Vault APR". Le "Vault APR" est ensuite converti en "Vault APY" en incluant les intérêts composés. L'APY total affiché sur les vaults appliquent la formule suivante:&#x20;

$$
APY = (1 + vaultAPY) * (1 + tradingAPR) - 1
$$

{% hint style="info" %}
Pour calculer le Trading APR, Beefy utilise les données on-chain et une période de 24 heures pour déterminer le volume de trading et les frais subséquents, alors que la plupart des DEX utilisent une période de 7 jours. Cela peut entraîner des différences dans l'APY affiché par rapport à un DEX, mais sachez que cela est dû à la méthode de calcul. Nous soutenons que Beefy est plus précis parce qu'il utilise une période plus courte qui reflète plus rapidement les changements dans le Trading APR.
{% endhint %}

Pour finir, voici un outil pratique de conversion APR > APY pour vos recherches: [APRtoAPY.com](https://www.aprtoapy.com/)

## Comment puis-je contribuer à Beefy ?

Beefy Finance est un projet alimenté par sa communauté depuis sa création. Si vous voulez rejoindre le groupe de contributeurs, cela dépendra de ce sur quoi vous voulez travailler. Nous avons des places ouvertes pour des développeurs Solidity, ou des développeurs qui veulent débuter dans ce language, pour nous rejoindre en tant que stratège et déployer des vaults (et gagner un revenu passif, équivalent aux frais de stratège). Beefy est sur beaucoup de chaînes et il y a souvent des opportunités pour des vaults simples et complexes. Vous pouvez commencer par des vaults simples, puis passer à des plus complexes au fur et à mesure que votre connaissance de Solidity augmente. Vous n'avez pas besoin d'être le meilleur dès le départ, et soyez assuré qu'un processus de révision rigoureux est en place pour garantir la sécurité et la qualité. Vous pouvez contacter nos stratèges principaux sur le [Discord Beefy](https://discord.com/invite/yq8wfHd) dans le channel #🎯-strategy-devs.

Beefy aimerait également que des personnes travaillent sur des projets non stratégiques ; à peu près tout ce à quoi vous pouvez penser peut être formulé dans une proposition. Discutez des projets avec les autres membres de la Cowmunauté et rejoignez l'une des équipes ou menez-en une vous-même, vous pouvez être payé pour tout travail que vous faites pour améliorer Beefy. Une liste rapide des subventions précédentes : ici et ici. Beefy V2 est un projet en développement qui nécessite toutes sortes de développeurs, pas seulement des techniciens ; la contribution du design est cruciale pour améliorer l'UI/UX.

Le [GitHub ](https://github.com/beefyfinance)de Beefy embrasse l'idée de collaboration ouverte, c'est pourquoi beaucoup de référentiels sont open-source. Nous utilisons des fichiers CONTRIBUTING.md pour permettre aux gens de simplement faire des contributions ou des recommandations au moyen de Pull-Requests. Vous pouvez vous lancer simplement en mettant à jour la documentation Git ou en corrigeant une coquille, et cela vous permet également de vous rapprocher de l'équipe de contributeurs.

Si vous avez un intérêt pour le développement commercial, vous pourriez aider à établir des partenariats et à proposer des décisions commerciales à la DAO. Beefy est encore une entreprise relativement nouvelle qui peut utiliser des personnes talentueuses pour aider et conseiller le noyau central du projet.

Vous pouvez également contribuer au marketing, si vous savez écrire un tweet décent, vous pouvez aider dans le channel #🐦-tweet-development. Le [Discord ](https://discord.com/invite/yq8wfHd)a un channel #social-watch où sont postés les liens vers les mentions de Beefy sur les médias sociaux. Vous pouvez aider à répondre aux questions des utilisateurs sur ce canal ou directement sur le [Discord ](https://discord.com/invite/yq8wfHd)ou le [Telegram](https://t.me/beefyfinance). Les modérateurs du Discord et du Telegram sont également rémunérés (de manière variable) et constituent généralement la première ligne de soutien aux utilisateurs.

La meilleure façon de s'impliquer est de se lancer, d'aider quand vous le pouvez, de contribuer aux discussions et de collaborer avec tout le monde.

## Quelle est la différence entre un vault et un Earnings Pool ?

Dans un vault, vous gagnez davantage de ce que vous y avez déposé, avec des intérêts composés (APY). Dans un Earnings Pool, vous gagnez un jeton différent de l'actif que vous avez déposé, avec un intérêt linéaire (APR).

Par exemple, le BIFI Maxi Vault, dans lequel vous gagnez plus de BIFI de manière exponentielle, et les nombreux BIFI Earnings Pools, dans lesquels vous gagnez des intérêts linéaires sous la forme de $ETH, $BNB, $AVAX, etc.

## Pourquoi cela coûte si cher de déposer dans un vault Beefy ?

Beaucoup de vaults Beefy utilisent la fonction «[ Harvest on Deposit ](../ecosystem-1/vaults.md#quest-ce-que-la-recolte-au-depot-harvesting-on-deposit)». Cela signifie que lorsque vous effectuez un dépôt dans le vault, vous appelez également la fonction de récolte (Harvest). L'appel de la fonction Harvest est plus complexe qu'un simple dépôt et a donc une limite de gaz/des frais plus élevés. Beefy fait cela pour qu'il soit impossible pour des acteurs malveillants de voler le rendement, et donc des frais de retrait ne sont pas nécessaires. Cela profite également grandement aux investisseurs long terme.

Presque tous les vaults des chaînes les moins coûteuses comme Fantom et Polygon utilisent la fonction de récolte au dépôt (Harvest on Deposit). Vous pouvez également savoir si un vault utilise cette fonction s'il n'y a pas de frais de retrait.\
\
En tant qu'appelant de la récolte, vous recevrez également une partie des jetons natifs  de la chaîne wrappés en tant que récompense pour avoir appelé la récolte. Rendez-vous sur la[beefy-finance-fees-breakdown.md](../ecosystem/beefy-bulletins/beefy-finance-fees-breakdown.md "mention") pour plus d'informations sur l'appelant de la récolte (Harvest Caller).

## Comment puis-je suivre mes gains ?

Vos récompenses sont ajoutées au montant total de votre jeton déposé à chaque récolte et composition. Vous pouvez utiliser un tableau de bord DeFi qui sera capable de calculer exactement le bénéfice que vous avez réalisé sur vos investissements. Des outils externes tels que [TopDeFi ](https://thetopdefi.com/)liront l'adresse de votre portefeuille et vous donneront une image précise de votre investissement initial et de vos gains actuels.

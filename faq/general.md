# Général

## Est-ce que Beefy est audité ?

Notre premier auditeur était DefiYield, qui a audité le jeton $BIFI, le RewardPool et tous les systèmes d'horloge.

Beefy est également audité par Certik, qui garantit la robustesse de nos smart contracts et la sécurité des fonds investis via Beefy.

Certik a audité certaines des stratégies d'investissement les plus complexes et réutilisables utilisées au sein de la plateforme. Cela garantit la sécurité et la robustesse des aspects importants des contrats intelligents avec lesquels la majorité de nos utilisateurs interagissent.

[Tous les audits de Beefy peuvent être trouvés ici.](https://github.com/beefyfinance/beefy-audits)

## Qu'est-ce qu'un optimiseur de rendement ?

Un optimiseur de rendement est un service automatisé qui cherche à obtenir le rendement maximal possible sur les crypto-investissements, beaucoup plus efficacement qu'en essayant de maximiser le rendement par des moyens manuels.

Chaque coffre a sa propre stratégie d'exploitation, qui implique normalement le réinvestissement des actifs crypto dans des fonds communs de liquidité. Au niveau le plus simple, il exploite les récompenses données par les actifs mis en jeu et les réinvestit dans le pool de liquidités. Cela permet d'augmenter le montant des intérêts perçus et d'accroître le montant des mises sur lequel le rendement est basé. Un optimiseur de rendement peut répéter ce processus jusqu'à des milliers de fois par jour.

Cette méthode assez simple est la raison principale derrière les grands APYs trouvés sur Beefy. Les frais de composition sont amortis entre tous les participants du coffre, ce qui les rend moins chers pour l'utilisateur.

## Quelle est la différence entre l'APR et l'APY ?

L'APR (Annual Percentage Rate) est l'intérêt annuel, moins les frais. Il n'inclut pas les effets de composition qui se produisent lors du réinvestissement des bénéfices. Si vous investissez $100 avec un APR de 100%, vous ferez $100 de bénéfices en un an.

Cependant, si vous réinvestissez vos bénéfices régulièrement, vous composerez vos intérêts. Ce calcul sur un an vous donne votre APY (Annual Percentage Yield). Plus vous composez vos intérêts, plus la différence entre le APR et l'APY sera importante.

## Comment fonctionne l'APY ?

L'APY est le rendement annuel en pourcentage offert par un investissement donné. Il tient compte des intérêts composés, ce qui vous donne une idée précise de vos rendements par rapport aux intérêts simples.

Des APY de l'ordre de plusieurs milliers de dollars sont possibles avec des investissements qui offrent des rendements quotidiens de 1 % ou plus. Comme les récompenses de votre réserve de liquidités sont constamment collectées et réinvesties, les intérêts sont composés sur des montants de plus en plus importants.

## Que signifient Vault Daily et Trading Daily ?

![](../.gitbook/assets/vault-trading-daily.png)

Trading Daily signifie de combien la valeur de vos jetons de liquidité augmentera. Les fonds communs de liquidité partagent les frais de transaction entre tous les fournisseurs de liquidité, comme l'a introduit le [modèle de liquidité Uniswap](https://docs.uniswap.org/protocol/V2/concepts/advanced-topics/fees). Le Trading Daily est affecté par le volume de transactions et le pourcentage des frais de swap alloués aux fournisseurs de liquidité.

Vault Daily signifie combien votre jeton va augmenter en nombre. En raison de la récolte constante de récompenses par le coffre, et de leur réinvestissement, le montant de vos jetons déposés augmentera. Vault Daily est affecté par les récompenses de la ferme de rendement (c'est-à-dire des incitations supplémentaires en plus des frais de négociation), comme CAKE sur Pancakeswap.

Le Trading Daily et le Vault Daily peuvent être multipliés par 365 pour calculer le Trading APR et le Vault APR. Le Vault APR est ensuite converti en Vault APY pour tenir compte des intérêts composés. Le pourcentage du rendement annuel total affiché est calculé comme suit :

$$
APY = (1 + vaultAPY) * (1 + tradingAPR) - 1
$$

{% hint style="info" %}
Pour calculer le Trading APR, Beefy utilise les données sur la chaîne et une période de 24 heures pour déterminer le volume de transactions et les frais subséquents, alors que la plupart des DEX utilisent une période de 7 jours. Cela peut entraîner des différences dans l'APY affiché par rapport à un DEX, mais sachez que cela est dû à la méthode de calcul. En fait, nous soutenons que Beefy est plus précis parce qu'il utilise une période plus courte qui reflète plus rapidement les changements dans le Trading APR.
{% endhint %}

Un outil pratique pour convertir le APR en APY est disponible : [APRtoAPY.com](https://www.aprtoapy.com)

## Comment puis-je contribuer à Beefy ?

Beefy Finance est un projet alimenté par la communauté depuis le premier jour. Si vous voulez rejoindre le groupe toujours croissant de contributeurs, cela dépend de ce sur quoi vous voulez travailler. Nous avons des places ouvertes pour les développeurs Solidity, ou les développeurs qui veulent commencer une carrière dans Solidity, pour rejoindre en tant que stratège et déployer des coffres (et gagner un revenu passif des frais de stratège). Beefy est sur beaucoup de chaînes et il y a souvent des opportunités pour des coffres simples et complexes. Vous pouvez commencer par des coffres simples, puis passer à des coffres plus difficiles au fur et à mesure que votre connaissance de Solidity augmente. Vous n'avez pas besoin d'être le meilleur dès le départ, et soyez assuré qu'un processus de révision rigoureux est en place pour garantir la sécurité et la qualité. Vous pouvez contacter nos principaux stratèges sur [Beefy's Discord](https://discord.gg/yq8wfHd) dans #strategy-devs.

Beefy aimerait également que des personnes travaillent sur des projets non stratégiques ; à peu près tout ce à quoi vous pouvez penser peut être formulé dans une subvention. Parlez des projets aux autres membres de la cowmoonité et rejoignez l'une des équipes ou menez-en une vous-même, vous pouvez être payé pour tout travail que vous faites pour améliorer Beefy. Une liste rapide des subventions précédentes : [ici](https://forum.beefy.finance/c/grant-ideas/11) et [ici](https://forum.beefy.finance/c/grant-requests-b1/10). Beefy V2 est un projet en cours qui nécessite toutes sortes de développeurs, pas seulement des techniciens ; la contribution du design est cruciale pour améliorer l'UI/UX.

Beefy's [GitHub](https://github.com/beefyfinance) adhère à l'idée de collaboration ouverte, c'est pourquoi de nombreux dépôts sont à code source ouvert. Nous utilisons des fichiers CONTRIBUTING.md pour permettre aux gens de faire des contributions ou des recommandations par le biais de Pull-Requests. Vous pouvez vous lancer, ne serait-ce qu'en mettant à jour la documentation Git ou en corrigeant une coquille, pour vous rapprocher de l'équipe de contributeurs.

Si vous avez un intérêt pour le développement commercial, vous pourriez aider à établir des partenariats et à proposer des décisions commerciales à la DAO. Beefy est encore une entreprise relativement nouvelle qui peut utiliser des personnes talentueuses pour aider à conseiller l'équipe centrale.

Il y a aussi du marketing auquel vous pouvez contribuer, si vous savez écrire un tweet décent, vous pouvez aider au #tweet-development. Le [Discord](https://discord.gg/yq8wfHd) a un canal #social-watch où sont postés les liens vers les mentions de Beefy sur les médias sociaux. Vous pouvez aider à répondre aux questions des utilisateurs sur ce canal ou sur le [Discord](https://discord.gg/yq8wfHd) ou le [Telegram](https://t.me/beefyfinance) lui-même. Les modérateurs de Discord et Telegram sont également des postes rémunérés (de manière variable) et constituent généralement la première ligne d'assistance à la clientèle.

La meilleure façon de s'impliquer est de se lancer, d'aider quand vous le pouvez, de contribuer aux discussions et de collaborer avec tout le monde.

## Quelle est la différence entre un coffre (Vault) et une Earnings Pool ?

Dans un coffre (Vault), vous gagnez davantage de ce que vous y avez déposé, avec des intérêts composés (APY). Dans un Earnings Pool, vous gagnez un jeton différent de l'actif que vous avez déposé, avec un intérêt linéaire (APR).

Un exemple est le BIFI Maxi Vault, dans lequel vous gagnez plus de BIFI de manière exponentielle, et les nombreux BIFI Earnings Pools, dans lesquels vous gagnez des intérêts linéaires sous la forme de $ETH, $BNB, $AVAX et plus encore.

## Pourquoi ça coûte si cher de déposer dans un coffre Beefy ?

Beaucoup de coffres de Beefy “[Collecte sur dépôt](../products/vaults.md#what-is-harvesting-on-deposit)". Cela signifie que lorsque vous effectuez un dépôt dans le coffre, vous appelez également la fonction de collecte. L'appel de la fonction de récolte est plus complexe qu'un simple dépôt et a donc une limite de gaz/frais plus élevés. Beefy fait cela pour qu'il soit impossible pour les acteurs malveillants de voler le rendement, de sorte que les frais de retrait ne sont pas nécessaires. Cela profite grandement aux investisseurs à long terme puisque les frais de retrait peuvent être supprimés.

Presque tous les coffres des chaînes plus bon marché comme Fantom et Polygon "collectent sur dépôt". Vous pouvez également savoir si un coffre "collecte sur dépôt" s'il n'y a pas de frais de retrait.

En tant qu'appelant de la collecte (Harvest Caller), vous recevrez également une partie du jeton de la chaîne native enveloppée en récompense de l'appel de la collecte. Voir [beefy-finance-fees-breakdown.md](../ecosystem/beefy-bulletins/beefy-finance-fees-breakdown.md "mention") pour plus d'informations sur le Harvest Caller.

## Comment puis-je connaître le montant des gains que j'ai accumulés ?

Vos récompenses sont ajoutées au montant de votre jeton déposé à chaque cycle de récolte et de composition. Vous pouvez utiliser un tableau de bord DeFi qui sera capable de calculer exactement le bénéfice que vous avez réalisé sur vos investissements. Des outils externes tels que [TopDeFi] (https://thetopdefi.com/) liront l'adresse de votre portefeuille et vous donneront une image précise de votre investissement initial et de vos gains actuels.

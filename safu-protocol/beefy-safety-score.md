# Score de Sûreté Beefy

Ce document donne un aperçu de la conception du Score de Sûreté Beefy. Le but du score de sûreté est d'éduquer les utilisateurs lorsqu'ils prennent la décision d'entrer sur un vault Beefy. Ce score n'est pas nécessairement parfait, mais c'est un outil de plus pour aider l'utilisateur.

Le score de sûreté d'un vault peut aller de 1 à 10. Le meilleur score possible est 10 et le pire est 1. Il est techniquement possible pour un vault d'avoir un score inférieur à 1, dans quel cas 1 sera affiché.

Les risques sont répartis en trois catégories principales:

* Risques Beefy: Les risques que nous ajoutons en servant de plateforme.
* Risques des actifs: Les risques du vault qui doit gérer les actifs.
* Risques de la Plateforme: Les risques concernant la plateforme utilisée pour le rendement.

Chaque catégorie représente un pourcentage du score total. Chacune d'entre elles est divisée en multiples sous-catégories.

Tous les vaults débutent avec un score parfait de 10, et des points sont soustraits lorsqu'ils ont des attributs qui augmentent le risque.

## Catégorie: Risques Beefy

Ce sont les risques liés à la plateforme Beefy Finance elle-même. Il pourrait y avoir des risques supplémentaires dû à la complexité de la stratégie du vault, si c'est un déploiement expérimental, si il a été audité par les autres, etc. Les risques Beefy représentent vingt pour cent du score de sûreté.

### Sous-catégorie: Complexité

Trace la complexité de la stratégie appliquée à un vault.

#### COMPLEXITY\_LOW

* Titre: Stratégie Beefy à complexité faible
* Explication: Les stratégies à complexité faible ont peu, s'il y en a, de mouvements et leur code est simple à lire et corriger. Il y a une corrélation directe entre la complexité du code et le risque. Une stratégie simple permet de mitiger les risques d'implémentation.&#x20;
* Critère de qualification: Une stratégie à complexité faible ne devrait interagir qu'avec seulement un contrat intelligent audité et réputé, par exemple, le MasterChef. La stratégie sert de façade pour ce contrat intelligent, ainsi, les demandes de dépôts, récoltes et retraits tiennent en une seule ligne de code.

#### COMPLEXITY\_MID

* Titre: Stratégie Beefy de complexité moyenne
* Explication: Les stratégies de complexité moyenne interagissent avec deux ou plus contrats intelligents audités et connus. Leur code est toujours facile à lire, tester et corriger. Il réduit la plupart des risques d'implémentation en restant simple, mais l'interaction avec deux ou plus de systèmes ajoute une couche de complexité.
* Critères de qualification: Une stratégie de complexité moyenne interagit avec deux ou plus contrats intelligents connus. Cette stratégie automatise l'exécution d'une série d'étapes. Le même processus est appliqué à chaque appel de deposit(), harvest() et withdraw().

#### COMPLEXITY\_HIGH

* Titre: Stratégie Beefy à complexité haute
* Explication: Les stratégies à complexité haute interagissent avec un ou plusieurs contrats intelligents réputés. Ces stratégies avancées présentent des voies d'exécution ramifiées. Dans certains cas, plusieurs contrats intelligents sont requis pour implémenter la stratégie complète.
* Critères de qualification: Une stratégie de complexité haute peut être identifiée par un ou plusieurs facteurs: haute complexité cyclique, interaction avec deux ou plus tiers-plateformes, implémentation divisée entre plusieurs contrats intelligents.

### Sous-catégorie: Longévité

Traque depuis combien de temps cette stratégie est en place sans rencontrer de problème majeur.

#### BATTLE\_TESTED&#x20;

* Titre: Stratégie Beefy aguerrie
* Explication: Plus une stratégie est en place longtemps, plus il est probable que chaque potentiel bug ait été trouvé et corrigé. Cette stratégie à été exposée à l'utilisation et aux attaques depuis un certain temps, n'ayant reçu que de petites voir aucune modifications. Elle est considérée robuste.
* Critères de qualification:
  * Was deployed using a BeefyStratFactory \
    Elle a été déployée en utilisant la BeefyStratFactory&#x20;
  * 10+ stratégies déployées partageant le même code
  * 3 mois de fonctionnement sans problème ni actualisation.

#### NEW\_STRAT

* Titre: Stratégie en place depuis moins d'un mois
* Explication: Plus une stratégie est en place longtemps, plus il est probable que chaque potentiel bug ait été trouvé et corrigé. Cette stratégie est une modification ou itération d'une ancienne stratégie. Elle est récente et donc n'a pas été testée autant que les autres.
* Critères de qualification: -

#### EXPERIMENTAL\_STRAT

* Titre: Stratégie comportant de nouvelles fonctionnalités&#x20;
* Explication: Plus une stratégie est en place longtemps, plus il est probable que chaque potentiel bug ait été trouvé et corrigé. Cette stratégie est toute récente et possède au moins une nouvelle fonctionnalité. Utilisez-la prudemment à vos propres risques.
* Critères de qualification: -

## Catégorie: Risques d'actifs

Les risques liés à l'actif ou aux actifs gérés par le vault. Entrer dans un vault avec du BTC présente un ensemble de risques différent de celui d'un vault d'un jeton plus récent et/ou plus petit. Vingt pour cent du score est déterminé par cette catégorie.

### Sous-catégorie: Perte non permanente (IL)

Traque le risque de perte non permanente au sein du vault

#### IL\_NONE

* Titre: Perte non permanente (IL) projetée très basse voire nulle
* Explication: L'actif dans ce vault à une très petite voir aucune perte non permanente attendue. Cela peut-être car vous déposez un actif simple, ou que les actifs dans la paire de liquidité sont étroitement corrélés, comme USDC-USDT ou WBTC-renBTC.
* Les vaults à actif simple et les vaults qui gèrent des stablecoins ayant un ancrage monétaire non expérimental : USDT, USDC, DAI, sUSD, etc.&#x20;

#### IL\_LOW

* Titre: Perte non permanente (IL) projetée basse
* Explication: Lorsque vous apportez de la liquidité sur une paire de jetons, par exemple ETH-BNB, il y a une chance que le prix de ces actifs se décorrèle. Le BNB pourrait par exemple baisser considérablement par rapport à l'ETH. Vous perdriez alors des fonds par rapport à une simple détention d'ETH et de BNB. Les actifs dans ce vault ont un risque de perte non permanente (IL).
* Critère de Qualification: Les vaults qui supportent ce que nous appelons les paires de liquidité (LP) "Pool 1" rentrent dans cette catégorie: ETH-USDC, MATIC-AAVE, etc. Les jetons de gouvernance pour de plus petits projets sont normalement connu comme "Pool 2" et ainsi exclus.

#### IL\_HIGH

* Titre: Perte non permanente (IL) projetée haute
* Explication: Lorsque vous apportez de la liquidité sur une paire de jetons, par exemple ETH-BNB, il y a une chance que le prix de ces actifs se décorrèle. Le BNB pourrait par exemple baisser considérablement par rapport à l'ETH. Vous perdriez alors des fonds par rapport à une simple détention d'ETH et de BNB. Les actifs dans ce vault ont un très grand risque de Perte non permanente (IL).
* Critère de Qualification: Les vaults des paires de liquidité (LP) "Pool 2" vont ici. Ces paires de liquidité comprennent normalement le jeton de gouvernance de la ferme lui-même.

#### ALGO\_STABLE

* Titre: Stablecoin Algorithmique, Peg expérimental
* Explication: Lorsque vous apportez de la liquidité sur une paire de jetons, par exemple ETH-BNB, il y a une chance que le prix de ces actifs se décorrèle. Le BNB pourrait par exemple baisser considérablement par rapport à l'ETH. Vous perdriez alors des fonds par rapport à une simple détention d'ETH et de BNB. Au moins l'un des stablecoins contenu dans ce vault est algorithmique. Cela veut dire que le peg de ce jeton est expérimental et très risqué. Utilisez-le prudemment à votre propre jugement.&#x20;
* Critère de Qualification: Les “Stablecoins” avec un peg expérimental, ou les tokenomiques qui ont échoués plusieurs fois dans le passé à maintenir leur peg vont dans cette catégorie.

### Sous-catégorie: Liquidité

Traque la difficulté d'achat/vente des jetons du vault.

#### LIQ\_HIGH

* Titre: Liquidité d'échange forte
* Explication: La liquidité d'un actif affecte le risque de le conserver. Les actifs liquides sont échangés à plusieurs endroits avec de bons volumes. L'actif contenu dans ce vault à une forte liquidité. Cela veut dire que vous pouvez échanger vos rendements facilement à plusieurs endroits.
* Critère de Qualification: -

#### LIQ\_LOW

* Titre: Liquidité d'échange faible
* Explication: La liquidité d'un actif affecte le risque de le conserver. Les actifs liquides sont échangés à plusieurs endroits avec de bons volumes. L'actif contenu dans ce vault à une faible liquidité. Cela veut dire qu'il n'est pas facile à échanger et que vous pourriez avoir un plus gros slippage au moment de l'échange.
* Critère de Qualification: -

### Sous-catégorie: Capitalisation de Marché

La valeur totale de tous les jetons en circulation. Traque indirectement la volatilité de l'actif contenu dans le vault.

#### MCAP\_LARGE

* Titre: Capitalisation de marché haute, actif à volatilité faible
* Explication: La capitalisation de marché de l'actif affecte directement le risque de le conserver. Habituellement, une petite capitalisation implique une forte volatilité et une faible liquidité. L'actif contenu dans ce vault à une grande capitalisation de marché. Cela veut dire qu'il s'agit d'un actif plutôt sûr à conserver. L'actif à de grandes chances de rester en vie et de prendre de la valeur dans le temps.
* Critère de Qualification: Top 50 de Capitalisation de marché sur CoinGecko ou CoinMarketCap.

#### MCAP\_MEDIUM

* Titre: Capitalisation de marché moyenne, actif à volatilité moyenne
* Explication: La capitalisation de marché de l'actif affecte directement le risque de le conserver. Habituellement, une petite capitalisation implique une forte volatilité et une faible liquidité. L'actif contenu dans ce vault à une capitalisation de marché moyenne. Cela veut dire qu'il s'agit d'un actif potentiellement sûr à conserver. L'actif à le potentiel de perdurer et de prendre de la valeur dans le temps.
* Critère de Qualification: Top 50-300 de Capitalisation de marché sur CoinGecko ou CoinMarketCap.

#### MCAP\_SMALL

* Titre: Petite capitalisation de marché, haute volatilité
* Explication: La capitalisation de marché de l'actif affecte directement le risque de le conserver. Habituellement, une petite capitalisation implique une forte volatilité et une faible liquidité. L'actif contenu dans ce vault à une capitalisation de marché faible. Cela veut dire qu'il y a un potentiel risque de conserver cet actif. Il a un assez faible potentiel de rester en vie et de grandir dans le temps.
* Critère de Qualification: Top 300-500 de Capitalisation de marché sur CoinGecko ou CoinMarketCap.\


#### MCAP\_MICRO

* Titre: Capitalisation de marché minime, volatilité extrême
* Explication: La capitalisation de marché de l'actif affecte directement le risque de le conserver. Habituellement, une petite capitalisation implique une forte volatilité et une faible liquidité. L'actif contenu dans ce vault à une capitalisation de marché extrêmement faible. Cela veut dire qu'il est très risqué à conserver. Il n'a que très peu de chance de perdurer.
* Critère de Qualification: Les actifs au dessus du Top 500 de Capitalisation de marché sur CoinGecko ou CoinMarketCap.

### Sous-catégorie: Offre en circulation

Traque les risques liés à l'offre en circulation de l'actif. Peut-il être en danger à cause d'un utilisateur ? Est-ce centralisé ?&#x20;

#### SUPPLY\_CENTRALIZED

* Titre: Quelques baleines très (trop?) puissantes
* Explication: Lorsque l'offre en circulation n'est concentrée que dans quelques mains, ces personnes peuvent grandement affecter le prix lorsqu'ils se mettent à vendre. Les baleines peuvent manipuler le prix d'un jeton. Plus il y a de personnes investis sur un jeton, plus le prix est organique et représentatif.
* Critère de Qualification: Moins de 50 portefeuilles possèdent plus de 50% de l'offre en circulation.&#x20;

## Catégorie: Risques de Plateforme

Les risques liés à une plateforme tiers utilisée par le vault. A-t-elle fait ses preuves par le passé, la solidité du code, existe-t-il une action dangereuse qu'un administrateur de cette plateforme puisse effectuer, etc. Soixante pourcent du score est déterminé par cette catégorie.

### Sous-catégorie: Réputation

L'estimation de la réputation de l'équipe administrant la plateforme ainsi que sa communauté. Par exemple, un administrateur a-t-il déjà arnaqué ou Rug Pull ses utilisateurs sur un projet antérieur.

#### PLATFORM\_ESTABLISHED

* Titre: La plateforme à déjà fait ses preuves
  * Explication: Lorsque vous participez dans une ferme, cela peut être utile de savoir depuis combien de temps la plateforme propose ses produits ainsi que sa réputation. Le plus celle-ci possède d'historique, le plus l'équipe et la communauté ont fait leurs preuves et se sont investis dans le projet. Ce vault travaille sur une plateforme qui est en place depuis plusieurs mois.
  * Critère de Qualification: La ferme sous-jacente existe depuis au moins 3 mois.

#### PLATFORM\_NEW

* Titre: La plateforme n'a pas encore fait ses preuves
* Explication: Lorsque vous participez dans une ferme, cela peut être utile de savoir depuis combien de temps la plateforme propose ses produits ainsi que sa réputation. Le plus celle-ci possède d'historique, le plus l'équipe et la communauté ont fait leurs preuves et se sont investis dans le projet. Ce vault travaille sur une nouvelle plateforme qui n'a été que récemment ouverte.
* Critère de Qualification: La ferme sous-jacente existe depuis moins de 3 mois.

### Sous-catégorie: Sécurité

Traque différentes bonnes pratiques mises en place sur les contrats intelligents.&#x20;

#### NO\_AUDIT

* Titre: La plateforme n'a jamais été auditée par un service d'audit tiers fiable
* Explication: Les audits sont des comptes-rendus du code effectués par un groupe de développeur tiers.
* Critère de Qualification: -

#### AUDIT

* Titre: La plateforme a déjà été auditée par au moins un service d'audit tiers fiable
* Explication: Les audits sont des comptes-rendus du code effectués par un groupe de développeur tiers.
* Critère de Qualification: Un ou plusieurs audits est disponible et indique un bilan positif lors de l'analyse

#### CONTRACTS\_VERIFIED

* Titre: Tous les contrats pertinents sont publiquement vérifiés
* Explication: Par défaut, le code fonctionnel d'un contrat n'est pas publique. Les explorateurs de blocs permettent aux développeurs de vérifier le code derrière un contrat en particulier. C'est une bonne chose car cela permet aux autres développeurs de vérifier que le code fait bien ce qu'il est supposé faire. Tous les contrats tiers que ce vault utilise sont vérifiés. Cela le rend moins risqué.\

* Critère de Qualification: -

#### CONTRACTS\_UNVERIFIED

* Titre: Certains contrats ne sont pas vérifiés
* Explication: Par défaut, le code fonctionnel d'un contrat n'est pas publique. Les explorateurs de blocs permettent aux développeurs de vérifier le code derrière un contrat en particulier. C'est une bonne chose car cela permet aux autres développeurs de vérifier que le code fait bien ce qu'il est supposé faire. Certains contrats que ce vault utilise ne sont pas vérifiés. Cela veut dire qu'il y a des éléments que les développeurs de Beefy n'ont pas pu inspecter.
* Critère de Qualification: -

#### ADMIN\_WITH\_TIMELOCK

* Titre: Des fonctionnalités dangereuses sont derrière un timelock
* Explication: Parfois le propriétaire ou l'administrateur du contrat peut exécuter certaines actions qui pourraient mettre les fonds des utilisateurs en danger. Le mieux est les éviter purement et simplement. Si elles doivent impérativement être présentes, il est important de les conserver derrière un timelock afin de pouvoir donner un avertissement convenable aux utilisateurs avant de les utiliser. Ce contrat a certaines actions administrateur dangereuses, mais elles sont au minimum derrière un timelock significatif.&#x20;
* Critère de Qualification: Il y a au moins une fonction présente qui pourrait partiellement ou complètement voler les fonds des utilisateurs. Cette fonction doit être derrière un timelock d'au minimum 6 heures.

#### ADMIN\_WITHOUT\_TIMELOCK

* Title: Des fonctionnalités dangereuses ne sont pas protégées par un timelock
* Explication: Parfois le propriétaire ou l'administrateur du contrat peut exécuter certaines actions qui pourraient mettre les fonds des utilisateurs en danger. Le mieux est les éviter purement et simplement. Si elles doivent impérativement être présentes, il est important de les conserver derrière un timelock afin de pouvoir donner un avertissement convenable aux utilisateurs avant de les utiliser. Ce contrat a certaines actions administrateur dangereuses, et il n'y a pas de timelock mis en place. Celles-ci peuvent donc être exécutées directement sans préavis.
* Critère de Qualification: Il y a au moins une fonction présente qui pourrait partiellement ou complètement voler les fonds des utilisateurs. Cette fonction n'a aucun timelock.

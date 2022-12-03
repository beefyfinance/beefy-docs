# Score de Sécurité de Beefy

Ce document décrit la conception du score de sécurité Beefy. Le but du score de sécurité est d'éduquer les utilisateurs lorsqu'ils prennent la décision d'entrer dans un coffre Beefy particulier. Le score de sécurité n'est pas nécessairement parfait, mais c'est un outil supplémentaire qui aide l'utilisateur.

Le score de sécurité qu'un coffre peut obtenir est compris entre 0 et 10. Le meilleur score possible est 10 et le pire est 0. Il est techniquement possible pour les coffres d'obtenir un score inférieur à 0, auquel cas 0 sera affiché.

Les risques sont répartis en trois grandes catégories :
* Risques de Beefy : Risques liés à l'utilisation de la plateforme.&#x20;
* Risques des actifs : Risques liés à la manipulation de l'actif par le coffre.
* Risques de plateforme : Risques liés à la structure du contrat intelligent ou à la plate-forme sous-jacente utilisée.

Chaque catégorie est responsable d'un pourcentage du score total. Chaque catégorie est elle-même divisée en plusieurs sous-catégories.

Tous les coffres commencent avec un score parfait de 10 et se voient retirer des points chaque fois qu'ils présentent des caractéristiques qui aggravent le risque.

## Category: Risques liés à Beefy

Ce sont des risques liés à la plateforme Beefy Finance elle-même. Il peut s'agir de risques ajoutés par la complexité de la stratégie du coffre, s'il s'agit d'un déploiement expérimental, s'il a été audité par d'autres, etc. Vingt pour cent du score de sécurité est déterminé par les risques de la plateforme Beefy.

### Sous-catégorie : Complexité

Permet de suivre la complexité de la stratégie qui se cache derrière un coffre.

#### COMPLEXITÉ\_FAIBLE

* Titre : Stratégie de complexité faible
* Explication : Les stratégies à faible complexité ont peu, voire aucune, parties actives et leur code est facile à lire et à débuguer. Il existe une corrélation directe entre la complexité du code et le risque implicite. Une stratégie simple atténue efficacement les risques de mise en œuvre.
* Critères de qualification : Une stratégie de faible complexité doit interagir avec un seul contrat intelligent audité et bien connu, par exemple MasterChef. La stratégie sert de façade pour ce contrat intelligent, transmettant les appels de dépôt, de collecte et de retrait en utilisant une seule ligne de code.

#### COMPLEXITÉ\_MOYENNE

* Titre : Stratégie de complexité moyenne
* Explication : Les stratégies de complexité moyenne interagissent avec deux ou plusieurs contrats intelligents audités et bien connus. Son code reste facile à lire, à tester et à débuguer. Elle atténue la plupart des risques de mise en œuvre en gardant les choses simples, mais les interactions entre deux systèmes ou plus ajoutent une couche de complexité.
* Critères de qualification : Une stratégie de complexité moyenne interagit avec 2 ou plusieurs smart contracts bien connus. Cette stratégie automatise l'exécution d'une série d'étapes sans chemins de bifurcation. Chaque fois que deposit(), harvest() et withdraw() est appelé, le même processus d'exécution est réalisé.

#### COMPLEXITÉ\_ÉLEVÉE

* Titre: Stratégie de complexité élevée
* Explication : Les stratégies de haute complexité interagissent avec un ou plusieurs contrats intelligents bien connus. Ces stratégies avancées présentent des chemins d'exécution ramifiés. Dans certains cas, plusieurs contrats intelligents sont nécessaires pour mettre en œuvre la stratégie complète.
* Critères de qualification : Une stratégie de complexité élevée peut être identifiée par un ou plusieurs des facteurs suivants : complexité cyclomatique élevée, interactions entre deux ou plusieurs plateformes tierces, répartition de la mise en œuvre entre plusieurs contrats intelligents.

### Sous-catégorie : Temps de présence sur le marché

Indique depuis combien de temps cette stratégie fonctionne sans problème majeur.

#### MISE\_À\_L'ÉPREUVE

* Titre : La stratégie de Beefy est mise à l'épreuve
* Explication : Plus une stratégie spécifique est utilisée longtemps, plus il est probable que tous les bugs potentiels ont été trouvés et corrigés. Cette stratégie a été exposée aux attaques et à l'utilisation depuis un certain temps déjà, avec peu ou pas de changements. Cela la rend plus robuste.
* Critères de qualification :
  * A été déployé en utilisant un BeefyStratFactory
  * 10+ stratégies partageant le même code déployé
  * 3 mois de fonctionnement sans mise à jour

#### NOUVELLE\_STRATÉGIE

* Titre : La stratégie est en cours depuis moins d'un mois.
* Explication : Plus une stratégie spécifique est en cours d'exécution, plus il est probable que tous les bugs potentiels ont été trouvés et corrigés. Cette stratégie est une modification ou une itération d'une stratégie précédente. Elle n'a pas été testée autant que les autres.
* Critères de qualification : -

#### STRATÉGIE\_EXPÉRIMENTALE

* Titre : La stratégie a des caractéristiques qui sont nouvelles.
* Explication : Plus une stratégie particulière fonctionne longtemps, plus il est probable que tous les bugs potentiels qu'elle comportait aient été trouvés et corrigés. Cette stratégie est toute nouvelle et possède au moins une fonctionnalité expérimentale. Utilisez-la avec précaution et à votre propre discrétion.
* Critères de qualification : -

## Catégorie : Risques liés aux actifs

Risques liés à l'actif ou aux actifs détenus par le coffre. Entrer dans un coffre avec des BTC présente un ensemble de risques différent de celui d'un coffre avec une monnaie plus récente et plus modeste. Vingt pour cent du score est déterminé par cette catégorie.

### Sous-catégorie : Perte impermanente

Suivre le risque de perte impermanente au sein d'un coffre.

#### IL\_ABSENT

* Titre : Perte impermanente prévue très faible voire nulle.
* Explication : L'actif de ce coffre a une perte impermanente attendue très faible ou même nulle. Cela peut être dû au fait que vous mettez en jeu un seul actif, ou que les actifs dans le LP sont étroitement corrélés comme USDC-USDT ou WBTC-renBTC.
* Critères de qualification : Les coffres d'actifs uniques et les coffres qui gèrent des monnaies stables avec un ancrage qui n'est pas expérimental : USDT, USDC, DAI, sUSD, etc. 

#### IL\_FAIBLE

* Title: Perte impermanente prévue faible.
* Explication : Lorsque vous fournissez de la liquidité dans une paire de jetons, par exemple ETH-BNB, il existe un risque que ces actifs se découplent en termes de prix. BNB pourrait chuter considérablement par rapport à ETH. Vous perdriez alors des fonds par rapport à une simple détention d'ETH et de BNB. Les actifs de ce coffre présentent donc des certains risques de perte impermanente.
* Critères de qualification : Les coffre qui gèrent ce que l'on appelle normalement les LP du "Pool 1" conviendraient ici : ETH-USDC, MATIC-AAVE, etc. Les jetons de gouvernance pour les petits projets sont normalement appelés "Pool 2" et sont donc exclus.

#### IL\_ÉLEVÉE

* Title: Perte impermanente prévue élevée.
* Explication : Lorsque vous fournissez de la liquidité dans une paire de jetons, par exemple ETH-BNB, il existe un risque que ces actifs se découplent en termes de prix. BNB pourrait chuter considérablement par rapport à ETH. Vous perdriez alors des fonds par rapport à une simple détention d'ETH et de BNB. Les actifs de ce coffre présentent donc des certains risques de perte impermanente.
* Critères de qualification : Les coffres qui gèrent les LP du "Pool 2" vont ici. Ces LP comprennent normalement le jeton de gouvernance de la plateforme elle-même.

#### STABLE\ALGO

* Title: Stablecoins algorithmiques, expérimentation du peg.
* Explication : Lorsque vous fournissez de la liquidité dans une paire de jetons, par exemple ETH-BNB, il existe un risque que ces actifs se découplent en termes de prix. BNB pourrait chuter considérablement par rapport à ETH. Vous perdriez alors des fonds par rapport à une simple détention d'ETH et de BNB. Les actifs de ce coffre présentent donc des certains risques de perte impermanente.
* Critères de qualification : Les "Stablecoins" avec des pegs expérimentaux, ou les tokenomics qui ont échoué à plusieurs reprises à tenir leur peg dans le passé, vont ici.

### Sous-catégorie : Liquidité

Traque la difficulté d'acheter/vendre le jeton du coffre.

#### LIQUIDITÉ\_ÉLEVÉE

* Titre : Liquidité élevée des échanges.
* Explication : La liquidité d'un actif influe sur le risque qu'il y a à le détenir. Les actifs liquides sont échangés dans de nombreux endroits et avec un bon volume. L'actif détenu par ce coffre a une liquidité élevée. Cela signifie que vous pouvez échanger vos profits facilement à de nombreux endroits.
* Critères de qualification : -

#### LIQUIDITÉ\_FAIBLE

* Titre : Liquidité faible des échanges.
* Explication : La liquidité d'un actif influe sur le risque qu'il y a à le détenir. Les actifs liquides sont échangés dans de nombreux endroits et avec un bon volume. L'actif détenu par ce coffrea une faible liquidité. Cela signifie qu'il n'est pas aussi facile de l'échanger et que vous pouvez subir un slippage élevé lorsque vous le faites.
* Critères de qualification : -

### Sous-catégorie : Capitalisation du marché

Valeur totale de toutes les pièces en circulation. Indique indirectement la volatilité de l'actif sous-jacent du coffre.

#### CAPITALISATION\_DE\_MARCHÉ\_ÉLEVÉE

* Titre : Actif à forte capitalisation de marché et à faible volatilité
* Explication : La capitalisation de marché de l'actif crypto affecte directement le degré de risque qu'il y a à le détenir. Habituellement, une faible capitalisation de marché implique une forte volatilité et une faible liquidité. L'actif détenu par ce coffre a une grande capitalisation de marché. Cela signifie que c'est potentiellement un actif très sûr à détenir. L'actif a un fort potentiel de conservation et de croissance dans le temps.
* Critères de qualification : Top 50 MC par Gecko/CMC

#### CAPITALISATION\_DE\_MARCHÉ\_MOYENNE

* Titre : Capitalisation de marché moyenne, actif à volatilité moyenne
* Explication : La capitalisation de marché de l'actif crypto affecte directement le degré de risque qu'il y a à le détenir. Habituellement, une faible capitalisation de marché implique une forte volatilité et une faible liquidité. L'actif détenu par ce coffre a une capitalisation de marché moyenne. Cela signifie qu'il s'agit potentiellement d'un actif sûr à détenir. L'actif a le potentiel de rester en place et de croître au fil du temps.
* Critères de qualification : Entre 50 et 300 MC par Gecko/CMC

#### CAPITALISATION\_DE\_MARCHÉ\_FAIBLE

* Titre : Faible capitalisation boursière, actif à forte volatilité
* Explication : La capitalisation de marché de l'actif crypto affecte directement le degré de risque qu'il y a à le détenir. Habituellement, une faible capitalisation de marché implique une forte volatilité et une faible liquidité. L'actif détenu par ce coffre a une petite capitalisation de marché. Cela signifie qu'il s'agit d'un actif potentiellement risqué à détenir. L'actif a un faible potentiel de conservation et de croissance dans le temps.
* Critères de qualification : Entre 300 et 500 MC par Gecko/CMC

#### CAPITALISATION\_DE\_MARCHÉ\_TRÈS\_FAIBLE

* Titre : Micro capitalisation de marché, actif de volatilité extrême
* Explication : La capitalisation de marché de l'actif crypto affecte directement le degré de risque qu'il y a à le détenir. Habituellement, une faible capitalisation de marché implique une forte volatilité et une faible liquidité. L'actif détenu par ce coffre a une micro capitalisation boursière. Cela signifie qu'il s'agit d'un actif potentiellement très risqué à détenir. L'actif a un faible potentiel de conservation.
* Critères de qualification : +500 MC par Gecko/CMC

### Sous-catégorie : Offre

Traque les risques liés à l'offre d'actifs. Peut-il être modifié par n'importe qui ? Dans quelle mesure est-il centralisé ?

#### SUPPLY\_CENTRALIZED

* Title: Few very powerful whales
* Explanation: When the supply is concentrated in a few hands, they can greatly affect the price by selling. Whales can manipulate the price of the coin. The more people that have a vested interest over a coin, the better and more organic the price action is.
* Qualification Criteria: Less than 50 accounts hold more than 50% of the supply.&#x20;

## Category: Platform Risks

Risks relating to the third party platforms used by the vault. How much track record they have, how solid the code is, are there any dangerous actions that an admin can take, etc. Sixty percent of the score is determined by this category.

### Subcategory: Reputation

Tries to give clues about the team and community's track record. How likely are they to rug for example.

#### PLATFORM\_ESTABLISHED

* Title: The platform has a known track record
* Explanation: When taking part in a farm, it can be helpful to know the amount of time that the platform has been around and the degree of its reputation. The longer the track record, the more investment the team and community have behind a project. This vault farms a project that has been around for many months.
* Qualification Criteria: The underlying farm has been around for at least 3 months.

#### PLATFORM\_NEW

* Title: Platform is new with little track record
* Explanation: When taking part in a farm, it can be helpful to know the amount of time that the platform has been around and the degree of its reputation. The longer the track record, the more investment the team and community have behind a project. This vault farms a new project, with less than a few months out in the open.
* Qualification Criteria: The underlying farm has been around for less than 3 months.

### Subcategory: Security

Tracks various smart contract good practices.

#### NO\_AUDIT

* Title: The platform has never been audited by third-party trusted auditors
* Explanation: Audits are reviews of code by a group of third party developers.
* Qualification Criteria: -

#### AUDIT

* Title: The platform has an audit from at least one trusted auditor
* Explanation: Audits are reviews of code by a group of third party developers.
* Qualification Criteria: One or more audits from an auditor that has some positive track record in the space.

#### CONTRACTS\_VERIFIED

* Title: All relevant contracts are publicly verified
* Explanation: Code running in a particular contract is not public by default. Block explorers let developers verify the code behind a particular contract. This is a good practice because it lets other developers audit that the code does what it’s supposed to. All the third party contracts that this vault uses are verified. This makes it less risky.
* Qualification Criteria: -

#### CONTRACTS\_UNVERIFIED

* Title: Some contracts are not verified
* Explanation: Code running in a particular contract is not public by default. Block explorers let developers verify the code behind a particular contract. This is a good practice because it lets other developers audit that the code does what it’s supposed to. Some of the third party contracts that this vault uses are not verified. This means that there are certain things that the Beefy devs have not been able to inspect.
* Qualification Criteria: -

#### ADMIN\_WITH\_TIMELOCK

* Title: Dangerous functions are behind a timelock
* Explanation: Sometimes the contract owner or admin can execute certain functions that could put user funds in jeopardy. The best thing is to avoid these altogether. If they must be present, it’s important to keep them behind a timelock to give proper warning before using them. This contract has certain dangerous admin functions, but they are at least behind a meaningful Timelock.&#x20;
* Qualification Criteria: There is at least one function present that could partially or completely rug user funds. The function must be behind a +6h timelock.

#### ADMIN\_WITHOUT\_TIMELOCK

* Title: Dangerous functions are without a timelock
* Explanation: Sometimes the contract owner or admin can execute certain functions that could put user funds in jeopardy. The best thing is to avoid these altogether. If they must be present, it’s important to keep them behind a timelock to give proper warning before using them. This contract has certain dangerous admin functions, and there is no time lock present. They can be executed at a moment's notice.
* Qualification Criteria: There is at least one function present that could partially or completely rug user funds. The function has no time lock protection.

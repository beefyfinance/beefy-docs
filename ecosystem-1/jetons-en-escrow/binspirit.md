---
description: Beefy-wrapped inSPIRIT
---

# binSPIRIT

## Le SPIRIT, c'est quoi ?

Le SPIRIT est le jeton natif de SpiritSwap, un échangeur décentralisé (DEX) sur Fantom Opera. Il récompense les détenteurs avec une part des revenus de la plateforme et agit également comme un jeton de gouvernance. Le SPIRIT à une supply maximum fixe et son émission est décroissante dans le temps.

Les utilisateurs peuvent staker et bloquer leurs jetons SPIRIT sur SpiritSwap pendant une période déterminée entre 1 semaine et 4 ans, et recevrons un montant proportionnel d'inSPIRIT. Les détenteurs d'inSPIRIT reçoivent trois avantages supplémentaires : \
\----------------

* Une proportion des revenus du protocole (qui varient d'une semaine à l'autre, mais il à déjà atteint 80 % APR)&#x20;
* Du droit de vote dans la gouvernance du protocole ;&#x20;
* Jusqu'à 2,5 fois les récompenses boostées des fermes SpiritSwap, en fonction du solde d'inSPIRIT détenu par l'utilisateur.

Une proportion des revenus du protocole (qui varient d'une semaine à l'autre, mais il à déjà atteint 80 % APR) ; (2) Du droit de vote dans la gouvernance du protocole ; et (3) jusqu'à 2,5 fois les récompenses boostées des fermes SpiritSwap, en fonction du solde d'inSPIRIT détenu par l'utilisateur.\
\----------------\
\
Le inSPIRIT n'est pas transférable et le montant détenu par un utilisateur diminue régulièrement jusqu'à 0 lorsque le verrouillage est terminé. Les utilisateurs ne peuvent pas non plus liquider ou transférer leurs positions SPIRIT verrouillées jusqu'à la fin de la période de verrouillage.

## Et le binSPIRIT, qu'est ce que c'est ?

Le binSPIRIT est une version en escrow du jeton inSPIRIT créée par Beefy, qui est staké afin de générer de ce dernier. Les détenteurs de binSPIRIT bénéficient des mêmes avantages que les possesseurs d'inSPIRIT détaillés ci-dessus, mais sans être limités par le mécanisme de verrouillage de la plateforme SpiritSwap.\
\
Le jeton est entièrement backé à 1:1 en SPIRIT, bien qu'il soit perpétuellement verrouillé pour générer du inSPIRIT, et donc ne peut pas être rééchangé en SPIRIT. Cependant, le binSPIRIT est un jeton ERC-20 transférable, il peut donc être échangé contre d'autres jetons sur des échangeurs décentralisés (DEX), permettant aux détenteurs de vendre leurs jetons à tout moment.

## Comment obtenir du binSPIRIT ?

Les utilisateurs peuvent mint du binSPIRIT en déposant et bloquant du SPIRIT sur [la page du vault binSPIRIT](https://app.beefy.finance/vault/beefy-binspirit) à un ratio de 1:1. S'il est plus rentable pour l'utilisateur d'acheter le binSPIRIT, alors le Smart Minter de Beefy l'achètera, donnant à l'utilisateur le plus de binSPIRIT possible en échange de son SPIRIT. Les utilisateurs peuvent également obtenir du binSPIRIT d'eux-mêmes en l'achetant sur un échangeur décentralisé.

DOC FROM ILLUST

![Le beMINT détermine la stratégie la plus rentable](broken-reference)

## Comment fonctionne le binSPIRIT ?

Beefy utilise le SPIRIT déposé par les utilisateurs pour générer autant d'inSPIRIT que possible en verrouillant perpétuellement tous les dépôts sur SpiritSwap pendant la plus longue période disponible. Il utilise ensuite l'inSPIRIT généré pour toucher les revenus du protocole, booster ses vaults, et voter pour les primes d'émissions de la plateforme SpiritSwap.

Tous les revenus du protocole sont versés en SPIRIT, qui sont automatiquement récupérés par Beefy. Ils sont ensuite redéposés dans le vault binSPIRIT, soit en mintant plus de binSPIRIT (si le binSPIRIT est au-dessus du peg), soit en l'achetant sur un échange décentralisé (si le binSPIRIT est en-dessous du peg).

Tous les dépôts, retraits et récoltes de récompenses des vaults SpiritSwap boostés de Beefy sont gérés via le contrat binSPIRIT, afin qu'ils puissent bénéficier du boost grâce au inSPIRIT. En conservant tous les inSPIRIT dans un seul contrat et en gérant tous les vaults via ce même contrat, le binSPIRIT garantit que chaque vault reçoit le maximum de boost possible. \
Chaque vault conserve ses propres récompenses boostées individuellement.

Le contrat binSPIRIT soumet également au nom de Beefy des propositions de votes et d'incentives gauges pour nos vaults à la gouvernance de SpiritSwap. Les holders de binSPIRIT sont habilités à voter sur l'attribution des gauges, comme décrit ci-dessous.\
\
Pour plus de détails sur le fonctionnement et les spécificités du binSPIRIT, voir la page du [contrat GaugeStaker](broken-reference).

## Que faire avec mon binSPIRIT ?

Une fois en possession de binSPIRIT, vous pouvez soit:

1. Le staker dans le vault Beefy binSPIRIT pour toucher des revenus du protocole SpiritSwap, qui sont automatiquement récoltés en transformés en plus de binSPIRIT;
2. Déposez-le dans une Réserve de Liquidité binSPIRIT sur un échangeur décentralisé (par exemple SpiritSwap, Solidly) pour gagner des frais d'échanges (et potentiellement des récompenses);
3. Déposez-le dans la Réserve de Liquidité SPIRIT-binSPIRIT LP sur SpiritSwap et stakez-le dans [le vault Beefy SPIRIT-binSPIRIT LP](https://app.beefy.finance/vault/spirit-binspirit-spirit) pour toucher des frais d'échanges et des récompenses qui seront composés automatiquement.

## Qu'en est-il des frais ?

Beefy a les frais d'optimisation de rendement les plus bas sur la blockchain Fantom. Ils se résument à des frais de performance de 4,5% sur ses vaults binSPIRIT et SPIRIT-binSPIRIT LP. Aucun frais n'est demandé pour l'utilisation du Smart Minter de Beefy pour convertir les SPIRIT en binSPIRIT.

## Comment le binSPIRIT garde-t-il son Peg ?

Lorsqu'un utilisateur souhaite liquider sa position, il peut échanger ses binSPIRIT sur un échangeur décentralisé (DEX). Contrairement au jeton inSPIRIT, les utilisateurs ne sont jamais bloqués avec leurs binSPIRIT et peuvent revendre leurs jetons à tout moment. Cela veut aussi dire que le prix du binSPIRIT n'est peut-être pas toujours lié à celui du SPIRIT, mais vise à maintenir un peg proche.

\--------------------

Si le binSPIRIT descend sous son peg, le contrat utilisera les revenus générés grâce au protocole SpiritSwap pour racheter du binSPIRIT. Chaque possesseur reçoit une part proportionnelle de binSPIRIT calculée sur leur dépôt initial de SPIRIT, ce qui n'aurait pas été possible en bloquant ces mêmes jetons SPIRIT directement sur SpiritSwap.

Si le binSPIRIT dépasse le peg, le contrat utilisera les revenus du protocole pour mint plus de binSPIRIT à profit.\
\
If binSPIRIT goes under peg, then the contract will use the claimed SpiritSwap protocol revenues to buy back more binSPIRIT. This increases the size of each binSPIRIT holder's proportional share of deposited SPIRIT, leaving them with more than they would have achieved from locking the same SPIRIT directly on SpiritSwap.\
\
If binSPIRIT goes over peg, then the contract will use protocol revenues to mint more binSPIRIT at a profit.

\--------------------

## Puis-je voter avec mon binSPIRIT ? <a href="#can-i-vote-with-binspirit" id="can-i-vote-with-binspirit"></a>

Non. Bien que Beefy ait précédemment mis en place un système de vote binSPIRIT et une [page Snapshot dédiée](https://snapshot.org/#/binspirit.eth), le passage à SpiritSwap V2 a permis à Beefy d'automatiser le processus de bribes afin de permettre d'obtenir le meilleur retour sur investissement pour les holders. Beefy renvoie ensuite tous les revenus des bribes dans les vaults binSPIRIT.&#x20;

Bien que Beefy ait automatisé ce processus, nous sommes toujours à l'écoute afin de recevoir de nouvelles offres pour les bribes binSPIRIT. Veuillez contacter l'équipe Core sur Discord, Telegram ou Twitter pour en savoir plus.

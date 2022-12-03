# binSPIRIT

## Qu'est-ce que SPIRIT ?

SPIRIT est le token natif de SpiritSwap, un échange décentralisé natif de la blockchain Fantom. Il récompense ses détenteurs avec une part des revenus de la plateforme et agit également comme jeton de gouvernance. SPIRIT a un modèle d'approvisionnement fixe et d'émissions décroissantes.

Les utilisateurs peuvent mettre en dépôt et verrouiller leurs jetons SPIRIT sur SpiritSwap pour une période fixe comprise entre 1 semaine et 4 ans, afin de recevoir un montant proportionnel de inSPIRIT. Les détenteurs de inSPIRIT reçoivent une série d'avantages, notamment : (1) une proportion des revenus du protocole (qui varient d'une semaine à l'autre, mais qui ont atteint jusqu'à 80 % du TAP) ; (2) des droits de vote dans la gouvernance du protocole et la jauge d'incitation à la voûte ; (3) jusqu'à 2. 5x les récompenses des fermes SpiritSwap, en fonction du solde d'inSPIRIT détenu par l'utilisateur ; et (4) l'accès à des pots-de-vin pour voter pour des jauges incitatives de tiers.

inSPIRIT n'est pas transférable et le montant détenu par un utilisateur donné diminue régulièrement jusqu'à 0 lorsque la jauge est terminée. Les utilisateurs ne peuvent pas non plus liquider ou transférer leurs positions SPIRIT verrouillées avant la fin du verrouillage temporel.

## Qu'est-ce que binSPIRIT ?

binSPIRIT est la version Beefy-escrowed de inSPIRIT qui est stacké pour accumuler du inSPIRIT. Les détenteurs de binSPIRIT reçoivent tous les avantages de inSPIRIT détaillés ci-dessus, mais sans être contraints par le mécanisme de verrouillage SpiritSwap.

Le jeton est entièrement soutenu 1:1 par SPIRIT, mais est perpétuellement verrouillé pour inSPIRIT, et ne peut donc pas être retiré vers SPIRIT. Cependant, binSPIRIT est un jeton ERC-20 transférable, il peut donc être échangé contre d'autres jetons sur des échanges décentralisés, permettant aux détenteurs de sortir de leurs positions à tout moment.

## Comment obtient-on un binSPIRIT ?

Les utilisateurs peuvent miner du binSPIRIT sur la [page du coffre de binSPIRIT](https://app.beefy.finance/#/vault/beefy-binspirit) à un ratio de 1:1. S'il est plus rentable d'acheter du SPIRIT-bin, le mineur "intelligent" de Beefy s'en chargera et l'utilisateur obtiendra plus de SPIRIT-bin pour son SPIRIT. Les utilisateurs peuvent également obtenir du binSPIRIT en l'achetant sur un échange décentralisé.

![beMINT détermine la stratégie la plus rentable](../../.gitbook/assets/binspirit\_mint.jpg)

## Comment fonctionne binSPIRIT ?

Beefy utilise le SPIRIT déposé pour accumuler autant de inSPIRIT que possible en verrouillant immédiatement et perpétuellement tous les dépôts sur SpiritSwap pour la plus longue période disponible. Il utilise ensuite l'inSPIRIT accumulé pour réclamer les revenus du protocole SpiritSwap, renforcer ses coffres SpiritSwap et voter pour les émissions incitatives de SpiritSwap. 

Tous les revenus du protocole sont payés en SPIRIT, qui est automatiquement réclamé par Beefy et ensuite retourné dans le coffre binSPIRIT, soit en minant plus de binSPIRIT (si le binSPIRIT est supérieur à la valeur de référence) ou en achetant des binSPIRIT sur un échange décentralisé (si la valeur de référence est inférieure à la valeur de référence) et ensuite, dans les deux cas, redéposer le binSPIRIT dans le coffre.

Tous les dépôts, retraits et récompenses de récolte des coffres SpiritSwap boostés de Beefy sont acheminés par le contrat binSPIRIT, afin qu'ils puissent recevoir le bénéfice de son boost inSPIRIT. En gardant tous les inSPIRIT accumulés dans un seul contrat, et en faisant passer tous les coffres par ce contrat, binSPIRIT garantit que chaque coffre reçoit le maximum de boost disponible. Toutes les récompenses boostées sont conservées par les coffres individuels Beefy.

Le contrat binSPIRIT soumet également des votes au nom de Beefy pour les propositions de gouvernance SpiritSwap et les jauges d'incitation des coffres. Les détenteurs de binSPIRIT sont habilités à [voter](binspirit.md#puis-je-voter-avec-binspirit) sur les jauges, comme décrit plus loin.

Pour plus de détails sur les fonctionnalités et méthodes spécifiques de binSPIRIT, voir la description de son principal [contrat intelligent GaugeStaker](../../developer-documentation/other-beefy-contracts/gaugestaker-contract.md).

## Comment puis-je gagner de l'argent avec mon binSPIRIT ?

Une fois que vous détenez un binSPIRIT, il y a quelques options disponibles. Vous pouvez soit :

1. Le placer dans le coffre binSPIRIT de Beefy pour gagner des revenus de protocole, qui sont composés automatiquement en plus de binSPIRIT ;
2. Le déposer dans un pool de liquidité binSPIRIT avec un échange décentralisé (par exemple SpiritSwap, Solidly) pour gagner des frais de négociation (et potentiellement des récompenses) ; ou
3. Le déposer dans le SPIRIT-binSPIRIT LP sur SpiritSwap, et miser dans la [coffre Beefy SPIRIT-binSPIRIT LP](https://app.beefy.finance/#/vault/spirit-binspirit-spirit) pour gagner des frais de transaction et des récompenses composés automatiquement.

## Mais qu'en est-il des frais ?

Beefy s'efforce de maintenir des frais d'optimisation de rendement parmi les plus bas, et facture des frais standards sur ses coffres binSPIRIT. Aucun frais Beefy n'est facturé pour l'utilisation du Smart Minter de Beefy pour convertir SPIRIT en binSPIRIT.

## Comment binSPIRIT maintient-il sa parité ?

Si un utilisateur souhaite liquider sa position, il pourra négocier binSPIRIT sur un échange. Contrairement à inSPIRIT, les utilisateurs ne sont jamais bloqués et peuvent sortir de leur position à tout moment. Cela signifie également que le binSPIRIT peut ne pas toujours être rattaché à SPIRIT, mais vise à maintenir un lien souple.

Si le binSPIRIT passe en dessous de la parité, le contrat utilisera les revenus du protocole SpiritSwap pour racheter plus de binSPIRIT. Cela augmente la taille de la part proportionnelle de SPIRIT déposé de chaque détenteur de binSPIRIT, les laissant avec plus que ce qu'ils auraient obtenu en verrouillant le même SPIRIT directement sur SpiritSwap.

Si le binSPIRIT dépasse le peg, alors le contrat utilisera les revenus du protocole pour miner plus de binSPIRIT avec un profit.

## Puis-je voter avec binSPIRIT ?

Non. Bien que Beefy ait précédemment mis en place un système de vote binSPIRIT et une [page Snapshot dédiée](https://snapshot.org/#/binspirit.eth), le passage à SpiritSwap V2 a permis à Beefy d'automatiser le processus de corruption pour nous aider à obtenir le meilleur retour pour les détenteurs. Beefy renvoie ensuite tous les revenus des pots-de-vin directement dans les coffres de binSPIRIT, facilitant ainsi des retours élevés avec un effort minimal.

Bien que Beefy ait automatisé le processus, nous sommes toujours ouverts à recevoir des offres directes pour les pots-de-vin binSPIRIT. Veuillez contacter l'équipe centrale sur Discord, Telegram ou Twitter pour en savoir plus.

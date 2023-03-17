# beOPX

## Qu'est-ce que l'OPX?

L'OPX est le jeton natif d'OPX Finance, un échangeur décentralisé proposant des produits spot et perpetual, basé initialement sur la blockchain Optimism. Il récompense les holders d'une part des revenus du protocole, ainsi qu'un droit de vote dans la gouvernance du protocole. Bien que le jeton intègre des possibilités de mint et de burn, il a adopté un modèle de supply fixe.

OPX propose une nouvelle forme de tokenomique de jetons de vote en escrow ([Qu'est-ce qu'un jeton escrow ?](./)) pour ses mécanismes de partage de profits et de gouvernance. Pour cela, les holders doivent staker et bloquer leurs jetons OPX et un NFT OPX sur le protocole. En contrepartie, ils reçoivent des veOPX, qui reflètent leurs droits à participer à la gouvernance et aux bénéfices du protocole. Les NTF OPX ne peuvent être obtenus qu'à partir d'une mystery box OPX (ou via l'achat à un tiers) et sont mintés avec un niveau aléatoire, qui détermine le pourcentage de boost appliqué aux veOPX détenus.\
\----\
OPX NFTs can only be obtained from an OPX mystery box (or third party sale)\
\----

Le principal mécanisme de gouvernance du jeton veOPX consiste à décider de la répartition des jetons OPX entre :&#x20;

* 1 - Les fournisseurs de liquidité OPX (OLP) ;
* 2 - Le partage des profits aux stakers d'OPX ;
* 3 - La liquidité appartenant au protocole OPX ;
* 4 - La trésorerie des développeurs d'OPX ;
* 5 - Le programme de rachat et de burn de jetons d'OPX ;
* 6 - Le retour de profits à la DAO DarkCrypto - les créateurs d'OPX.

(1) Les fournisseurs de liquidité OPX (OLP) ; (2) Le partage des profits aux stakers d'OPX ; (3) La liquidité appartenant au protocole OPX ; (4) La trésorerie des développeurs d'OPX ; (5) Le programme de rachat et de burn de jetons d'OPX ; et (6) Le retour de profits à la DAO DarkCrypto - les créateurs d'OPX. Le [staking ](https://www.opx.finance/#/stake)et le [vote ](https://www.opx.finance/#/vote)peuvent être effectués via [l'application web d'OPX](https://www.opx.finance/#/).

Le jeton veOPX n'est pas transférable et le montant détenu par un utilisateur diminue progressivement jusqu'à zéro à mesure que la période de blocage se rapproche de son terme. Les utilisateurs ne peuvent pas non plus liquider ou transférer leurs jetons OPX verrouillés avant la fin de la période de verrouillage.

## Et le beOPX, qu'est ce que c'est ?

Le beOPX est une version en escrow du jeton OPX créée par Beefy. L'OPX est ensuite staké afin de recevoir du veOPX et de profiter des avantages offerts par la plateforme aux stakers.&#x20;

Beefy possédant un NFT OPX d'une rareté de niveau 5 (le plus haut rang possible), celui-ci permet d'accéder à une part supplémentaire des bénéfices de la plateforme, qui est réservée aux quelques chanceux qui possèdent un NFT de cette rareté.

Le jeton est entièrement backé à 1:1 OPX et peut être échangé contre des OPX gardés en réserve. Cette réserve s'alimente de plusieurs manières :

1. Si le montant de la réverse est inférieur au minimum prévu lorsque de nouveaux utilisateurs déposent des OPX ;
2. Si le montant de la réverse est inférieur au minimum prévu lorsque le contrat lance la récolte des frais de la plateforme OPX ;
3. Si l'OPX staké dans le contrat est autorisé à être débloqué progressivement.\
   if the contract's staked OPX is left to gradually unlock.

## Comment obtenir du beOPX?

Vous pouvez mint du beOPX sur [la page du vault beOPX ](https://app.beefy.finance/vault/beefy-beopx)à 1:1 avec de l'OPX. Il n'y a pas de prime de liquidité pour le beOPX, mais il existe une réserve de retrait.

## Comment fonctionne le beOPX ?

Lorsque vous mintez du beOPX, et à condition que le montant de la réserve ne soit pas inférieur au montant minimum prévu, le contrat va immédiatement essayer de staker et de bloquer les OPX déposés pour obtenir du veOPX.&#x20;

Au moment du mint, si la réserve d'OPX dépasse le montant minimum prévu (qui est actuellement de 30% des veOPX du contrat), le contrat peut staker les OPX excédentaires pour obtenir des veOPX. Si le montant de la réserve d'OPX est inférieur au montant minimum requis, les OPX déposés seront ajoutés à la réserve pour couvrir le déficit actuel.

Après que le contrat ait staké et bloqué l'OPX, il reçoit du veOPX. Celui-ci permet au contrat de recevoir une proportion des revenus du protocole OPX qui sont attribués aux stakers de la plateforme, ainsi que la possibilité de voter sur les distributions futures des revenus du protocole parmi les différentes options disponibles.

Le contrat beOPX renouvelle continuellement son dépôt et blocage d'OPX, ce qui lui permet de toujours obtenir le maximum de pouvoir de vote et revenus du protocole. Ces derniers sont régulièrement récoltés, échangés en beOPX et redéposés dans [le vault beOPX](https://app.beefy.finance/vault/beefy-beopx) afin d'autocomposer le rendement pour ses utilisateurs.

## Que faire de mon beOPX?

Lorsque vous possédez du beOPX, vous pouvez le staker dans [le vault beOPX](https://app.beefy.finance/vault/beefy-beopx) pour gagner plus de beOPX.

Lorsque notre contrat beOPX récolte les revenus de la plateforme, ceux-ci sont échangés en beOPX et redéposés dans [le vault beOPX](https://app.beefy.finance/vault/beefy-beopx) pour déclencher son autocomposition. Cela permet de maximiser le rendement pour les holders.

## Qu'en est-il des frais ?

Beefy s'efforce de maintenir des frais d'optimisation de rendement parmi les plus bas. Sur le vault beOPX, Beefy n'applique que des frais standard.

## Comment le beOPX garde-t-il son Peg ?

Il n'y a pas de liquidité fournie pour le beOPX, donc il sera toujours égal à 1:1 OPX. Les utilisateurs peuvent burn leur beOPX pour récupérer de l'OPX tant que la réserve est alimentée, sans en affecter le peg.

## Comment puis-je récupérer mon OPX ?

Tant que des jetons OPX seront disponibles dans la réserve, vous pourrez burn vos jetons beOPX existants (jusqu'au montant total de la réserve) pour récupérer une quantité équivalente d'OPX.

Lorsque la réserve ne contient pas suffisamment de jetons OPX pour effectuer le retrait demandé, vous ne pourrez retirer que le montant disponible dans celle-ci. Les utilisateurs peuvent attendre la prochaine récolte de revenus, qui va alimenter la réserve et leur permettre de burn leurs beOPX. Malheureusement, le système de verrouillage des jetons d'OPX Finance ne comprend pas de mécanisme de libération d'urgence.

Le montant minimum de la réserve étant lié à la quantité de veOPX détenue par le contrat, et que le solde de veOPX baisse au fil du temps à mesure que le temps restant jusqu'au déverrouillage diminue, le montant minimum de la réserve diminuera aussi naturellement au fil du temps jusqu'à ce que le verrouillage des OPX soit prolongé. Ainsi, et en supposant qu'aucun autre dépôt d'OPX ne soit effectué pour reconstituer la réserve, le montant minimum de la réserve diminuera progressivement au fil du temps, ce qui signifie que la quantité d'OPX disponible pour le retrait augmentera constamment.

## Puis-je voter avec mon beOPX?

Non. Tout le pouvoir de vote sera utilisé par Beefy pour voter lors de la distribution des revenus du protocole. Les votes ont lieu sur [l'application web d'OPX](https://www.opx.finance/#/vote).

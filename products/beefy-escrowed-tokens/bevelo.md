# beVELO

## Qu'est-ce que VELO ?

VELO est le token natif de Velodrome Finance, une place de marché décentralisée de trading et de liquidité native de la blockchain Optimism. Il récompense les détenteurs d'une part des revenus de la plateforme et sert également de token de gouvernance pour sa jauge hebdomadaire d'incitations au pool. VELO a un modèle d'approvisionnement fixe et d'émissions décroissantes.

Les utilisateurs peuvent mettre en jeu et verrouiller leurs jetons VELO sur Vélodrome pour une période fixe comprise entre 1 semaine et 4 ans, afin de recevoir un NFT de séquestre de vote ("**veNFT**"), qui est utilisé pour enregistrer la quantité de veVELO détenue par l'utilisateur. Les détenteurs de veVELO reçoivent trois avantages : (1) une part des commissions de trading des swaps utilisant les pools de liquidité de la plateforme ; (2) la possibilité de diriger les émissions de VELO distribuées aux fournisseurs de liquidité de la plateforme ; et (3) la possibilité de gagner des pots-de-vin de parties externes en votant pour leurs pools de liquidité incités. Le jalonnement de VELO peut être effectué par l'intermédiaire de l'application Web de Velodrome [web app](https://app.velodrome.finance/vest).

VELO n'est pas transférable et le montant détenu par un utilisateur donné diminue progressivement jusqu'à zéro à mesure que la période de blocage se rapproche de son terme. Les utilisateurs ne peuvent pas non plus liquider ou transférer leurs positions VELO verrouillées avant la fin de la période de verrouillage.

## Qu'est-ce que beVELO ?

beVELO est une version du VELO en jeton de réserve, afin de profiter des divers avantages offerts aux détenteurs de jetons du vélodrome.

Le jeton est entièrement soutenu 1:1 par VELO et peut être échangé contre des VELO détenus en réserve. Cette réserve se remplit dans plusieurs circonstances :

1. lorsque de nouveaux utilisateurs déposent des VELO dans beVELO, s'ils sont inférieurs au montant de réserve requis à ce moment-là;
2. lorsque le contrat récolte des frais d'échange et des pots-de-vin du Vélodrome, s'il est inférieur au montant de réserve requis à ce moment-là ; ou
3. si le VELO jalonné du contrat est laissé pour se débloquer progressivement.

<figure><img src="../../../.gitbook/assets/bevelo_poster-1.png" alt=""><figcaption><p>beVELO est conçu pour capturer le maximum de récompenses et d'avantages possibles de la tokenomique d'escrow de vote de Velodrome.</p></figcaption></figure>.

## Comment obtient-on beVELO ?

Vous pouvez miner des beVELO sur la page [coffre](https://app.beefy.finance/vault/beefy-bevelo) de beVELO dans un rapport de 1:1. Il n'y a pas de liquidité incitative pour beVELO, mais une réserve de retrait.

## Comment fonctionne beVELO ?

Lorsque vous minez du beVELO, le contrat va immédiatement essayer de staker et de verrouiller les VELO déposés en veVELO, sous réserve que la réserve requise soit maintenue.

Si les réserves de VELO du contrat au moment de la fabrication dépassent le montant de la réserve obligatoire (qui est actuellement de 20 % des veVELO du contrat), le contrat peut staker les VELO excédentaires sur les veVELO. Si les réserves de VELO sont inférieures au montant de réserve requis, les VELO déposés seront ajoutés à la réserve pour couvrir le déficit actuel.

Une fois que le contrat VELO est placé et bloqué dans veVELO, il bénéficie de trois avantages : (1) une part des frais de négociation provenant des pools de liquidité de la plateforme ; (2) la possibilité de diriger les émissions de VELO distribuées aux stakers de pool de liquidité ; et (3) la possibilité de gagner des pots-de-vin de parties externes en votant pour leurs pools de liquidité incités.

Comme le contrat beVELO rebloque perpétuellement ses dépôts de VELO, il s'efforce toujours d'obtenir le maximum de pouvoir de vote et d'avantages. Les frais de transaction et les pots-de-vin gagnés sont régulièrement récoltés, échangés contre des beVELO et redéposés dans la chambre forte de beVELO afin de composer automatiquement le rendement pour les détenteurs de beVELO.

## Comment puis-je gagner avec mon beVELO ?

Une fois que vous détenez des beVELO, vous pouvez les mettre en dépôt dans notre coffre pour gagner davantage de beVELO.

Lorsque notre contrat beVELO gagne des frais de transaction et des pots-de-vin en déployant ses veVELO sur le protocole, ces revenus du protocole sont échangés contre des beVELO et redéposés dans le coffre beVELO pour donner lieu à un effet d’intérêts composés. Le rendement pour les détenteurs est ainsi maximisé par rapport à ce qu'ils pourraient obtenir seuls sur le protocole.

<figure><img src="../../../.gitbook/assets/bevelo_vault-1.png" alt=""><figcaption><p>Le beVELO peut être déposé dans notre coffre beVELO, où les gains provenant du staking du VELO du contrat en veVELO sont redéposés et composés automatiquement.</p></figcaption></figure>.

## Mais qu'en est-il des frais ?

Beefy s'efforce de maintenir des frais d'optimisation de rendement parmi les plus bas, et facture des frais standard sur ses coffres beVELO.

## Comment beVELO garde-t-il sa valeur ?

Il n'y a pas de liquidité fournie pour beVELO, donc il sera toujours à 1:1 avec VELO. Les utilisateurs peuvent brûler beVELO pour VELO tant que la réserve dure sans affecter la parité.

## Comment puis-je récupérer mon VELO ?

Tant qu'il y aura des jetons VELO disponibles dans la réserve, vous pourrez brûler vos jetons beVELO existants (jusqu'au montant de la réserve) pour récupérer un montant équivalent de VELO.

Si la réserve ne contient pas suffisamment de jetons VELO pour faciliter le retrait demandé, vous ne pourrez retirer que jusqu'au montant de la réserve.  Les utilisateurs peuvent alors attendre la prochaine récolte de frais d'échange et de pots-de-vin, qui remplira à nouveau la réserve et leur permettra de brûler leurs VELO. Autrement, le mécanisme de verrouillage du Velodrome ne comprend pas de mécanisme de libération d'urgence.

Comme le montant de la réserve requise est lié à la quantité de veVELO détenue par le contrat, et que tous les soldes de veVELO diminuent avec le temps à mesure que le temps restant jusqu'au déverrouillage diminue, le montant de la réserve requise diminuera aussi naturellement avec le temps jusqu'à ce que le verrouillage des veVELO soit prolongé. En tant que tel, et en supposant qu'aucun autre dépôt de VELO ne soit effectué pour reconstituer la réserve, le montant de la réserve requise diminuera progressivement au fil du temps, ce qui signifie que le montant de VELO disponible pour le retrait augmentera constamment.

## Puis-je voter avec mon beVELO ?

Non. Tous les droits de vote des beVELO seront utilisés par Beefy pour voter lors de la procédure d'incitation hebdomadaire des pools de liquidité ;

Les votes seront généralement dirigés soit vers les pools de liquidité offrant le plus de frais de transaction et de pots-de-vin, soit vers les pools de liquidité qui soutiennent notre jeton BIFI (par exemple, BIFI-OP LP). Le contrat beVELO récoltera tous les frais de transaction et les pots-de-vin du protocole et les échangera contre plus de VELO à auto-compenser dans la chambre forte beVELO (augmentant ainsi le rendement pour les détenteurs). Le vote sur les pools de liquidité incitatifs de Velodrome a lieu sur son [application web](https://app.velodrome.finance/vote).

Si vous souhaitez proposer un pot-de-vin à Beefy, veuillez contacter l'équipe centrale sur Discord, Telegram ou Twitter pour en savoir plus.

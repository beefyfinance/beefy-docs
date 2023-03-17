# GMX et GLP

## Qu'est-ce que le GMX?

[GMX ](https://app.gmx.io/#/trade/?ref=beefy)est un échangeur décentralisé multi-chaîne présent sur Arbitrum One et Avalanche, vous permettant d'interagir facilement avec des contrats Perpetuals. Sur le GMX DEX, vous pouvez échanger du BTC, ETH, AVAX, LINK et UNI avec un effet de levier allant jusqu'à x30 depuis votre portefeuille personnel.

En tant que trader, vous entrez et sortez de vos positions avec un impact nul sur le prix, tout en profitant de spreads minimes et d'une grande liquidité. Des données fiables sur les prix sont obtenues via l'agrégation des flux de prix, de sorte que les utilisateurs bénéficient également de risques de liquidation réduits.

## Et le GLP, qu'est ce que c'est ?

Le GLP est un jeton minté par les fournisseurs de liquidité sur GMX. Le GLP représente un indice d'actifs, utilisé pour les échanges avec effet de levier et les swaps sur la plateforme GMX. Vous pouvez le mint en utilisant n'importe quel actif de l'indice et le burn pour racheter n'importe quel actif de l'indice. Le coût du mint et du rachat est calculé suivant la formule suivante :

_(la valeur totale des actifs de l'indice, y compris les profits et les pertes des positions ouvertes) / (La supply de GLP)_

Après avoir mint des GLP, ils sont automatiquement stakés pour gagner des esGMX, une version en escrow du jeton d'utilité et de gouvernance de GMX), \
\----\
des points multiplicateurs \
multiplier points, \
\----\
et des récompenses en ETH ou AVAX selon le réseau sur lequel vous utilisez la plateforme.

## Comment fonctionne la stratégie GPL de Beefy ?

Beefy créé un vault acceptant les dépôts de GLP sur chaque réseau sur lequel l'application est déployée (actuellement Arbitrum et Avalanche). \
\
Pour mint des GLP, vous devrez déposer un actif présent dans l'indice GLP sur GMX comme indiqué précédemment. Les GLP ne sont pas transférables entre les différents réseaux.

La stratégie fonctionne de la manière suivante :

1. Les utilisateurs stakent leur GLP dans [le vault GLP Arbitrum](https://app.beefy.finance/vault/gmx-arb-glp) ou [le vault GLP Avalanche](https://app.beefy.finance/vault/gmx-avax-glp).
2. Beefy récupère et stake tous les esGMX et les ---- multiplier points points multiplicateurs.----\
   \
   Beefy claims and stakes all the earned esGMX and multiplier points.
3. Les esGMX sont utilisés pour booster les récompenses en jetons natifs du réseau du vault.
4. \----Les points multiplicateurs---- sont également utiliser pour augmenter les gains de jetons natifs.
5. Beefy récupère des revenus et mint des GLP supplémentaires avec ces derniers afin de récupérer plus de revenus au fil du temps.

## Quels sont les avantages de la stratégie ?

Les holders de GLP fournissent de la liquidité aux traders à effet de levier et profitent des pertes de ces derniers. À l'inverse, si les traders réalisent des bénéfices, les holders de GLP subissent des pertes. Dans un marché de range à long terme, ces vaults sont considérés comme un pari contre les traders tout en prenant une position stable sur un indice.

## Le délai de transfert du jeton GLP

Il y a un délai de 15 minutes entre le mint et le transfert possible de GLP. Le dépôt de GLP dans le vault Beefy ne sera possible que lorsque la période de délai sur l'adresse de l'utilisateur aura expiré. Ce délai affecte également les retraits du vault Beefy, car chaque récolte entraîne le mint de nouveaux jetons GLP sur l'adresse de la stratégie du vault.

Les retraits ne fonctionneront donc que 15 minutes après la récolte la plus récente. Cette information sera affichée sur l'interface utilisateur du vault. Au niveau du contrat, Beefy a introduit des mesures de sécurité pour empêcher les tentatives d'abus autour de ce système.

## Le lien Referral GMX de Beefy

Les traders qui utilisent [notre lien GMX](https://app.gmx.io/#/trade/?ref=beefy) obtiendront un discount de 5% et accorderont également aux adresses de trésorerie de Beefy un discount de 5%.

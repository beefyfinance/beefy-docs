# GMX et GLP

<figure><img src="../../.gitbook/assets/gmx.png" alt=""><figcaption></figcaption></figure>

## Qu'est-ce que le GMX ?

[GMX](https://app.gmx.io/#/trade/?ref=beefy) est un échange décentralisé multi-chaînes sur Arbitrum One et Avalanche, vous permettant de trader facilement des futures perpétuels. Sur le GMX DEX, vous pouvez trader BTC, ETH, AVAX, LINK, et UNI avec un effet de levier allant jusqu'à 30x à partir de votre portefeuille crypto indépendant.

En tant que trader, vous entrez et sortez de vos positions avec un impact nul sur le prix, tout en profitant de spreads minimes et d'une liquidité importante. Des données fiables sur les prix sont obtenues par l'agrégation des prix, de sorte que les utilisateurs bénéficient également de risques de liquidation réduits.

## Qu'est-ce que le GLP ?

GLP est un jeton attribué aux fournisseurs de liquidité sur GMX. Le GLP représente un indice d'actifs, utilisé pour le trading à effet de levier et les swaps sur la plateforme GMX. Vous pouvez le miner en utilisant n'importe quel actif de l'indice et le brûler pour racheter n'importe quel actif de l'indice. Le coût de minage et de rachat est calculé sur la base de :

_(la valeur totale des actifs de l'indice, y compris les profits et les pertes des positions ouvertes) / (l'offre de BPL).

Après avoir miné des GLP, ils sont automatiquement mis en gage pour gagner des GMX bloqués (esGMX, une version bloquée du jeton d'utilité et de gouvernance de GMX), des points multiplicateurs et des récompenses ETH ou AVAX selon le réseau.

## Comment fonctionne la stratégie GLP de Beefy ?

Beefy crée deux nouveaux coffres, chacun acceptant les dépôts de BPL sur Arbitrum ou Avalanche. Pour miner des BPL, vous devrez déposer un actif contenu dans l'indice BPL sur GMX comme indiqué précédemment. Les BPL ne sont pas transférables entre Arbitrum et Avalanche.

La stratégie fonctionne comme suit :

1. Les utilisateurs placent des BPL dans un des deux coffres de Beefy : [Le coffre Arbitrum GLP](https://app.beefy.finance/vault/gmx-arb-glp) et [le coffre Avalanche GLP](https://app.beefy.finance/vault/gmx-avax-glp).
2. Beefy réclame et met en jeu tous les points esGMX et multiplicateurs gagnés.
3. L'esGMX gagné n'est jamais investi mais est utilisé pour augmenter les gains pour plus de jetons natifs.
4. Les points multiplicateurs gagnés augmentent également les gains pour plus de tokens natifs.
5. Beefy réclame des frais et mine des GLP supplémentaires pour gagner également plus de frais.

## Quels sont les avantages de cette stratégie ?

Les détenteurs de BPL fournissent des liquidités aux traders à effet de levier et profitent des pertes de ces derniers. Si les traders à effet de levier font des profits, les détenteurs de BPL font une perte. Dans un marché de crabe à long terme, ces Vaults sont essentiellement un pari contre les traders tout en prenant une position stable sur l'indice.

## Le délai de transfert des BPL

Il y a un délai de 15 minutes entre le minage et le transfert de GLP. Le dépôt de GLP dans le coffre ne sera possible que lorsque le délai d'attente sur le compte de l'utilisateur aura expiré. Le délai d'attente affecte également les retraits du coffre Beefy Vault car chaque récolte entraîne la frappe de nouveaux GLP à l'adresse stratégique du coffre.

Les retraits ne fonctionneront donc que 15 minutes après la dernière collecte. Ceci sera affiché sur l'interface utilisateur du coffre. Au niveau du contrat, Beefy a mis en place des mesures de protection pour éviter le détournement des retraits.

## Le lien de référence GMX de Beefy

Les traders qui utilisent notre [lien GMX](https://app.gmx.io/#/trade/?ref=beefy) obtiendront une réduction de 5 % et accorderont aux adresses de trésorerie de Beefy une remise de 5 %.

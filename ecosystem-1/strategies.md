# Stratégies

## Qu'est-ce qu'une stratégie de vault ?

Les stratégies de vault Beefy sont des contrats intelligents modulaires qui indiquent au vault  quels actifs il doit exploiter et où les vendre. Les récompenses sont régulièrement récoltées, échangées contre l'actif initial du vault et déposées à nouveau pour profiter de l'effet de composition.

## Qui contrôle les stratégies ?

Chaque lien entre vault et stratégie est codé en dur, et le code a été conçu pour être immuable, donc une fois qu'ils sont publiés, ils ne sont plus modifiables. Personne ne peut modifier les vaults et les stratégies.&#x20;

Pour publier une nouvelle stratégie sur n'importe quel actif, il faut donc créer un nouveau contrat intelligent pour le vault et un autre pour la stratégie.

### Comment puis-je créer une stratégie ?

Pour l'instant, vous pouvez publier et discuter de votre stratégie sur le [Discord Beefy](https://discord.com/invite/beefyfinance) dans le canal #🎯-strategy-devs. Détaillez-y ce qu'il devrait acheter/vendre/exploiter et quel serait l'APY actuel. Il y aura un modèle dans les messages épinglés pour vous aider à démarrer.

### Qu'est-ce que l'APR et l'APY ?

L'APR reflète le taux d'intérêt simple sur une année, tandis que l'APY correspond au taux d'intérêt annuel en prenant en compte l'effet de composition.

### Est-ce que diviser l'APY par 365 permet-il de déterminer les gains quotidiens ?

Non, l'effet des intérêts composés est exponentiel et non linéaire. Un intérêt composé quotidiennement de 1% rapporterait 3678,34% par an.

### Comment Beefy optimise l'APY ?

Beefy automatise l'ensemble du processus de composition, le rendant le plus optimal possible. La fréquence de composition dépend de différentes variables du système, telles que la TVL, l'APR et les frais de stratégie.

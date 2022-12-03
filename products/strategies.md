# Stratégies

### Qu'est-ce qu'une stratégie de coffre ?

Les stratégies de coffre de Beefy sont des contrats intelligents modulaires qui lui indiquent les actifs à récolter, et où il doit vendre les actifs récoltés. Les récompenses sont régulièrement récoltées, échangées contre l'actif de coffre original, et déposées à nouveau pour réaliser un rendement composé.

### Comment fonctionnent les coffres LP ?

![](../../.gitbook/assets/Flow\_LP.png)

### Comment fonctionnent les coffres de prêt ?

![](../../.gitbook/assets/Flow\_single\_asset\_lending.png)

### **Qui contrôle les stratégies ?**

Chaque coffre et chaque stratégie est codée en dur, et le code a été construit pour être immuable, donc une fois qu'ils sont libérés, ils deviennent inarrêtables. Personne ne peut modifier les coffres et les stratégies.

Pour lancer une nouvelle stratégie sur n'importe quel actif, un nouveau contrat intelligent de coffre et de stratégie doit être construit.

### Comment puis-je créer une stratégie ?

Pour le moment, vous pouvez poster et discuter de votre stratégie sur le Discord de Beefy dans le canal #strategies. Détaillez ce qu'il faut acheter/vendre/exploiter et quel est le taux annuel effectif global actuel. Il y aura un modèle pour vous aider à démarrer.

### Qu'est-ce que l’APR et l'APY ?

L’APR reflète le taux d'intérêt simple sur un an, tandis que l'APY décrit le taux avec l'effet de composition.

### APY/365 est-il le bon moyen de déterminer les gains quotidiens ?

Non, l'effet des intérêts composés est exponentiel et non linéaire. Un intérêt composé quotidien de 1% rapporterait 3678.34% par an.

### Comment Beefy optimise-t-il le rendement annuel ?

Beefy automatise l'ensemble du processus de capitalisation, le rendant aussi proche que possible de l'optimum. La fréquence des intérêts composés dépend de différentes variables du système, comme la TVL, l'APR et les frais de stratégie.
# APY des mooVaults

## Qu'est-ce que l'APY?

Prenons l'exemple d'une Ferme de Rendement (Yield Farm) classique, annonçant un APY (Rendement Annuel en Pourcentage) de 100%. La définition de l'APY étant **le taux réel de retour sur investissement, prenant en compte les intérêts composés**. Utiliser le terme APY sous-entend que la ferme effectue la composition des intérêts pour vous, alors que ce n'est pas le cas. La terminologie utilisée devrait être APR (Taux Annuel en Pourcentage), le taux annuel n'étant calculé que sur l'investissement initial. Par définition, cela voudrait dire que cette Ferme de Rendement devrait doubler votre investissement à la fin de l'année 1 sans réinvestir les intérêts. Mais que ce passerait-il si vous réinvestissiez dans cette ferme le montant total (investissement initial + intérêts) l'année suivante, puis encore l'année d'après?

## Comprendre la croissance exponentielle, l'intérêt composé (Compounding)

\--Growth whose rate becomes ever more rapid in proportion to the growing total number or size.--

&#x20;\
La formule à observer pour ce phénomène est : **Croissance **_**= (1 + r)^x,**_ où "r" = rendement et "x" = le nombre de répétition de l'action. Par exemple, avec un rendement annuel de 100%, vous doublez votre argent chaque année. Après trois ans, en ajoutant votre rendement à votre dépôt initial chaque année, vous aurez multiplié par 8 votre investissement.

![Croissance = (1 + 100%)^3](<../.gitbook/assets/capture (2).png>)

## D'accord, mais l'APY, qu'est-ce que c'est réellement ?

Un investissement classique ne paie habituellement pas sur une base annuelle, mais sur des périodes plus courtes (versement journalier, hebdomadaire, mensuel, etc.). Dans le cas d'une Ferme de Rendement, il s'agit d'une base par bloc. Avec une moyenne de 28,800 blocs par jour et des frais de transactions faibles, il est possible de mettre en place une stratégie de croissance exponentielle, que l'on nomme aussi la Composition (Compound), le réinvestissement des intérêts. Voyons ensemble comment cela se présente:

* Composition = **P \* (1+r/n)^nt**                Exemple : 100 \* (1+1/12)^(12\*1)
* P = Principal ou dépôt initial
* r = APR = 100%
* n = Nombre de composition = 12 mois
* t = Temps = 1 an
* Le calcul de l'APY peut être effectué sur Excel avec la formule =EFFECT(r, n)

![
Avec la composition des intérêts, l'année 1 se terminerait avec 261 jetons, soit un APY de 161% contre un APR de 100% sans ce processus](<../.gitbook/assets/capture (3).png>)

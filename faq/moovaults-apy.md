# APY mooVaults

## Qu'est-ce que l'APY ?

Prenons l'exemple d'une ferme de rendement typique, où l'on indique un APY (rendement annuel en pourcentage) de +100% par exemple. La définition traditionnelle de l'APY _**est le taux de rendement réel obtenu sur un investissement en tenant compte de l'effet de la capitalisation des gains**_. L'utilisation de cette terminologie indiquerait que la ferme de rendement compose des gains pour vous. Ce n'est tout simplement pas le cas. Une terminologie plus appropriée serait l'APR (taux annuel en pourcentage), c'est-à-dire le taux annuel obtenu grâce à un investissement. Par définition, cela signifierait que votre ferme de rendement à 100 % doublerait votre investissement initial à la fin de la première année sans réinvestir aucun revenu. Mais qu'en est-il si vous réinvestissez la totalité de ce montant l'année suivante et l'année d'après ?

## Comprendre la croissance exponentielle (Intérêts Composés)

Croissance dont le taux devient de plus en plus rapide en proportion de l'augmentation du nombre total ou de la taille. La formule simple est _**croissance = (1 + r)^x** _ , où "r" = rendement et "x" = nombre de "fois". Par exemple, votre argent double chaque année si vous obtenez un rendement annuel de 100 %. Au bout de 3 ans, vous aurez multiplié par 8 votre investissement initial.

![croissance = (1 + 100%)^3](<../.gitbook/assets/capture (2).png>)

## Ok, alors qu'est-ce que vraiment l'APY ?

Un investissement typique n'est pas seulement payé sur une base annuelle, mais aussi en termes plus petits (c'est-à-dire quotidiennement, mensuellement, etc.). Pour le rendement des fermes, les retours sont même payés sur une base de blocs. Avec une moyenne de 28 800 blocs par jour et des frais de transaction peu élevés, cela peut permettre une croissance exponentielle ou une composition importante de votre rendement. Voyons comment décomposer cela...

* Composition = **P \* (1+r/n)^nt**                Exemple : 100 \* (1+1/12)^(12\*1)
* P = capital ou solde de départ
* r = APR = 100%
* n = périodes de composition = 12 months
* t = période totale = 1 year
* Le calcul simple de l'APY dans Excel peut également être exprimé comme suit = EFFECT(r, n)

![La fin de la première année serait de 261 jetons ou 161% de rendement annuel contre 100% de taux annuel sans capitalisation.](<../.gitbook/assets/capture (3).png>)














# APY de los mooVaults

## ¿Qué es el APY?

Veamos una granja de rendimientos típica, en la que declaran un APY (rendimiento porcentual anual) de, por ejemplo, +100%. La definición tradicional de APY es la tasa de rendimiento real obtenida de una inversión teniendo en cuenta el efecto del interés compuesto. El uso de esta terminología indicaría que la granja de rendimiento se encontraba componiendo las ganancias por usted. Este no es el caso. Una terminología más aplicable sería el APR (tasa de porcentaje anual), es decir, la tasa anual obtenida a través de una inversión. Por definición, esto significaría que su granja de rendimiento con una tasa de 100% duplicaría su inversión original al final del año sin reinvertir ninguna ganancia. Pero, ¿qué pasaría si reinvirtiera toda esa cantidad al año siguiente y al siguiente?

## Entendiendo el crecimiento exponencial (compuesto)

Crecimiento cuya tasa se hace cada vez más rápida en proporción al número o tamaño total creciente. La fórmula sencilla para ello es **crecimiento = (1 + r)^x**, donde “r” = crecimiento y “x” = número de “veces”. Por ejemplo, tu dinero se duplica cada año si obtienes una rentabilidad anual del 100%. Al cabo de 3 años tendrás 8 veces tu inversión original.

![Crecimiento = (1 + 100%)^3](<../.gitbook/assets/capture (2).png>)

## &#x20;Ahora bien, ¿Qué es REALMENTE el APY?

Una inversión típica no sólo se paga anualmente, sino en términos más pequeños (es decir, diariamente, mensualmente, etc.) En el caso del yield farming, los rendimientos se pagan incluso por bloque. Con una media de 28.800 bloques al día y unas tarifas de transacción baratas, esto puede permitir una cantidad significativa de crecimiento exponencial o de capitalización de tus rendimientos. Veamos como desglosar esto...

* Compuesto = **P \* (1+r/n)^nt**                Ejemplo : 100 \* (1+1/12)^(12\*1)
* P = saldo inicial
* r = APR = 100%
* n = períodos de composición = 12 meses
* t = tiempo = 1 año
* El cálculo del APY simple también se puede expresar en Excel como =EFECTO(r, n)

![Al final del año 1 resultaría en 261 tokens o un 161% de APY frente al 100% de APR sin composición.](<../.gitbook/assets/capture (3).png>)

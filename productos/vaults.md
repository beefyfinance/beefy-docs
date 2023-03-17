# Vaults

## ¿Qué es un vault?

Los vaults (o bóvedas, en español) son instrumentos de inversión que emplean un conjunto específico de estrategias para la obtención de rendimientos. Estas hacen uso de la automatización para continuamente invertir y re-invertir los fondos depositados, lo que ayuda a conseguir altos niveles de interés compuesto. Al hacer uso de un vault de Beefy para capitalizar tus ganancias, se ahorran miles de transacciones junto con sus costes de gas y preciado tiempo personal. En vez de retirar y vender las ganancias para comprar más tokens y re invertirlos continuamente, un vault hace todo eso automáticamente con una alta frecuencia.

Los vaults son el núcleo del ecosistema de Beefy.Finance. En un vault de Beefy, se gana más del activo que se deposita en este, independientemente de si se trata de un token proveedor liquidez (LP) o de un solo activo. Por ejemplo, los vaults en los que se puede depositar BTC-BNB LP darán lugar a más BTC-BNB LP con el tiempo, aumentando efectivamente tu participación en el vault y permitiendo así más y más recompensas a lo largo del tiempo.

A pesar de lo que el nombre “vault” sugiere, tus fondos nunca son bloqueados en ningún vault dentro de Beefy Finance: siempre puedes retirarte en cualquier momento. Beefy.Finance tampoco es dueña de los fondos de los usuarios depositados en los vaults. Sin embargo, generalmente es mejor considerar a los vaults como herramientas de inversión para almacenar fondos a mediano y largo plazo, con el fin de que los efectos de la auto-capitalización surtan efecto

Cuando navegue por los vaults en la plataforma, verá la tasa de rendimiento anual (APY, del inglés), la cual tiene en cuenta la auto-capitalización en comparación con la tasa de porcentaje anual (APR), que no la tiene. También podrás ver los porcentajes de interés diarios y el importe total invertido en un vault por todos lo usuarios (TLV). Además es posible ver cual es la la plataforma subyacente que el vault está usando como fuente de ingresos.

Cada vault puede referirse tanto a un par de tokens invertidos en fondos de liquidez, como los tokens CAKE-BNB LP dentro de ecosistema de Binance Smart Chain, o a un solo token invertido en plataformas de préstamos o en pools de un único activo. Después de depositar tokens en un vault, el usuario recibe mooTokens específicos del vault, los cuales representan su participación en el mismo. En la siguiente sección desarrollaremos sobre los mooTokens.

Cualquiera persona de la comuunidad puede colaborar en la creación de nuevas estrategias y presentarlas a la gobernanza para su votación. Observamos las [solicitudes de vaults](https://forum.beefy.finance/c/vault-requests) a través de nuestro foro oficial, donde cualquiera es libre de presentar propuestas.

Resumiendo, los vaults pueden:

* Ejecutar eficientemente las estrategias de optimización de rendimiento.
* Auto-componer las recompensas dentro de la cantidad de tokens depositados
* Utilizar cualquier activo como liquidez.
* Proporcionar un activo como garantía para otro.
* Gestionar el colateral a un nivel seguro para mitigar la liquidación.
* Poner a trabajar cualquier activo para generar un rendimiento.
* Reinvertir los beneficios obtenidos.

Los usuarios pueden sentarse y relajarse, ¡y ver crecer su inversión!

## **¿Qué son los mooTokens?**

Un mooToken es una prueba de depósito tokenizada que genera intereses y que recibirás en el momento en que deposites en un vault de Beefy. Un mooToken es único por vault, por ejemplo: obtienes tokens mooBIFI al depositar BIFI en el vault BIFI Maxi. Los mooTokens se pueden considerar como el recibo de tu depósito en un vault.

{% hint style="info" %}
Los usuarios de Beefy.Finance deben aferrarse a sus mooTokens y no venderlos ni cambiarlos, ¡ya que perderían la propiedad de sus activos depositados en el vault si lo hicieran!
{% endhint %}

## ¿Cómo generan intereses los mooTokens?

Los vaults de Beefy crean automáticamente más del activo depositado en forma de interés compuesto. Al tener mooTokens en tu wallet, su valor aumenta con respecto al activo del correspondiente vault. El número de mooTokens en tu wallet permanecerá constante, pero la cantidad de tokens del vault por los que pueden ser canjeados aumentará. Esta es también la razón por la que los mooTokens no coinciden 1:1 con la cantidad de tokens depositados inicialmente.

## ¿Cómo hago para canjear los mooTokens por los tokens depositados inicialmente?

Siempre que quieras retirar los tokens que están en staking para ti en tu vault de Beefy, simplemente debes iniciar una transacción de retiro para intercambiarlos. Los mooTokens son retirados de tu wallet para ser quemados, y se te devolverán a cambio los activos depositados más los intereses generados.

## ¿Cúales son las ventajas del sistema de mooToken?

El sistema mooToken de Beefy tiene algunas ventajas importantes:

1. Los mooTokens permiten a cualquier usuario retirar su parte de los fondos depositados;
2. El sistema te permite depositar el recibo de mooToken en una wallet fría o de hardware para una mayor seguridad;
3. Tu privacidad se mantiene, ya que sigues siendo anónimo para Beefy. Tus fondos en el vault no están vinculados a la dirección de la wallet desde la que hiciste el depósito, ya que los mooTokens son la única evidencia de tu parte en el vault. Por lo tanto, podrías retirar parte de los fondos desde una dirección diferente si trasladaras tus mooTokens a ella;
4. Los mooTokens tienen ventajas fiscales: como no estás vendiendo recompensas ni recibiendo recompensas de staking directamente a tu dirección, no hay hechos imponibles cuando tienes los fondos depositados en un vault;
5. Por último, los mooTokens pueden ser utilizados como colateral mientras intereses.

## **¿Con qué frecuencia recogen los vaults sus beneficios y los reinvierten?**

Normalmente, los depósitos son recogidos y reinvertidos varias veces al día automáticamente (se auto-componen). Puedes comprobar la tasa de recolección y capitalización de un vault con [ésta guía](../../faq/how-to-guides/how-to-check-harvesting-compounding-rate.md).

## ¿Por qué no puede alguien hacerlo por sí mismo?

Podrían hacerlo, pero los vaults le ayudan a ahorrar tiempo personal y gastos por transacción, mantener ratios de deuda y colateral saludables, auto-optimizarse para obtener los mejores rendimientos posibles y reinvertir automáticamente las ganancias. Intentar hacer todo esto manualmente daría lugar a grandes ineficiencias. En Beefy nos gusta decir: “Siéntate y relájate, los vaults hacen todo el trabajo por usted”.

## **¿Cuál es la estructura de las tarifas de los vaults?**

La mayoría de los vaults tienen una estructura de comisiones sobre el rendimiento, tomando el 4.5% de las recompensas generadas. Este 4.5% sobre los beneficios es repartido de nuevo: el 3% se distribuye de nuevo al pool de recompensas y a aquellos que hacen staking de $BIFI, 0,5% se destina a la tesorería, otro 0,5% es para el estratega que desarrolló el vault, y el último 0,5% es para quien llama a cosechar las recompensas. Estas comisiones ya están incorporadas al APY de cada vault y a la tasa diaria. No es necesario que lo calcules tu mismo.

La comisión sobre el rendimiento adicional, es decir, los beneficios del vault, se distribuyen de gran medida a quienes realizan staking de $BIFI, además de ser la principal fuente de ingresos de la plataforma de Beefy.Finance. Una parte de las comisiones también financia la tesorería, que se utiliza para seguir financiando el desarrollo y seguridad de la plataforma junto a otras iniciativas. La comisión sobre el rendimiento se implementó también para promover el compromiso y participación de la comunidad en la gobernanza. Una comunidad exitosa y comprometida es fundamental para nuestro crecimiento futuro, que a su vez recompensa más a los usuarios de la plataforma.

Además, los vaults tienen una comisión de retiro. El objetivo principal de esta comisión es evitar posibles explotaciones de actores de mala fe. Sin la comisión, alguien podría depositar justo antes de la ejecución de la función harvest() (cosechar) y retirar directamente después de ese evento, llevándose un % de las ganancias generadas por los stakers legítimos. Las comisiones de retiro permanecen en el vault y son repartidas entre los fondos de éste.

### Vaults especiales

El vault Pure CAKE, lanzado el 14 de junio de 2021, tiene 0% de comisión de depósito, 0% de comisión de retirada, 0% de comisión de tesorería y 0% de comisión de estratega. Hay solo una comisión de rendimiento, que va directamente a los stakers de BIFI Maxi, la cual es del 1%. Para evitar que los malos actores roben las recompensas de la cosecha, el vault de Pure CAKE cosecha directamente antes de que el usuario deposite su CAKE.

## **¿Se descuenta la comisión de rendimiento cuando retiro mis fondos?**

* No, las comisiones de rendimiento son sobre los beneficios y se toman cada vez que alguien llama a la función harvest().

## ¿La página del vault muestra el APY?

Sí. Nuestros valores de APY mostrados reflejan la tasa prevista que ganaría un vault en un año. Esta tasa está determinada por la plataforma subyacente que el vault utiliza, la estrategia con la que está interactuando en ese momento, la cantidad de fondos en el vault, y teniendo en cuenta también el efecto de la auto-capitalización. Como característica única, también hemos incluido todas las comisiones del vault en el cálculo del APY. ¡Lo que ves es lo que obtienes!

## ¿Qué riesgos tienen los vaults?

Los vaults de Beefy son auditados, pero esto no significa que estén totalmente libres de riesgos. A continuación se indican algunos de los riesgos generales de los vaults:

* Los activos depositados en el vault no tienen riesgo de disminuir en cantidad, pero sí en valor monetario.
* Como con cualquier contrato inteligente, el riesgo final es que los fondos de un inversor acaben siendo robados o retirados. El equipo toma medidas para cuantificar los riesgos de seguridad de los contratos inteligentes y sólo interactuará con aquellos que cumplan una serie de requisitos específicos tras realizar una enorme cantidad de pruebas para asegurarse de que la plataforma subyacente no contenga las funciones denominadas como “rug-pull” (“tirón de alfombra”).

Puedes encontrar más detalles sobre los riesgos de los vaults, o mejor aún, sobre la seguridad de los vaults de Beefy expresada en nuestra propia puntuación de seguridad, aquí: [Puntuación de Seguridad de Beefy](../../safu-protocol/beefy-safety-score.md).

## **¿Cuáles son los diferentes vaults?**

* **Mercado Monetario:** utiliza plataformas de préstamos, como Venus en BSC, para generar el mayor rendimiento posible para estas monedas (por ejemplo: BUSD, BNB, LINK, DOT, DAI, USDT, ETH, BTCB).
* **Granjas de Tokens Nativos :** Granjas de tokens nativos: Aprovechan el alto rendimiento de granjas populares depositando otro activo para ganar, vender o capitalizar los beneficios del token de recompensa nativo.

## ¿Qué obtendré al momento de retirarme de un vault?

Siempre retirarás el tipo de token que depositaste, porque en Beefy ganas lo que depositas. Recibirás la cantidad que depositaste más el rendimiento generado menos las comisiones de retiro de el vault.

## **¿Cómo funcionan los vaults de LP?**

Los fondos de liquidez (LP) funcionan reinvirtiendo las comisiones concedidas a quienes participan en los LP. A cambio de proporcionar liquidez al fondo, muchas plataformas recompensan a los inversores con tokens. Nuestros vaults cosechan regularmente estas recompensas, las venden, compran más activos subyacentes del LP y luego los reinvierten para completar el ciclo.

Esto auto-capitaliza las recompensas obtenidas de un fondo de liquidez. Beefy.Finance crea estrategias que automatizan este proceso, ahorrando tiempo y tasas de gas en comparación con el farming manual. Todo esto se hace a cambio de una pequeña comisión que se distribuye a quienes participan en el fondo de gobernanza de Beefy o en el vault BIFI Maxi. Un pequeño porcentaje también va dirigido a la tesorería de Beefy Finance.

## **¿Con qué frecuencia se actualizan los balances en los vaults?**

* Las recompensas pendientes no se reflejan en el saldo hasta que se intercambian por el token depositado inicialmente. Esto puede variar en función de la estrategia que se esté ejecutando.

## **¿Cómo son añadidos los vaults a Beefy Finance?**

Los potenciales nuevos vaults pueden ser discutidos en nuestro Discord en el canal #whitebaord. Nuestros estrategas añaden entonces la estrategia de inversión a nuestra lista de potenciales estrategias. Se asigna una prioridad a cada nueva potencial estrategia en función de su APY, TVL y sostenibilidad. Después, nuestros desarrolladores/estrategas trabajan en la lista en orden de mayor a menor prioridad. El foro oficial es utilizado para presentar verdaderas [solicitudes de vaults](https://forum.beefy.finance/c/vault-requests).

## **¿Cuál es su proceso de nombramiento de vaults?**

Cada vault en la plataforma lleva el nombre del token que los usuarios pueden depositar en él. Por ejemplo, el vault CAKE-BNB LP utiliza tokens CAKE-BNB LP para su estrategia de inversión. Un vault de BTC utiliza el token BTC, etc.

Debajo del nombre del vault, puedes encontrar la plataforma utilizada para invertir el token y para realizar el farming de los rendimientos. Por ejemplo: Venus significa que ese vault en particular invierte el token en Venus, un mercado monetario algorítmico DeFi y un protocolo de stablecoin sintético.

## **¿Cómo funcionan los vaults de préstamos?**

_Lo siguiente se aplica a: Aave, Banker Joe, Blizz, Geist, Scream, Venus y plataformas de préstamo similares._

La mayoría de los vaults de activos individuales de Beefy utilizan mercados descentralizados para prestamistas y prestatarios. Al depositar su activo en el vault, Beefy lo deposita en el mercado de préstamos y pide prestado contra su token a niveles seguros de colateral.

Los tokens prestados se vuelven a depositar en la plataforma y se utilizan de nuevo como colateral para pedir prestados más tokens. Este ciclo se repite varias veces para generar el mayor beneficio posible de los intereses del préstamo y el token de recompensa, que se utiliza para comprar más de los activos depositados inicialmente por ti. Esta estrategia también se conoce como estrategia de plegado. Cabe destacar que este “apalancamiento” de múltiples entregas y tomas de préstamos se realiza únicamente con el token depositado en el vault, por lo que no existe riesgo de liquidación debido a las oscilaciones de precio del token.&#x20;

{% hint style="info" %}
Comisiones por transacción: debido al ciclo múltiple de de entrega y toma de préstamos, la comisión por transacción por un depósito o retiro de uno de estos vaults es generalmente más alta en comparación a otros vaults.
{% endhint %}

{% hint style="warning" %}
Riesgo de comerciabilidad: cuando el token subyacente en la plataforma de préstamos se sobre-presta, puede impedir que la estrategia de el vault se des-apalanque (se despliegue) para dar lugar a una retirada. Esto suele ocurrir cuando el mercado es más volátil, o cuando hay un evento en curso por el que la gente quiere tomar prestados fondos de la plataforma de préstamos en cuestión. La situación de sobre-endeudamiento se resolverá de forma natural una vez que la liquidez vuelva a la plataforma de préstamos, un proceso que puede durar horas, o a veces, unos días. Mientras tanto, los fondos permanecen siempre seguros.
{% endhint %}

Debido a la acumulación de intereses de la entrega/toma de préstamos, uno puede notar que la cantidad de tokens depositados puede disminuir ligeramente entre las cosechas. Después de la cosecha, verás que la cantidad de tokens depositados aumenta a medida que los rendimientos se vuelven a acumular en estos. El cambio en la cantidad de tokens depositados a lo largo del tiempo en un típico vault del estilo de préstamos tiene el siguiente aspecto:

![Después de un evento de cosecha, los rendimientos se añaden a la cantidad de tokens depositados](../../.gitbook/assets/venus-style-vault.png)

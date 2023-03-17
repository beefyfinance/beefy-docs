# GMX & GLP

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

## ¿Qué es GMX?

GMX es un exchange descentralizado multi-cadena en Arbitrum One y Avalanche, que te permite comerciar fácilmente futuros perpetuos. En el DEX de GMX, puedes comerciar BTC, ETH, AVAX, LINK y UNI con un apalancamiento de hasta 30x desde tu billetera de criptomonedas auto custodiada.&#x20;

Como trader, puedes entrar y salir de tus posiciones sin ningún impacto en el precio, mientras obtienes ganancias de spreads mínimos y liquidez profunda. Los datos de precios confiables se logran mediante la agregación de fuentes de precios, por lo que los usuarios también se benefician de riesgos de liquidación reducidos.

## ¿Qué es GLP?&#x20;

GLP es un token minteado para proveedores de liquidez en GMX. GLP representa un índice de activos, utilizado para trading con apalancamiento e intercambios en la plataforma GMX. Puedes mintearlo utilizando cualquiera de los activos del índice y quemarlo para canjear cualquiera de los activos del índice. El costo de mintear y canjear se calcula en base a:

&#x20;(el valor total de los activos en el índice, incluidas las ganancias y pérdidas de posiciones abiertas) / (suministro de GLP)&#x20;

Después de mintear GLP, se estaca automáticamente para ganar GMX en custodia (esGMX, una versión en custodia del token de utilidad y gobernanza de GMX), puntos multiplicadores y recompensas en ETH o AVAX dependiendo de la red.

## ¿Cómo funciona la estrategia GLP de Beefy?

Beefy está creando dos nuevos Vaults, cada uno aceptando depósitos de GLP en Arbitrum o Avalanche. Para crear GLP, deberá depositar un activo contenido en el índice GLP en GMX como se describió anteriormente. GLP no es transferible entre Arbitrum y Avalanche.&#x20;

La estrategia funciona de la siguiente manera: Los usuarios depositan GLP en uno de los dos Vaults de Beefy:&#x20;

1. Vault de GLP en Arbitrum o Vault de GLP en Avalanche.&#x20;
2. Beefy reclama y stakea todas las ganancias de esGMX y puntos multiplicadores.&#x20;
3. El esGMX ganado nunca se invierte, sino que se utiliza para aumentar las ganancias de tokens nativos.
4. &#x20;Los puntos multiplicadores también aumentan las ganancias de tokens nativos.&#x20;
5. Beefy reclama fees y crea GLP adicional para obtener más fees.

## ¿Cuáles son los beneficios de la estrategia?&#x20;

Los titulares de GLP proporcionan liquidez para los traders apalancados y obtienen ganancias cuando los traders apalancados sufren pérdidas. Si los traders apalancados obtienen ganancias, los titulares de GLP sufren pérdidas.&#x20;

En un mercado bajista a largo plazo, estas bóvedas son esencialmente una apuesta en contra de los traders, mientras que también mantienen una posición estable en el índice.

## Tiempo de espera para transferir GLP&#x20;

Existe un tiempo de espera de 15 minutos entre la creación y la transferencia de GLP. El depósito de GLP en la Bóveda Beefy solo tendrá éxito cuando haya expirado el tiempo de espera en la cuenta del usuario.&#x20;

El tiempo de espera también afecta a los retiros de la Bóveda Beefy, ya que cada cosecha generará nuevos GLP a la direccióndel contrato de la Bóveda.&#x20;

Por lo tanto, los retiros solo funcionarán 15 minutos después de la cosecha más reciente. Esto se mostrará en la interfaz de usuario de la Bóveda. A nivel de contrato, Beefy ha introducido medidas de seguridad para evitar retiros abusivos.

## El enlace de referencia de Beefy GMX

Los traders que utilicen nuestro enlace GMX obtendrán un descuento del 5% y otorgarán a las direcciones de tesorería de Beefy un reembolso del 5%.

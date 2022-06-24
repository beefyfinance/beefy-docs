# Puntuación de seguridad de Beefy

Este documento describe el diseño de la puntuación de seguridad de Beefy. El propósito de la puntuación de seguridad es educar  a los usuarios a la hora de tomar la decisión de entrar en un vault de Beefy en particular. La puntuación de seguridad no es necesariamente perfecta, pero es otra herramienta que ayuda al usuario.

La puntuación de seguridad que puede obtener un vault va de 0 a 10. La mejor puntuación posible es 10 y la peor es 0. Es técnicamente imposible que los vaults tengan una puntuación inferior a 0, en cuyo caso se mostrará un 0.

Los riesgos se distribuyen en tres categorías principales:

* Riesgos de Beefy: Riesgos que añadimos al servir de plataforma.&#x20;
* Riesgos del activo: Riesgos del activo que está siendo manejado por el vault.
* Riesgos de la plataforma: Riesgos de la plataforma o granja subyacente utilizada.

Cada categoría es responsable de un porcentaje de la puntuación total. Cada categoría se divide a su vez en múltiples subcategorias.

Todos los vaults comienzan con una puntuación perfecta de 10 y se le restan puntos siempre que tenga cualidades que aumentan el riesgo.

## Categoría: Riesgos de Beefy

Se trata de riesgos relacionados con la propia plataforma de Beefy Finance. Pueden ser riesgo añadidos por la complejidad de la estrategia del vault, si es un lanzamiento experimental, si ha sido auditado por otros, etc. El 20% de la puntuación de seguridad es determinada por los riesgos de Beefy.

### Subcategoría: Complejidad

Indica la complejidad de la estrategia detrás de un vault.

#### COMPLEJIDAD\_BAJA

* Título: Estrategia de baja complejidad
* Explicación: Las estrategias de baja complejidad tienen pocas partes móviles, o ninguna, y su código es fácil de leer y depurar. Existe una correlación directa entre la complejidad del código y el riesgo implícito. Una estrategia sencilla mitiga eficazmente los riesgos de implementación.
* Criterios de Calificación: Una estrategia de baja complejidad debe interactuar con un solo contrato inteligente auditado y conocido, por ejemplo MasterChef. La estrategia sirve de fachada para este contrato inteligente, enviado las llamadas de depósito, recolección y retirada utilizando una sola línea de código.

#### COMPLEJIDAD\_MEDIA

* Título: La estrategia de Beefy es de complejidad media
* Explicación: Las estrategias de complejidad media interactúan con dos o más contratos inteligentes auditados y conocidos. Su código sigue siendo fácil de leer, probar y depurar. Mitiga la mayoría de los riesgos de implementación al mantener las cosas simples, sin embargo las interacciones entre 2 o más sistemas añaden una capa de complejidad.
* Criterios de calificación: Una estrategia de complejidad media interactuá con 2 o más contratos inteligentes conocidos. Esta estrategia automatiza la ejecución de una serie de pasos sin rutas de bifurcación. Cada vez que se llama a las funciones depositar(), recolectar() y retirar(), se sigue la misma ruta de ejecución.

#### COMPLEJIDAD\_ALTA

* Título: La estrategia de Beefy es compleja
* Explicación: Las estrategias de alta complejidad interactúan con uno o más contratos inteligentes conocidos. Estas estrategias avanzadas presentan rutas de ejecución ramificadas. En algunos casos se requieren múltiples contratos inteligentes para implementar la estrategia completa.
* Criterio de calificación: Una estrategia de alto nivel de complejidad puede ser identificada por uno o más de los siguientes factores: alta complejidad ciclomática, interacciones entre dos o más plataformas de terceros, implementación dividida entre múltiples contratos inteligentes.

### Subcategoría: Tiempo en el mercado

Indica cuánto tiempo ha estado funcionando esta estrategia sin ningún problema importante.

#### BATALLA\_PROBADA

* Título: La estrategia de Beefy es probada en batalla
* Explicación: Cuanto más tiempo se ejecuta una estrategia en particular, más probable es que cualquier error potencial que hubiera podido tener ya ha sido encontrado y resuelto. Esta estrategia ha sido expuesta a ataques y uso durante algún tiempo ya, con pocos o ningún cambio. Esto la hace más robusta.
* Criterios de calificación:
  * Fue implementada usando BeefyStratFactory
  * 10+ estrategias comparten el mismo código implementado
  * 3 meses funcionando como se esperaba sin actualizaciones

#### NUEVA\_ESTRATEGIA

* Título: La estrategia lleva menos de un mes funcionando
* Explicación: Cuanto más tiempo lleva una estrategia en marcha, más probable es que se hayan encontrado y solucionado los posibles errores que tenga. Esta estrategia es una modificación o iteración de una estrategia anterior. No ha sido probada en batalla tanto como otras.
* Criterios de calificación: -

#### ESTRATEGIA\_EXPERIMENTAL

* Título: La estrategia tiene algunas características que son nuevas
* Explicación: Cuanto más tiempo esté funcionando una estrategia en particular, más probable es que se hayan encontrado y solucionado los posibles errores que tenía. Esta estrategia es nueva y tiene al menos una característica experimental. Utilícela con cuidado a su propia discreción.
* Criterios de calificación: -

## Categoría: Riesgos de los activos

Riesgos relacionados con el activo o los activos que maneja el vault. Entrar en un vault con BTC tiene un conjunto diferente de riesgos que entrar en un vault con una moneda más nueva y más pequeña. El 20% de la puntuación viene determinada por esta categoría.

### Subcategoría: Pérdida impermanente

Indica el riesgo de pérdida impermanente dentro del vault.

#### SIN\_PI

* Título: PI proyectada muy baja o nula
* Explicación: El activo en este vault tiene una pérdida impermanente esperada muy baja o incluso nula. Esto puede deberse a que está stakeando un solo activo, o a que los activos en el LP están estrechamente correlacionados, como USDC-USDT o WBTC-renBTC.
* Criterios de calificación: Vaults de un solo activo y vaults que gestionan stablecoins con una vinculación que no es experimental: USDT, USDC, DAI, sUSD, etc.

#### PI\_BAJA

* Título: PI proyectada baja
* Explicación: Cuando se proporciona liquides a un par de tokens, por ejemplo ETH-BNB, existe el riesgo de que esos activos se desacoplen en el precio. BNB podría caer considerablemente en relación con ETH. Usted perdería algo de dinero como resultado, en comparación con sólo mantener ETH y BNB por su cuenta. Los activos de este vault tienen algunos riesgos de pérdida impermanente.
* Criterios de calificación: Los vaults que manejan lo que normalmente se denominan LPs de “Pool 1” encajarían aquí. ETH-USDC, MATIC-AAVE, etc. Los tokens de gobernanza para proyectos más pequeños se conocen normalmente como “Pool 2” y por lo tanto están excluidos.

#### PI\_ALTA

* Título: PI proyectada alta
* Explicación: Cuando se proporciona liquidez a un par de tokens, por ejemplo ETH-BNB, existe el riesgo de que esos activos se desacoplen en el precio. BNB podría caer considerablemente en relación con ETH. Usted perdería algunos fondos como resultado, en comparación con sólo mantener ETH y BNB por su cuenta. Los activos de este vault tienen un riesgo muy alto de pérdida impermanente.
* Criterios de calificación: Los vaults que manejan LPs de “Pool 2” van aquí. Estos LP normalmente incluyen el token de gobernanza de la propia granja.

#### ALGORITMO\_ESTABLE

* Título: Estabilidad algorítmica, vinculación experimental
* Explicación: Cuando se proporciona liquidez a un par de tokens, por ejemplo ETH-BNB, existe el riesgo de que esos activos se desacoplen en el precio. BNB podría caer considerablemente en relación con ETH. Usted perdería algunos fondos como resultado, en comparación con sólo mantener ETH y BNB por su cuenta. Al menos una de las stablecoins en este vault tiene estabilidad algorítmica. Esto significa que la vinculación estable es experimental y altamente arriesgada. Utilízalo con cuidado a tu propia discreción.
* Criterios de calificación: Las “stablecoins” con vinculaciones experimentales, o tokenomics que han fallado repetidamente en mantener su vínculo en el pasado, van aquí.

### Subcategoría: Liquidez

Indica lo difícil que es comprar/vender el token del vault.

#### LIQUIDEZ\_ALTA

* Título: Alta liquidez de intercambio
* Explicación: El grado de liquidez de un activo influye en el riesgo que significa mantenerlo. Los activos líquidos se negocian en muchos lugares y con un buen volumen. El activo que posee este vault tiene una alta liquidez. Esto significa que puedes intercambiar tus beneficios fácilmente en muchos lugares.
* Criterios de calificación: -

#### LIQUIDEZ\_BAJA

* Título: Baja liquidez de intercambio
* Explicación: El grado de liquidez de un activo influye en el riesgo que significa mantenerlo. Los activos líquidos se negocian en muchos lugares y con un buen volumen. El activo que posee este vault tiene baja liquidez. Esto significa que no es tan fácil de intercambiar y podría incurrir en un alto deslizamiento del precio al hacerlo.
* Criterios de calificación: -

### Subcategoría: Capitalización de mercado

Valor total de las monedas en circulación. Indirectamente, indica la volatilidad del activo subyacente del vault.

#### CAPM\_GRANDE

* Título: Activo de alta capitalización de mercado y baja volatilidad
* Explicación: La capitalización de mercado de la criptomoneda afecta directamente a lo arriesgado que es tenerla. Por lo general, una pequeña capitalización de mercado implica una alta volatilidad y baja liquidez. El activo que posee este vault tiene una gran capitalización de mercado. Esto significa que es un activo potencialmente seguro. El activo tiene un alto potencial para mantenerse y crecer con el tiempo.
* Criterios de calificación: Top 50 por capitalización de mercado según Gecko/CMC

#### CAPM\_MEDIA

* Título: ctivo de capitalización de mercado y volatilidad media
* Explicación: La capitalización de mercado de la criptomoneda afecta directamente a lo arriesgado que es tenerla. Por lo general, una pequeña capitalización de mercado implica una alta volatilidad y baja liquidez. El activo que posee este vault tiene una capitalización de mercado media. Esto significa que es un activo potencialmente seguro. El activo tiene potencial para mantenerse y crecer con el tiempo.
* Criterios de calificación: Entre el top 50 y 300 por capitalización de mercado según Gecko/CMC

#### CAPM\_BAJA

* Título: Activo de pequeña capitalización de mercado y alta volatilidad
* Explicación: La capitalización de mercado de la criptomoneda afecta directamente a lo arriesgado que es tenerla. Por lo general, una pequeña capitalización de mercado implica una alta volatilidad y baja liquidez. El activo que posee este vault tiene una capitalización de mercado pequeña. Esto significa que es un activo potencialmente riesgoso. El activo tiene un bajo potencial para mantenerse y crecer en el tiempo.
* Criterios de calificación: Entre el top 300 y 500 por capitalización de mercado según Gecko/CMC

#### CAPM\_DIMINUTA

* Título: Activo de capitalización de mercado diminuta y extrema volatilidad
* Explicación: La capitalización de mercado de la criptomoneda afecta directamente a lo arriesgado que es tenerla. Por lo general, una pequeña capitalización de mercado implica una alta volatilidad y baja liquidez. El activo que posee este vault tiene una capitalización de mercado diminuta. Esto significa que es un activo potencialmente muy arriesgado. El activo tiene un muy bajo potencial de mantenerse en el tiempo.
* Criterios de calificación: Top +500 por capitalización de mercado según Gecko/CMC

### Subcategoría: Suministro

Indica los riesgos relacionados con el suministro del activo. ¿Puede ser alterado por cualquiera? ¿Qué grado de centralización tiene?

#### SUMINISTRO\_CENTRALIZADO

* Título: Pocas y muy poderosas ballenas
* Explicación: Cuando el suministro se concentra en unas pocas manos, éstas pueden afectar enormemente al precio vendiendo. Las ballenas pueden manipular el precio de la moneda. Cuantas más personas tengan interés sobre una moneda, mejor y más orgánica es la acción del precio.
* Criterios de calificación: Menos de 50 cuentas tienen más del 50% de el suministro.

## Categoría: Riesgos de la plataforma

Riesgos relacionados con las plataformas de terceros utilizadas por el vault. Cuánto tiempo de experiencia tienen, cuán sólido es el código, hay acciones peligrosas que un administrador pueda realizar, etc. El sesenta por ciento (60%) de la puntuación está determinada por esta categoría.

### Subcategoría: Reputación

Intenta dar pistas sobre la trayectoria del equipo y la comunidad. Por ejemplo, cuál es la probabilidad de que se produzca un rug pull.

#### PLATAFORMA\_CONSOLIDADA

* Título: La plataforma tiene una trayectoria conocida.
* Explicación: A la hora de participar en una granja, puede ser útil conocer el tiempo que lleva la plataforma y su grado de reputación. Cuanto más larga sea la trayectoria, más inversión tienen el equipo y la comunidad detrás del proyecto. Este vault cultiva un proyecto que ha existido durante muchos meses.
* Criterios de calificación: La granja subyacente ha existido durante al menos 3 meses.

#### PLATFORMA\_NUEVA

* Título: La plataforma es nueva y tiene poco recorrido
* Explicación: A la hora de participar en una granja, puede ser útil conocer el tiempo que lleva la plataforma y su grado de reputación. Cuanto más larga sea la trayectoria, más inversión tienen el equipo y la comunidad detrás del proyecto. Este vault cultiva un proyecto nuevo, con menos de unos pocos meses de vida.
* Criterios de calificación: La granja subyacente lleva menos de 3 meses en funcionamiento.

### Subcategoría: Seguridad

Indica las buenas prácticas de los contratos inteligentes.

#### SIN\_AUDITAR

* Título: La plataforma nunca ha sido auditada por auditores de confianza de terceros
* Explicación: Las auditorías son revisiones del código realizadas por un grupo de desarrolladores de terceros.
* Criterios de calificación: -

#### AUDITADO

* Título: La plataforma cuenta con una auditoría de al menos un auditor de confianza
* Explicación: Las auditorías son revisiones del código realizadas por un grupo de desarrolladores de terceros.
* Criterios de calificación: Una o más auditorías de un auditor con una trayectoria positiva en el espacio.

#### CONTRATOS\_VERIFICADOS

* Title: Todos los contratos relevantes son verificados públicamente
* Explicación: El código que se ejecuta en un contrato en concreto no es público por defecto. Los exploradores de bloques permiten a los desarrolladores verificar el código que hay por detrás de un contrato en concreto. Esta es una buena práctica porque permite a otros desarrolladores auditar que el código hace lo que se supone que debe hacer. Todos los contratos de terceros que utiliza este vault están verificados. Esto hace que sea menos riesgoso.
* Criterios de calificación: -

#### CONTRACTOS\_SIN\_VERIFICAR

* Título: Algunos contratos no están verificados
* Explicación: El código que se ejecuta en un contrato en concreto no es público por defecto. Los exploradores de bloques permiten a los desarrolladores verificar el código que hay por detrás de un contrato en concreto. Esta es una buena práctica porque permite a otros desarrolladores auditar que el código hace lo que se supone que debe hacer. Algunos de los contratos de terceros que utiliza este vault no están verificados. Esto significa que hay ciertas cosas que los desarrolladores de Beefy no han podido inspeccionar.
* Criterios de calificación: -

#### ADMIN\_CON\_BLOQUEO\_TEMPORAL

* Título: Las funciones peligrosas están detrás de un bloqueo temporal
* Explicación: A veces el propietario o administrador del contrato puede ejecutar ciertas funciones que podrían poner en peligro a los fondos del usuario. Lo mejor es evitarlas por completo. Si deben estar presentes, es importante mantenerlas detrás de un bloqueo temporal para avisar adecuadamente antes de usarlas. Este contrato tiene ciertas funciones administrativas peligrosas, pero al menos están detrás de un bloqueo temporal significativo.
* Criterios de calificación: Hay al menos una función presente que podría robar parcial o completamente los fondos del usuario. La función debe estar detrás de un bloqueo temporal de +6 horas.

#### ADMIN\_SIN\_BLOQUEO\_TEMPORAL

* Título: Las funciones peligrosas se encuentran sin un bloqueo temporal
* Explicación: A veces el propietario o administrador del contrato puede ejecutar ciertas funciones que podrían poner en peligro a los fondos del usuario. Lo mejor es evitarlas por completo. Si deben estar presentes, es importante mantenerlas detrás de un bloque temporal para avisar adecuadamente antes de usarlas. Este contrato tiene ciertas funciones administrativas peligrosas, y no hay un bloqueo temporal presente. Pueden ser ejecutadas en un momento dado.
* Criterios de calificación: Hay por lo menos una función presente que podría robar parcial o totalmente los fondos del usuario. La función no tiene protección de bloqueo temporal.

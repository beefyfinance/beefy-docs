# General

## ¿Está Beefy auditado?

Nuestro primer auditor fue DefiYield, que auditó el token $BIFI, el rewardpool (pool de recompensas) y todos los timelocks (bloqueos temporales).

Ahora Beefy también es auditado por Certik, que garantiza la solidez de nuestros contratos inteligentes y la seguridad de los fondos invertidos a través de Beefy. Certik ya ha realizado auditorías para proyectos como Ocean Protocol, Neo, Ontology y Waves.

Certik ha auditado algunas de las estrategias de inversión más complejas y reutilizables utilizadas en la plataforma. Esto garantiza la seguridad y solidez de importantes aspectos de la plataforma con los que interactúan la mayoría de nuestros usuarios.

[Todas las auditorías de Beefy pueden ser encontradas aquí.](https://github.com/beefyfinance/beefy-audits)

## ¿Qué es un optimizador de rendimiento?

Un optimizador de rendimiento es un servicio automatizado que busca obtener el máximo rendimiento posible sobre las inversiones cripto, de forma mucho más eficiente que si se intentara maximizar el rendimiento por medios manuales.

Cada vault tiene su propia estrategia de cultivo, que normalmente implica la reinversión de los activos depositados en pools de liquidez. Esto capitaliza la cantidad de intereses recibidos y aumenta la cantidad depositada en la que se basa el rendimiento. Un optimizador de rendimientos puede repetir este proceso hasta miles de veces al día.

Este método bastante simple es la razón principal detrás de los grandes APYs encontrados en Beefy. Las comisiones de capitalización se amortizan entre todos los participantes de el vault, lo que hace que sea más barato para el usuario.

## ¿Cuál es la diferencia entre APR y APY?

El APR (tasa de porcentaje anual) es el interés anual, menos las comisiones. No incluye los efectos de capitalización que se producen al reinvertir los beneficios. Si inviertes $100 con un APR del 100%, obtendrás $100 de beneficio en un año.

Sin embargo, si reinviertes tus beneficios con regularidad, podrás hacer interés compuesto con tus intereses. Esto, calculado a lo largo de un año, le da su APY (rendimiento porcentual anual). Cuanto más a menudo componga sus intereses, mayor será la diferencia entre el APR y el APY.

## ¿Cómo funciona el APY?

El APY es el rendimiento porcentual anual que ofrece una determinada inversión. Eso tiene en cuenta el interés compuesto, lo que te da una idea precisa de su rendimiento en comparación con el interés simple.

Es posible obtener grandes APYs con miles de porcentaje con inversiones que proporcionen rendimientos diarios del 1% o más. Debido a que las recompensas de su pool de liquidez se cultivan y se reinvierten constantemente, de forma que los intereses se componen en cantidades cada vez mayores.

## ¿Que significan Vault diario y trading diario?

![](../.gitbook/assets/vault-trading-daily.png)

“Trading daily” (Trading diario) significa cuánto aumentará el valor de tus tokens de liquidez. Los pools de liquidez comparten las comisiones de trading entre los proveedores de liquidez, tal y como introdujo el [modelo de liquidez de Uniswap](https://docs.uniswap.org/protocol/V2/concepts/advanced-topics/fees). “Trading daily” se ve afectado por el volumen de trading y el porcentaje de las comisiones de intercambio asignadas a los proveedores de liquidez.

“Vault daily” (Vault diario) significa cuánto aumentará tu cantidad de tokens en número. Debido a que el vault constantemente cosecha las recompensas y las reinvierte, la cantidad de tokens aumentará. “Vault daily” se ve afectado por las recompensas del yield farming (es decir, incentivos adicionales además de las comisiones de trading), como CAKE en Pancakeswap.

“Trading daily” y “Vault daily” se pueden multiplicar por 365 para calcular “Trading APR” y “Vault APR”. El APR del vault se convierte en APY para tener en cuenta el interés compuesto. El porcentaje total de APY mostrado se calcula de la siguiente manera:

$$
APY = (1 + vaultAPY) * (1 + tradingAPR) - 1
$$

Una herramienta práctica para convertir el APR en APY es: [APRtoAPY.com](https://www.aprtoapy.com/)

## ¿Cómo puedo contribuir a Beefy?

Beefy Finance es un proyecto impulsado por la comunidad desde el primer día. Si quieres unirte al creciente grupo de colaboradores, depende de en qué quieras trabajar. Tenemos plazas abiertas para desarrolladores de Solidity, o para desarrolladores que quieran quieran empezar una carrera en Solidity, además de plazas para estrategas que suministren nuevos vaults (y así ganar ingresos pasivos provenientes de las comisiones de estrategas). Beefy está en muchas cadenas y suelen haber oportunidades para vaults simples y complejos. . Puedes empezar con las más sencillas y luego progresar con las más difíciles a medida que crecen tus conocimientos en Solidity. No tienes que ser el mejor desde el principio, y ten por seguro que hay un riguroso proceso de revisión para garantizar la seguridad y la calidad. Puedes ponerte en contacto con nuestros estrategas principales en el [Discord de Beefy](https://discord.gg/yq8wfHd) en #strategy-devs.

A Beefy también le gustaría que la gente trabajara en proyectos no relacionados con la estrategia; prácticamente cualquier cosa que se te ocurra puede ser formulada en una subvención. Habla con otros en la comuunidad sobre proyectos y únete a uno de los equipos, o lidera uno tú mismo. Puedes ser pagado por cualquier trabajo que hagas para mejorar Beefy. Una lista rápida de subvenciones anteriores: [aquí](https://forum.beefy.finance/c/grant-ideas/11) y [aquí](https://forum.beefy.finance/c/grant-requests-b1/10). Beefy V2 es un proyecto en curso que requiere todo tipo de desarrolladores, no sólo técnicos; la aportación del diseño es crucial para mejorar la UI/UX.

El [GitHub](https://github.com/beefyfinance) de Beefy adopta la idea de la colaboración abierta, de ahí que muchos de los repositorios sean de código abierto. Utilizamos archivos CONTRIBUTING.md para permitir que la gente haga contribuciones o recomendaciones mediante Pull-Requests. Puedes empezar incluso sólo actualizando los documentos Git o corrigiendo un error tipográfico, esto te ayudará a acercarte al equipo de colaboradores.

Si tienes interés en el desarrollo de negocios, podrías ayudar con asociaciones y proponer decisiones de negocios a la DAO. Beefy es todavía u negocio relativamente nuevo que puede utilizar personas con talento para ayudar a asesorar al equipo principal.

También puedes contribuir al marketing, si puedes escribir un tuit decente, puedes ayudar en el desarrollo de tuits. El [Discord](https://discord.gg/yq8wfHd) tiene un canal #social-watch donde se publican los enlaces a las menciones de Beefy en las redes sociales, puedes ayudar con las consultas de los usuarios allí o en el propio [Discord](https://discord.gg/yq8wfHd) o [Telegram](https://t.me/beefyfinance). Los moderadores de Discord y Telegram también son puestos remunerados (de forma variable) y suelen ser la primera línea de atención al cliente.

La mejor manera de involucrarse es simplemente empezar, ayudar en lo que puedas, contribuir a las discusiones y colaborar con todos.

## ¿Por qué cuesta tanto gas depositar en un vault de Beefy?

Muchos de los vaults de Beefy “cosechan al depositar”. Esto significa que cuando depositas en el vault, también estás llamando a la función de cosecha. Llamar a la función de Cosecha es más complejo que un simple depósito y, por lo tanto, tiene un límite de gas/tarifa más alto. Beefy hace esto para que sea imposible para los actores maliciosos robar el rendimiento, por lo que no se requiere una comisión de retiro. Esto beneficia enormemente a los inversores de largo plazo.

Casi todos los vaults en cadenas más económicas como Fantom y Polygon cosechan al depositar. También se puede saber si un vault cosecha al depositar si no tiene comisión por retiro.

Como llamador de la cosecha, también recibirás algunos tokens wrappeados de la cadena nativa como recompensa por llamar a la cosecha. Ver[beefy-finance-fees-breakdown.md](../ecosystem/beefy-bulletins/beefy-finance-fees-breakdown.md "mention") para más información sobre el Llamador de Cosechas.

## ¿Cómo puedo saber cuántos ingresos he acumulado?

Tus recompensas se añaden a la cantidad de tokens depositados en cada ciclo de cosecha y capitalización. Puedes utilizar un programa de control DeFi que será capaz de calcular exactamente cuánto beneficio has obtenido de tus inversiones. Herramientas externas como [TopDeFi](https://thetopdefi.com/) leerán la dirección de tu wallet y te darán una imagen precisa de tu inversión inicial y de las ganancias actuales.

---
description: >-
  En esta guía encontrarás los pasos necesarios para comprobar la tasa de
  recolección y capitalización de un vault.
---

# Cómo comprobar la tasa de recolección y capitalización de un vault

Los [vaults](../../ecosystem/products/vaults.md) de Beefy Finance, o más específicamente la estrategia de inversión vinculada al vault, aumentará automáticamente la cantidad de tu activo depositado convirtiendo las recompensas arbitrarias del yield farming en más de ese activo. Este ciclo constante de recolección de recompensas, y la capitalización, por lo general ocurre varias veces al día. En esta guía te guiaremos a través de los pasos para comprobar con precisión la frecuencia con la que se produce la capitalización.

## Guía

NOTA: Independientemente de la cadena que elija, puedes utilizar el [tablero de Beefy](https://dashboard.beefy.finance/) para realizar tu investigación.

### Ejemplo con la Binance Smart Chain (BSC)

Elijamos el vault CAKE-BNB LP en la Binance Smart Chain para demostrarlo:

![Captura de pantalla tomada el 5 de mayo de 2021](../../.gitbook/assets/cake-bnb-lp-2-5-2021.png)

#### 1. Ir al [tablero de Beefy.Finance](https://dashboard.beefy.finance/)

Este tablero elije qué estadísticas y vaults mostrar en función de la blockchain a la que esté conectada tu waller (por ejemplo, Metamask). Así que si no está ahora en BSC, simplemente cambia a esa red y la página del tablero se actualizará para mostrar las estadísticas y los depósitos de Beefy en BSC.

#### 2. Busca el contrato del vault que desees inspeccionar y haz click en él, abriendo una página en el explorador de bloques de BscScan

![](../../.gitbook/assets/cake-bnb-lp-vault-address.png)

#### 3. En la página de BscScan abre la pestaña "Contrato" y posteriormente la pestaña "Leer contrato"

![](../../.gitbook/assets/cake-bnb-lp-read-contract-tab.png)

#### 4. Desplázate hacia abajo para encontrar el contrato de la estrategia y haz click en él

![](../../.gitbook/assets/cake-bnb-lp-strategy-address.png)

#### 5. Haz click en la pestaña "Eventos" para ver los eventos de la estrategia que se han disparado

![](<../../.gitbook/assets/harvest events inspection.png>)

Los eventos “StratHarvest” son aquellos donde las recompensas del farming de los LPs son recolectadas y a su vez compuestas en más LPs subyacentes, o sea el activo depositado inicialmente, y luego redepositado en el vault de Beefy. Como reflejan las marcas de tiempo, este vault CAKE-BNB se autocompone aproximadamente una vez por hora.

### Otras cadenas (excepto Harmony, Celo y Cronos)

Cada una de las cadenas soportadas por Beefy puede ser investigada a través del mismo método mostrado anteriormente para la BSC. La única diferencia será el explorador de bloques que se use. Por ejemplo, en Polygon, se usará PolygonScan.

### Harmony, Celo y Cronos

El método básico que se muestra en el ejemplo de la BSC sigue siendo válido, excepto el último paso clave, el 5. Esto se debe a que estas cadenas utilizan diferentes softwares de exploración de bloques. En estos casos, el paso 5 cambia a la pestaña “Transacciones” para ver los eventos de las estrategias que se han disparado, como se ejemplifica a continuación.

![](../../.gitbook/assets/Avalanche-harvest-events.png)

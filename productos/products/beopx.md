---
description: Wrapped OPX de Beefy.
---

# beOPX

## Introducción

## ¿Qué es OPX?

OPX es el token nativo de OPX Finance, un intercambio descentralizado spot y perpetuo nativo de Optimism. El token OPX se utiliza para recompensar a los titulares con una parte de los ingresos del protocolo, al mismo tiempo que proporciona derechos de voto para su uso en la gobernanza del protocolo. OPX ha adoptado un modelo de suministro fijo de tokens, aunque el token OPX actual incorpora métodos de acuñación y quema.

OPX ofrece una forma novedosa de tokenómica de custodia de voto para su gobernanza y mecánica de participación en las ganancias. Esto requiere que los titulares apuesten y bloqueen tanto sus tokens OPX como un NFT de OPX con el protocolo. A cambio, los titulares reciben veOPX, que refleja los derechos del titular para participar en la gobernanza y las ganancias del protocolo. Los NFT de OPX solo se pueden obtener de una caja misteriosa de OPX (o venta de terceros) y se acuñan con un nivel aleatorio, que determina el porcentaje de impulso aplicado a la veOPX del titular.

El mecanismo de gobernanza clave de veOPX es decidir la distribución de los tokens OPX entre: (1) proveedores de liquidez de OPX (OLP); (2) participación en las ganancias de los titulares de OPX; (3) liquidez propiedad del protocolo OPX; (4) tesorería de desarrolladores de OPX; (5) programa de recompra y quema de OPX; y (6) devolución de ganancias a DarkCrypto DAO, los creadores de OPX. El staking y votación de OPX se pueden hacer a través de la aplicación web de OPX.

veOPX no es transferible y la cantidad que tiene un usuario disminuye constantemente hasta cero a medida que el período de bloqueo se acerca a su finalización. Los usuarios tampoco pueden liquidar ni transferir sus posiciones bloqueadas de OPX hasta el final del bloqueo temporal.

### ¿Qué es beOPX?

beOPX es una versión de OPX custodiada por Beefy y stakeada para veOPX para aprovechar los diversos beneficios que se ofrecen a los titulares de OPX. Como Beefy tiene un NFT de OPX de rareza de nivel superior (nivel 5), beOPX brinda a los titulares acceso a la máxima participación en las ganancias aumentadas, que de lo contrario está reservada para los pocos afortunados que adquieren un NFT similarmente raro.

El token está respaldado completamente en una proporción de 1:1 con OPX y se puede canjear por OPX en reserva. Esta reserva se llena en varias circunstancias:&#x20;

1. cuando los nuevos usuarios depositan OPX en beOPX, si el monto de reserva requerido es inferior en ese momento;&#x20;
2. cuando el contrato cosecha los ingresos del protocolo de OPX, si el monto de reserva requerido es inferior en ese momento; o&#x20;
3.  si el OPX stakeado del contrato se deja desbloquear gradualmente.

    <figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p>beOPX está diseñado para capturar la máxima cantidad posible de recompensas y beneficios de los tokenómics de OPX.</p></figcaption></figure>

### ¿Cómo puedo conseguir beOPX?

Puedes crear be OPX en la página del vault de beOPX a una ratio de 1:1. No hay liquidez incentivada para beOPX, en su lugar habrá una reserva de retiro.

## ¿Cómo funciona el beOPX?

Cuando se crea beOPX, el contrato intentará inmediatamente stakear y bloquear el OPX depositado en veOPX, siempre que se mantenga el monto de reserva requerido.

Si las reservas de OPX del contrato al momento de la creación superan el monto de reserva requerido (que actualmente es del 30% de veOPX del contrato), el contrato puede stakear cualquier exceso de OPX en veOPX. Si las reservas de OPX son inferiores al monto de reserva requerido, entonces el OPX depositado se agregará a la reserva para cubrir el déficit actual.

Una vez que el OPX del contrato está stakeado y bloqueado en veOPX, recibe una proporción de los ingresos del protocolo de OPX que se han asignado a los stakers, junto con la capacidad de votar sobre las distribuciones futuras de los ingresos del protocolo entre las diferentes opciones disponibles.

Dado que el contrato de beOPX vuelve a bloquear perpetuamente sus depósitos de OPX, siempre busca la máxima cantidad de poder de voto e ingresos del protocolo. Los ingresos obtenidos se cosechan regularmente, se intercambian por beOPX y se vuelven a depositar en la bóveda de beOPX para acumular automáticamente el rendimiento para los stakers de beOPX.



## ¿Cómo puedo ganar con mi beOPX?

Una vez que tienes beOPX, puedes stakearlo en nuestra bóveda de beOPX para ganar más beOPX.

Donde nuestro contrato de beOPX gana ingresos del protocolo al desplegar su veOPX en el protocolo, esos ingresos del protocolo se intercambian de vuelta a beOPX y se vuelven a depositar en la bóveda de beOPX para dar lugar a un efecto de acumulación automática. Esto maximiza el rendimiento para los holders de beOPX por encima de lo que podrían obtener solos del protocolo.

## ¿Y qué hay de las tarifas?&#x20;

Beefy se esfuerza por mantener algunas de las tarifas más bajas para la optimización de rendimiento y cobra tarifas estándar en sus bóvedas beOPX.

## ¿Cómo mantiene beOPX su peg?&#x20;

No se proporciona liquidez para beOPX, por lo que siempre estará en una proporción de 1:1 con OPX. Los usuarios pueden quemar beOPX por OPX mientras dure la reserva sin afectar el peg.

## ¿Cómo puedo recuperar mi OPX?&#x20;

Mientras haya tokens OPX disponibles en la reserva, podrás quemar tus tokens beOPX existentes (hasta el monto de la reserva) para recibir una cantidad equivalente de OPX.&#x20;

En caso de que la reserva no tenga suficientes tokens OPX para facilitar la retirada solicitada, solo podrás retirar hasta el monto de la reserva. Los usuarios pueden esperar hasta la próxima cosecha de ingresos del protocolo, que volverá a llenar la reserva y les permitirá quemar sus beOPX. De lo contrario, el mecanismo de bloqueo de OPX no incluye un mecanismo de liberación de emergencia.&#x20;

Como el monto requerido en la reserva está vinculado al monto de veOPX que posee el contrato, y todos los saldos de veOPX disminuyen con el tiempo a medida que disminuye el tiempo restante hasta que se desbloquee, el monto de la reserva requerido también disminuirá naturalmente con el tiempo hasta que se extienda el bloqueo de veOPX. Por lo tanto, y suponiendo que no se realicen más depósitos de OPX para reponer la reserva, el monto requerido en la reserva disminuirá gradualmente con el tiempo, lo que significa que la cantidad de OPX disponibles para retirar aumentará constantemente.

## ¿Puedo votar con mi beOPX?&#x20;

No. Todo el poder de voto de OPX será utilizado por Beefy para votar en los incentivos semanales de los pools de liquidez.

####

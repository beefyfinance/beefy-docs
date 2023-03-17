---
description: Wrapped VELO de Beefy.
---

# beVELO

## Introducción

## ¿Qué es VELO?

VELO es el token nativo de Velodrome Finance, un mercado descentralizado de trading y liquidez nativo de la cadena de bloques Optimism. Recompensa a los holders con una parte de los ingresos de la plataforma y también actúa como token de gobernanza para su indicador semanal de incentivos para la piscina. VELO tiene un suministro fijo y un modelo de emisiones en decadencia.

Los usuarios pueden stakear y bloquear sus tokens VELO en Velodrome por un período fijo de entre 1 semana y 4 años, para recibir un NFT de custodia de voto ("veNFT"), que se utiliza para registrar la cantidad de veVELO que posee el usuario. Los titulares de veVELO reciben tres beneficios: (1) una parte de los trading fees de swaps que utilizan las piscinas de liquidez de la plataforma; (2) la capacidad de dirigir las emisiones de VELO distribuidas a los proveedores de liquidez de la plataforma; y (3) la oportunidad de ganar sobornos de partes externas votando por sus piscinas de liquidez incentivadas. La apuesta de VELO se puede hacer a través de la aplicación web de Velodrome.

veVELO no es transferible y la cantidad que posee un usuario disminuye constantemente hasta cero a medida que el período de bloqueo se acerca a su finalización. Los usuarios tampoco pueden liquidar ni transferir sus posiciones de VELO bloqueadas hasta el final del bloqueo temporal.

### ¿Qué es beVELO?

beVELO es una versión de VELO garantizada por Beefy y depositada para obtener los diversos beneficios ofrecidos a los stakers de Velodrome.&#x20;

El token está respaldado totalmente en una proporción de 1:1 por VELO y se puede canjear por VELO guardado en reserva. Esta reserva se llena en varias circunstancias:&#x20;

1. cuando nuevos usuarios depositan VELO en beVELO, si está por debajo de la cantidad de reserva requerida en ese momento;&#x20;
2. cuando el contrato cosecha comisiones de trading y sobornos de Velodrome (que ocurre después de que la época cambia el jueves a las 00:00 UTC), si está por debajo de la cantidad de reserva requerida en ese momento; o&#x20;
3. si el VELO stakeado del contrato se deja desbloquear gradualmente.

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>beVELO está diseñado para capturar la máxima cantidad posible de recompensas y beneficios de los tokenómics de Velodrome.</p></figcaption></figure>

### ¿Cómo puedo conseguir beVELO?

Puedes crear beVELO en la página del vault de beVELO a una ratio de 1:1. No hay liquidez incentivada para beVELO, en su lugar habrá una reserva de retiro.

## ¿Cómo funciona el beVELO?

Cuando se crea beVELO, el contrato inmediatamente intentará stakear y bloquear el VELO depositado en veVELO, sujeto al mantenimiento de la reserva requerida.

Si las reservas de VELO del contrato en el momento de la creación superan la cantidad de reserva requerida (que actualmente es del 20% de la veVELO del contrato), el contrato puede stakear cualquier exceso de VELO en veVELO. Si las reservas de VELO están por debajo de la cantidad de reserva requerida, entonces el VELO depositado se agregará a la reserva para cubrir el déficit actual.&#x20;

Una vez que el VELO del contrato está stakeado y bloqueado en veVELO, recibe tres beneficios: (1) una parte de las tarifas de negociación de los pools de liquidez de la plataforma; (2) la capacidad de dirigir las emisiones de VELO distribuidas a los stakers del pool de liquidez; y (3) la oportunidad de ganar sobornos de partes externas votando por sus pools de liquidez incentivados.

Como el contrato de beVELO perpetuamente vuelve a bloquear sus depósitos de VELO, siempre se esfuerza por obtener la máxima cantidad de poder de voto y beneficios. Las tarifas de negociación y los sobornos ganados se cosechan regularmente, se intercambian por beVELO y se vuelven a depositar en el vault de beVELO para aumentar el rendimiento para los stakers de beVELO.



## ¿Cómo puedo ganar con mi beVELO?

Una vez que tengas beVELO, puedes stakearlos en nuestro vault de beVELO para ganar más beVELO.&#x20;

Donde nuestro contrato de beVELO gana tarifas de negociación y sobornos al implementar su veVELO en el protocolo, esas ganancias del protocolo se intercambian por beVELO y se vuelven a depositar en el vault de beVELO para generar un efecto de interés compuesto.&#x20;

Esto maximiza el rendimiento para los tenedores por encima de lo que podrían obtener solo del protocolo.



<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>beVELO se puede depositar en nuestro vault de beVELO, donde las ganancias de stakear el VELO del contrato en veVELO se vuelven a depositar y se autocompound.</p></figcaption></figure>

## ¿Y qué hay de las tarifas?&#x20;

Beefy se esfuerza por mantener algunas de las tarifas más bajas para la optimización de rendimiento y cobra tarifas estándar en sus bóvedas beVELO.

## ¿Cómo mantiene beVELO su peg?&#x20;

No se proporciona liquidez para beVELO, por lo que siempre estará en una proporción de 1:1 con VELO. Los usuarios pueden quemar beVELO por VELO mientras dure la reserva sin afectar el peg.

## ¿Cómo puedo recuperar mi VELO?&#x20;

Mientras haya tokens VELO disponibles en la reserva, podrás quemar tus tokens beVELO existentes (hasta el monto de la reserva) para recibir una cantidad equivalente de VELO.&#x20;

Si la reserva no tiene suficientes tokens VELO para facilitar la retirada solicitada, solo podrás retirar hasta el monto de la reserva. Los usuarios pueden esperar hasta la próxima recolección de tarifas de negociación y sobornos, que rellenará la reserva y les permitirá quemar sus beVELO. De lo contrario, el mecanismo de bloqueo de Velodrome no incluye un mecanismo de liberación de emergencia.

Dado que el monto de reserva requerido está vinculado a la cantidad de veVELO que tiene el contrato, y todos los saldos de veVELO disminuyen con el tiempo a medida que el tiempo restante hasta el desbloqueo disminuye, el monto de reserva requerido también disminuirá naturalmente con el tiempo hasta que se extienda el bloqueo de veVELO. Como tal, y suponiendo que no se realicen más depósitos de VELO para reponer la reserva, el monto de la reserva requerida disminuirá gradualmente con el tiempo, lo que significa que la cantidad de VELO disponible para retirar aumentará constantemente.

## ¿Puedo votar con mi beVELO?&#x20;

No. Todo el poder de voto de VELO será utilizado por Beefy para votar en los incentivos semanales de los pools de liquidez.

&#x20;Los votos normalmente serán dirigidos a los pools de liquidez que ofrezcan la mayor cantidad de trading fees y bribes, o a los pools de liquidez que apoyen nuestro token BIFI (por ejemplo, BIFI-OP LP). El contrato de beVELO cosechará todos los trading fees y bribes del protocolo y los intercambiará por más VELO para autocompensar en la bóveda de beVELO (aumentando así el rendimiento para los holders). La votación en los pools de liquidez incentivados de Velodrome tiene lugar en su aplicación web.&#x20;

Si estás interesado en proponer un soborno a Beefy, por favor, ponte en contacto con el equipo principal en Discord, Telegram o Twitter para obtener más información.



####

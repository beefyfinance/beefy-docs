---
description: Wrapped Qi de Beefy.
---

# beQI

## Introducción

## ¿Qué es Qi?

Qi es el token nativo de Mai Finance, un protocolo de deuda colateralizada nativo de la cadena de bloques de Polygon.

&#x20;Mai Finance está gobernado por QiDao, para el cual Qi es el token de gobernanza. Qi también se puede utilizar para participar en una parte de los ingresos del protocolo.

&#x20;Qi tiene un suministro fijo y un modelo de emisiones en decadencia. Los usuarios pueden stakear Qi para ganar eQi y recibir una participación potenciada de hasta 4 veces en los ingresos del protocolo y en el poder de voto de gobernanza.

### ¿Qué es beQI?

beQI es una versión de QI en Beefy, stakeada para ganar eQi, para aumentar la proporción de los ingresos del protocolo Mai Finance que Beefy gana y para participar en votaciones de incentivos de bóveda.&#x20;

El token está respaldado completamente en una proporción 1:1 por Qi y se puede canjear por Qi en reserva. Esta reserva se llena cuando los nuevos usuarios depositan (si está por debajo del monto de reserva requerido en ese momento), o la cantidad de reserva requerida disminuye gradualmente a medida que el eQi del contrato disminuye gradualmente y se desbloquea.

### ¿Cómo puedo conseguir beQI?

Puedes mintear beQI en su respectiva bóveda o la piscina de ganancia, a 1:1. no hay liquidez incentivada para beQI, por lo que para retirar deberás utilizar las reservas en nuestra página.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>beQI es minteado o quemado 1:1 en relación a Qi</p></figcaption></figure>

## ¿Cómo funciona el beQI?

Cuando creas beQI, el contrato inmediatamente intenta stakear y bloquear el Qi depositado en eQi, siempre y cuando se mantenga la reserva requerida.&#x20;

Si las reservas de Qi del contrato en el momento de la creación superan el monto de reserva requerido (que actualmente es del 20% del eQi del contrato), el contrato puede stakear cualquier exceso de Qi en eQi. Si las reservas de Qi están por debajo del monto de reserva requerido, entonces el Qi depositado se agregará a la reserva para cubrir la escasez actual.&#x20;

Una vez que el Qi del contrato se stakea y se bloquea en eQi, recibe dos beneficios: (1) recompensas de ingresos del protocolo semanalmente potenciadas; y (2) derechos de voto en la gobernanza de QiDao y en las votaciones de incentivos de bóveda. El enfoque de Beefy para votar por beQI se detalla a continuación.&#x20;

Los ingresos del protocolo de Mai Finance se pagan semanalmente y actualmente incluyen el 100% de todas las recompensas de agricultura de los ingresos de tarifas de depósito del protocolo, que se utilizan para la agricultura de Qi-MATIC, junto con el 30% de las tarifas de pago de deuda para todos los tipos de garantías (además de un bono semanal del 25%). Las recompensas individuales pueden aumentarse hasta 4 veces cuando un usuario tiene la cantidad máxima de eQi (es decir, ha bloqueado su Qi durante 4 años).&#x20;

Como el contrato de beQI perpetuamente vuelve a bloquear sus depósitos de Qi, siempre se esfuerza por obtener el máximo recompensado. Todas nuestras recompensas recibidas se distribuyen luego en nuestra bóveda y piscina de ganancias de Beefy beQI para beneficio de los titulares de beQI.



## ¿Cómo puedo ganar con mi beQI?

Una vez que tienes beQI, hay un par de opciones disponibles. Puedes:&#x20;

1. Stakear en la bóveda beQI para ganar más beQI; o&#x20;
2. Stakear en la piscina de ganancias de beQI para ganar Qi.&#x20;

Dado que los ingresos del protocolo de eQi potenciados se pagan en tokens Qi, estos pueden ser pagados a los titulares de beQI ya sea directamente en Qi (a través de la piscina de ganancias) o mediante la capitalización de beQI (a través de la bóveda) al crear más beQI con las recompensas de Qi.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption><p>beQI puede recibir ganancias en QI o más beQI</p></figcaption></figure>

## ¿Cómo funciona la estrategia de beQI?

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

## ¿Y qué hay de las tarifas?&#x20;

Beefy se esfuerza por mantener algunas de las tarifas más bajas para la optimización de rendimiento y cobra tarifas estándar en sus bóvedas beQI.

## ¿Cómo mantiene beQI su peg?&#x20;

No se proporciona liquidez para beQI, por lo que siempre estará a 1:1 con Qi. Los usuarios pueden quemar beQI por Qi mientras dure la reserva sin afectar el peg.

## ¿Cómo puedo recuperar mi Qi?&#x20;

Mientras haya tokens Qi disponibles en la reserva, podrás quemar tus tokens beQI existentes (hasta el monto de la reserva) para recibir la misma cantidad de Qi.

&#x20;Si la reserva no tiene suficientes tokens Qi para facilitar la retirada solicitada, solo podrás retirar hasta el monto de la reserva. Desafortunadamente, el bloqueo de eQi tampoco incluye un mecanismo de liberación de emergencia, por lo que en este escenario los holders deberán esperar hasta que se reponga la reserva.&#x20;

Dado que la cantidad requerida de reserva está vinculada a la cantidad de eQi que posee el contrato, y todos los saldos de eQi disminuyen con el tiempo a medida que el tiempo restante hasta el desbloqueo disminuye, la cantidad de reserva requerida también disminuirá naturalmente con el tiempo hasta que se extienda el bloqueo de eQi. Como tal, y suponiendo que no se realicen más depósitos de Qi para reponer la reserva, la cantidad de reserva requerida disminuirá gradualmente con el tiempo, lo que significa que la cantidad de Qi disponible para retirar aumentará constantemente.

## ¿Puedo votar con mi beQi?&#x20;

Por el momento, no se puede votar con beQI. Todo el poder de voto de Qi es actualmente utilizado por Beefy para votar en el indicador semanal de incentivos de bóveda. Los votos se dirigirán típicamente a los tipos de garantía de Beefy (por ejemplo, mooBIFI Fantom), lo que recompensa a nuestros usuarios que depositan sus activos de Beefy como garantía en Mai Finance.&#x20;

En caso de que nuestros tipos de garantía preferidos no califiquen para el indicador de incentivos, también podemos optar por aceptar sobornos de partes externas. Los ingresos de todos los sobornos se distribuyen directamente a nuestros titulares de beQI. Si está interesado en proponer un soborno a Beefy, comuníquese con el equipo principal en Discord, Telegram o Twitter para obtener más información.

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>



####

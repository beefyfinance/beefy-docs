# Prácticas SAFU de Beefy

_"No confíes, verifica"_

## Nuevas granjas en Beefy

Antes de que una nueva granja sea lanzada en Beefy, el proyecto tiene que pasar un estricto conjunto de normas de SAFU (Seguridad):

* Los contratos han sido verificados en el explorador de bloques;
* Suficiente liquidez para intercambiar las recompensa de los tokens de las granjas;
* Las funciones de Rug/migrador se han eliminado por completo o se han bloqueado por el tiempo suficiente;
* Las tasas de emisión de tokens de granjas tienen que estar bloqueadas en el tiempo (si los pares de tokens de la granja están siendo almacenados en un vault);
* Todos los cambios en la implementación del proxy deben estar bloqueados en el tiempo.

## Nuevos vaults en Beefy

Nuestros estrategas siguen un procedimiento de prueba manual en cada nuevo vault antes de que se ponga en marcha. Esto es para asegurar que el vault funciona como se pretende y los fondos de los usuarios están siempre seguros.

1\. Depositar una pequeña parte del activo; \
2\. Retirar todo;\
3\. Depositar de nuevo, esperar 1 minuto y comprobar que `callReward()` no es 0;\
4\. Recolectar la estrategia;\
5\. Poner en pánico la estrategia;\
6\. Retirar el 50% mientras se  esta en pánico para asegurarse de que los usuarios puedan salir;\
7\. Intentar depositar, debería aparecer un error pero no enviar el depósito;\
8\. Reanudar la estrategia; \
9\. Depositar el 50% que ha sido retirado previamente y recolectar de nuevo.

## Mejoras en la estrategia

De vez en cuando, los estrategas de Beefy sacan una nueva estrategia innovadora, o las granjas de rendimiento cambian sus contratos de recompensa. En ese caso, los vaults de Beefy tienen la flexibilidad de adaptarse a estos cambios, y tienen la capacidad de intercambiar sus estrategias para que los usuarios no tengan que migrar sus fondos a un nuevo vault: se hace automáticamente mediante una actualización de la estrategia.

La nueva estrategia se despliega con un vault ficticio y se completan todas las pruebas manuales descritas anteriormente. Una vez superadas las comprobaciones, la nueva estrategia se asigna al vault. El vault recibe la propuesta de la nueva estrategia a través de una wallet de multi-sig (de múltiples firmas) y tiene que esperar hasta que el retraso del bloqueo temporal haya pasado antes de que el vault utilice la nueva estrategia.

## Pánico

A veces algo puede ir mal con la granja de rendimiento subyacente, y reaccionar rápidamente es de gran importancia. Las estrategias de Beefy tienen un guardián al que se le permite entrar en pánico, retirando así todos los fondos stakeados en la granja de vuelta al contrato de la estrategia y eliminando todas las autorizaciones. Esto asegura que los fondos estén siempre disponibles para que los stakers de Beefy los retiren en caso de emergencia.

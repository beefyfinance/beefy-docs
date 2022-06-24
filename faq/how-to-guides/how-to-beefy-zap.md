---
description: ¡Invertir en los vaults de Beefy con un solo click!
---

# Cómo utilizar Beefy Zap

Beefy ZAP te permite crear tokens proveedores de liquidez y hacer depósitos en vaults de Beefy con una sola transacción. ¡Ya no es necesario [añadir y quitar liquidez manualmente](how-to-add-remove-liquidity.md)! Beefy ZAP es una solución simple, rápida, barata y segura que elimina la necesidad de manejar las direcciones de los contratos de tokens o incluso salir del cómodo entorno de la aplicación de Beefy.

{% hint style="info" %}
Cuando utilices Zap, ¡comprueba siempre tu cotización! Aunque Zap te protege contra el deslizamiento del mercado (cambios de precio en el momento de la orden y en el momento de la ejecución), **no** te protege contra el impacto del precio (cuánto cambiará tu transacción el precio de los tokens en el pool de liquidez)
{% endhint %}

## Entrando a un vult de LP

Vamos a mostrar el funcionamiento de Beefy ZAP para el [vault BIFI-BNB LP](https://app.beefy.finance/#/bsc/vault/cakev2-bifi-bnb) de PancakeSwap

![Captura de pantalla tomada el 30 de mayo de 2021](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-rate.png)

Utilizando únicamente BNB como activo de entrada, dejaremos que Beefy ZAP cree los tokens BIFI-BNB LP y haga el depósito en la cámara.

### 1. Expandir la visión sobre el vault

Haz click en BIFI-BNB LP o en cualquier lugar del campo del vault para ampliarlo y ver las opciones de depósito y retirada.

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-dropdown.png)

### 2. Selecciona "BNB" en el menú desplegable de depósitos

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-zap-dropdown-menu.png)

BNB no requiere de aprobación para gastar, ya que es la moneda nativa de la Binance Smart Chain.

### 3. Introduce el importe de BNB y pulse "Depositar".

Actualmente tenemos 4,0685 BNB, y para tener suficiente para pagar los gastos de transacción, utilizaremos 4 BNB como máximo.

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-deposit.png)

¡Y eso es todo! Depósito completo:

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-deposit-done.png)

Beefy ZAP creó automáticamente liquidez en Pancakeswap y depositó BIFI-BNB LP en el vault. Podes consultar [ésta guía](how-to-check-harvesting-compounding-rate.md) para ver cuándo el vault cosechará las recompensas y las capitalizará en más tokens BIFI-BNB LP.

## Retirarse de un vault de LP

Beefy ZAP te permite también retirar y quitar tokens de LP de un vault. Vamos a mostrar cómo retirar de el vault BIFI-BNB LP y recibir sólo BIFI.

### 1. Selecciona "BIFI" en el menú desplegable de retirada

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-bifi-withdraw.png)

### 2. Haz click en "Approve" (aprobar)

y confirma la transacción.

### 3. Seleccione la cantidad de BIFI que desees recibir, o utiliza todos los tokens depositados.

Haz click en la cantidad de tokens depositados, y retirate.

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-bifi-withdraw-all.png)

¡Y eso es todo! Beefy ZAP devolvió 1,4794 BIFI a nuestra wallet, que podemos stakear en el vault BIFI Maxi, por ejemplo:

![](../../.gitbook/assets/beefy-zap-bifi-bnb-lp-bifi-proof.png)

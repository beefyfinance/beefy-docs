---
description: Wrapped SPIRIT de Beefy.
---

# binSPIRIT

## Introducción

### ¿Qué es inSPIRIT?

Cuando los usuarios bloquean sus tokens SPIRIT en SpiritSwap durante un período de entre 1 semana y cuatro años, reciben una cantidad proporcional de inSPIRIT. inSPIRIT no es transferible y la cantidad en la wallet del holder disminuye de forma constante hasta llegar a 0 cuando el bloqueo finaliza. Los holders de inSPIRIT pueden reclamar las comisiones de los ingresos del protocolo (variables semana a semana, pero que han llegado hasta el 80% APR) y recibir hasta una potenciación de 2,5 veces en las granjas. La potenciación depende del saldo de inSPIRIT del usuario en comparación con todos los demás titulares y de los fondos que haya depositado en la granja en comparación con el TVL de la misma. Además no podrá liquidar su posición hasta el final del bloqueo temporal.

### ¿Qué es binSPIRIT?

binSPIRIT es la versión wrappeada de SPIRIT, permitiendo a los holders ganar comisiones del protocolo SpiritSwap sin tener que bloquear su SPIRIT. Un usuario puede mintear binSPIRIT 1:1 usando SPIRIT a través de la interfaz de usuario en la página del vault de binSPIRIT, o puede obtener binSPIRIT comprándolo en un exchange. binSPIRIT puede ser stakeado en el vault de Beefy para obtener más binSPIRIT, o directamente en el pool de recompensas para recibir SPIRIT.

El SPIRIT utilizado para mintear binSPIRIT está bloqueado para inSPIRIT. Beefy utiliza este inSPIRIT para potenciar todos los vaults de Beefy SpiritSwap y votar por las emisiones de incentivos.

### ¿Cómo hace binSPIRIT para mantener su peg?

Si un usuario quiere liquidar su posición, podrá operar binSPIRIT en un exchange. A diferencia de inSPIRIT, los usuarios nunca están bloqueados y pueden salir en cualquier momento. Esto también significa que binSPIRIT no siempre está vinculado a SPIRIT, si no que mantendrá su peg (vínculo) suelto.

Si binSPIRIT va por debajo de su peg entonces las tasas del protocolo SpiritSwap comprarán más binSPIRIT por SPIRIT y el APY del vault de Beefy aumentará. El APY para el pool de recompensas también aumentaría, permitiendo a los usuarios comprar y stakear binSPIRIT por una proporción mucho mayor de las comisiones del protocolo SpiritSwap que si sólo bloquearan SPIRIT..

Si binSPIRIT supera el peg, los arbitradores mintearán binSPIRIT y lo venderán por un beneficio.

## ¿Cómo funciona el Staker Gauge?

El contrato Staker Gauge tiene dos partes notables: el bloqueo de SPIRIT para mintear binSPIRIT y el paso de tokens entre estrategias y gauges. El bloqueo del SPIRIT en el Staker Gauge permite que el contrato obtenga inSPIRIT intransferibles. Todas las estrategias de SpiritSwap para los gauges pasarán sus depósitos, retiros y recompensas de cosecha a través del Staker Gauge. Dado que todos los depósitos proceden de la dirección del Staker Gauge, se puede obtener el mayor potenciado en todos los gauges, ya que el contrato también posee el inSPIRIT concentrado.

#### Deposita SPIRIT para mintear binSPIRIT

Un usuario puede depositar SPIRIT (`want`) y el contrato confirmará la cantidad recibida comprobando los saldos antes y después de la transferencia. Si la cantidad recibida es distinta a cero, entonces se comprueba si existe un bloqueo para el SPIRIT, lo que es probable a menos que el bloqueo no se haya iniciado antes o se haya dejado expirar. Si el bloqueo existe entonces se extenderá a los 4 años enteros si el tiempo de bloqueo actual es menor que la cantidad completa, y el saldo recibido de SPIRIT se bloquea para obtener una cantidad 1:1 de inSPIRIT. Si no existe actualmente ningún bloqueo, se crea uno nuevo y se bloquea el balance de SPIRIT en el contrato. Por último mintea una cantidad de binSPIRIT igual a la cantidad recibida de SPIRIT del usuario.

```
// deposit 'want' and lock
function _deposit(address _user, uint256 _amount) internal nonReentrant whenNotPaused {
    uint256 _pool = balanceOfWant();    
    want.safeTransferFrom(msg.sender, address(this), _amount);
    uint256 _after = balanceOfWant();    
    _amount = _after.sub(_pool); // Additional check for deflationary tokens
    if (_amount > 0) {
        if (balanceOfVe() > 0) {
            increaseUnlockTime();
            veWant.increase_amount(_amount);        
        } else {            
            _createLock();
        }        
        _mint(_user, _amount);        
        emit DepositWant(balanceOfVe());    
    }
}
```

#### Vota por que gauges potenciar

El guardián de Beefy puede votar sobre los incentivos de los mediadores utilizando el balance de inSPIRIT en el Staker Gauge como poder de voto. Se utilizará principalmente para votar por los gauges de Beefy y de sus socios. La función de votación es una simple llamada al contrato Proxy Gauge de SpiritSwap que registra los votos y decide la distribución de los incentivos de los gauges. El guardián de Beefy puede dividir el poder de votación entre varios gauges en una sola llamada utilizando las matrices de parámetros.

```
// vote on boosted farms
function vote(address[] calldata _tokenVote, uint256[] calldata _weights) external onlyManager {    
    gaugeProxy.vote(_tokenVote, _weights);    
    emit Vote(_tokenVote, _weights);
}
```

#### Paso de tokens entre estrategias y gauges

Las estrategias de los vaults de SpiritSwap de Beefy deben pasar por sus depósitos, retiros y cosechas hacia y desde el Staker Gauge. Sólo una estrategia incluida en la lista blanca puede interactuar con el Staker Gauge, y a cada gauge se le asigna como máximo una estrategia.

Los depósitos y retiros pasan a través de una cantidad exacta que se solicita (`amount`) en el token que se asigna al gauge (`underlying`). Las cosechas (`claimGaugeReward()`) pasan a través de sólo la recompensa SPIRIT (`want`) que es recibida por el Staker Gauge al reclamar la recompensa, ignorando el balance existente en el Staker Gauge. Ninguno de los fondos se guarda en el Staker Gauge, siempre se pasan en la misma transacción.

```
// pass through a deposit to a gauge
function deposit(address _gauge, uint256 _amount) external onlyWhitelist(_gauge) {
    address _underlying = IGauge(_gauge).TOKEN();    
    IERC20Upgradeable(_underlying).safeTransferFrom(msg.sender, address(this), _amount);    
    IGauge(_gauge).deposit(_amount);
}
    
// pass through a withdrawal from a gauge
function withdraw(address _gauge, uint256 _amount) external onlyWhitelist(_gauge) {
    address _underlying = IGauge(_gauge).TOKEN();    
    IGauge(_gauge).withdraw(_amount);    
    IERC20Upgradeable(_underlying).safeTransfer(msg.sender, _amount);
}

// pass through rewards from a gauge
function claimGaugeReward(address _gauge) external onlyWhitelist(_gauge) {
    uint256 _before = balanceOfWant();
    IGauge(_gauge).getReward();
    uint256 _balance = balanceOfWant().sub(_before);
    want.safeTransfer(msg.sender, _balance);
}
```

#### Reclama las comisiones del protocolo SpiritSwap

Holdear inSPIRIT da al Gauge Staker el derecho a reclamar una parte de las tasas del protocolo de SpiritSwap, que se distribuirán a los stakers de binSPIRIT en un pool de recompensas. Las comisiones del protocolo se distribuyen una vez a la semana en forma de SPIRIT y deben reclamarse al contrato de Distribuidor de Comisiones. El contrato del Pool de Recompensas llamará a la función de reclamo a través de `claimVeWantRewards()`. Sólo la recompensa SPIRIT (`want`) se devuelve inmediatamente al pool de recompensas, si es que hay algo disponible para reclamar.

```
// pass through rewards from the fee distributor
function claimVeWantReward() external onlyRewardPool {    
    uint256 _before = balanceOfWant();    
    feeDistributor.claim();    
    uint256 _balance = balanceOfWant().sub(_before);    
    want.safeTransfer(msg.sender, _balance);
}
```

#### Estableciendo estrategias en la lista blanca

El Guardián de Beefy puede poner en la lista blanca una dirección de estrategia siempre que no haya una estrategia activa que tenga fondos suministrados en el mismo gauge que la nueva estrategia. Una estrategia antigua debe ser objeto de pánico antes de que se pueda probar una nueva estrategia para el mismo gauge, por lo que los fondos de los usuarios están siempre protegidos. La aprobación del token (`want`) asignado al gauge se restablece y se incrementa hasta el límite máximo de gasto por el gauge. El indicador se asigna a la estrategia de la lista blanca y la estrategia permite el acceso al Staker Gauge para el gauge especificado.

```
// whitelists a strategy address to interact with the Gauge Staker and gives approvals
function whitelistStrategy(address _strategy) external onlyManager {    
    IERC20Upgradeable _want = IGaugeStrategy(_strategy).want();    
    address _gauge = IGaugeStrategy(_strategy).gauge();    
    require(IGauge(_gauge).balanceOf(address(this)) == 0, '!inactive');    
    _want.safeApprove(_gauge, 0);    
    _want.safeApprove(_gauge, type(uint256).max);    
    whitelistedStrategy[_gauge] = _strategy;
}
```

#### Actualizando estrategias

Se puede proponer una nueva estrategia para un gauge con una estrategia existente una vez se haya probado completamente. `ProposeStrategy()` debería ser llamado en el Staker Gauge antes de `upgradeStrat()` en el vault para que el cambio tenga éxito. La nueva estrategia debe tener el mismo gauge que la estrategia anterior. `upgradeStrategy()` sólo se llama en `retireStrat()` en la estrategia anterior, por lo que se controla indirectamente por el propietario del vault a través de la actualización de la dirección de la estrategia en el vault.

```
// prepare a strategy to be retired and replaced with another
function proposeStrategy(address _oldStrategy, address _newStrategy) external onlyManager {    
    require(IGaugeStrategy(_oldStrategy).gauge() == IGaugeStrategy(_newStrategy).gauge(), '!gauge');    
    replacementStrategy[_oldStrategy] = _newStrategy;
}

// switch over whitelist from one strategy to another for a gauge
function upgradeStrategy(address _gauge) external onlyWhitelist(_gauge) {
    whitelistedStrategy[_gauge] = replacementStrategy[msg.sender];
}
```

## Contratos

* binSPIRIT/StakerGauge: [0x44e314190D9E4cE6d4C0903459204F8E21ff940A](https://ftmscan.com/address/0x44e314190D9E4cE6d4C0903459204F8E21ff940A)
* Pool de recompensas: [0xFAE44b30F6F9BbD44E6B7687471dd73D71FaBDC6](https://ftmscan.com/address/0xFAE44b30F6F9BbD44E6B7687471dd73D71FaBDC6)

Las funciones críticas se gestionan siempre a través de transacciones multi-sig (de múltiples firmas) y de bloqueos temporales. No se almacenan fondos directamente en el Staker Gauge y sólo la estrategia activa en la lista blanca puede interactuar con los fondos almacenados en un gauge.

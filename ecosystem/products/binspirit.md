---
description: Обернутый Beefy токен SPIRIT
---

# binSPIRIT

## Введение

### Что такое inSPIRIT?

Когда пользователи блокируют свои SPIRIT токены в SpiritSwap на период от 1 недели до 4-х лет, они получают взамен пропорциональное количество inSPIRIT токенов. inSPIRIT токены нельзя перевести кому-либо, а их количество уменьшается каждый день до 0, до тех пор, пока не истечет срок, на который они были заблокированы. Владельцы inSPIRIT токенов имеют право получать прибыль платформы от комиссий (это значение варьируется каждую неделю, но временами достигает 80% годовых), и получают множитель буста до 2.5х в  доходном фермерстве. Значение множителя буста зависит от двух факторов: соотношение суммы inSPIRIT токенов на кошельке пользователя с суммой inSPIRIT токенов у всех других пользователей; соотношение суммы заблокированных средств пользователя относительно общей суммы заблокированных средств (TVL) в доходном фермерстве. При этом вы не можете вывести токены SPIRIT до того момента, как не истечет период блокировки средств.&#x20;

### Что такое binSPIRIT?

binSPIRIT — это обернутая Beefy версия SPIRIT, которая позволяет пользователям получать прибыль платформы от комиссий без необходимости блокировать свои SPIRIT токены. Пользователь может выпустить binSPIRIT в обмен на SPIRIT при соотношении 1 к 1 через UI на странице хранилища binSPIRIT или просто купить binSPIRIT на бирже. binSPIRIT можно внести в хранилище Beefy, чтобы зарабатывать еще больше binSPIRIT, или же внести непосредственно в пул наград (reward pool), где вы будете получать токены SPIRIT.

#### Внесите SPIRIT, чтобы выпустить binSPIRIT

Пользователь может внести SPIRIT ( `want` ), а контракт подтвердит количество полученных токенов путем проверки баланса до и после перевода средств. Если количество полученных binSPIRIT токенов не равно нулю, то проверьте, есть ли на контракте заблокированные SPIRIT. Если их нет, то блокировка SPIRIT в контракте не была осуществлена либо период блокировки токенов уже истек. Если же токены были заблокированы, то период блокировки будет пролонгирован до максимальных 4-х лет, чтобы получить токены inSPIRIT за SPIRIT в соотношении 1 к 1. Если заблокированных токенов нет, то внесите токены SPIRIT и заблокируйте их в контракте. Наконец, выпустите равное количеству SPIRIT токенов, binSPIRIT.

```
/// deposit 'want' and lock
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

#### Голосуйте за то, какие пары доходного фермерства бустить

Контракт Beefy Keeper может голосовать при определении множителя буста, так как он использует баланс токенов inSPIRIT на контракте Gauge Staker в качестве права голоса. Главным образом, этот баланс будет использоваться для того, чтобы голосовать за пары доходного фермерства Beefy и пары наших стратегических партнеров. При этом сам контракт Beefy Keeper может управляться через Beefy DAO для голосования за поощрение различных пар доходного фермерства. Сама фукнция голосования осуществляется через запрос к контракту Gauge Proxy SpiritSwap, который фиксирует голоса и распределяет их по парам доходного фермерства. Контракт Beefy Keeper может распределить свои голоса на несколько различных пар в рамках одного запроса к контракту SpiritSwap, используя ряд парамметров.

```
// vote on boosted farms
function vote(address[] calldata _tokenVote, uint256[] calldata _weights) external onlyManager {    
    gaugeProxy.vote(_tokenVote, _weights);    
    emit Vote(_tokenVote, _weights);
}
```

#### Перевод токенов между стратегиями и парами доходного фермерства

Стратегии доходного фермерства Beefy для хранилищ, использующих платформу SpiritSwap, производят транзакции ввода, вывода средств и сбора прибыли через контракт Gauge Staker. Только авторизованные стратегии могут взаимодействовать с контрактом Gauge Staker. Каждой паре доходного фермерства присваивается как минимум одна стратегия.

По операциям ввода и вывода производится перевод точного количества (`_amount` ) в токенах пары доходного фермерства ( `_underlying` ). Сбор прибыли (`claimGaugeReward()`) проводится только  по SPIRIT (`want`), которые поступают от контракта Gauge Staker при сборе прибыли. При этом не учитывается текущий баланс на контракте Gauge Staker. Средства не хранятся на контракте Gauge Staker, они всегда проходят через него до конечного адресата в рамках единой транзакции.&#x20;

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

#### Сбор прибыли от комиссий, взимаемых платформой SpiritSwap

Владение токенами inSPIRIT наделяет контракт Gauge Staker правом собирать часть прибыли платформы SpiritSwap от комиссий. Эта прибыль затем распределяется между держателями токенов binSPIRIT в пуле наград. Распределение прибыли платформы происходит раз в неделю в форме SPIRIT токенов и требует запроса на сбор прибыли к контракту Fee Distributor. Контракт Reward Pool для сбора прибыли производит запрос через функцию `claimVeWantReward()`. Награда в SPIRIT (`want`) сразу же начисляется обратно на Reward Pool, если таковая доступна для сбора.

```
// pass through rewards from the fee distributor
function claimVeWantReward() external onlyRewardPool {    
    uint256 _before = balanceOfWant();    
    feeDistributor.claim();    
    uint256 _balance = balanceOfWant().sub(_before);    
    want.safeTransfer(msg.sender, _balance);
}
```

#### Авторизация стратегий

Контракт Beefy Keeper может авторизовать адрес стратегии в том случае, если к этому доходному фермерству не привязана другая стртатегия с внесенными средствами. Средства внесенные в старую стратегию должны быть выведены в экстренном порядке, чтобы была возможность запустить и протестировать новую стратегию доходного фермерства. Это делается для защиты средств пользователей. Разрешение на трату токенов (`_want`) доходного фермерства - сбрасывается, а затем увеличивается до предельного значения. Доходное фермерство обозначает стратегию как авторизованную, после чего стратегии дается доступ к контракту Gauge Staker для конкретной пары доходного фермерства.

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

#### Обновление стратегий

Новая стратегия для пары доходного фермерства, к которой уже привязана существующая стратегия, может быть предложена сразу же после ее всестороннего тестирования. Сначала производится запрос `proposeStrategy()`к контракту Gauge Staker, а затем `upgradeStrat()` применяется к хранилищу, чтобы произвести изменения. Новая стратегия должна быть привязана к тому же доходному фермерству, что и предыдущая. `upgradeStrategy()` применяется только к `retireStrat()` старой стратегии, следовательно контролируется опосредовано владельцем харинилища через обновление адреса стратегии хранилища.

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

### Адреса контрактов

* binSPIRIT /GaugeStaker: [0x44e314190D9E4cE6d4C0903459204F8E21ff940A](https://ftmscan.com/address/0x44e314190D9E4cE6d4C0903459204F8E21ff940A)
* Reward Pool: [0xFAE44b30F6F9BbD44E6B7687471dd73D71FaBDC6](https://ftmscan.com/address/0xFAE44b30F6F9BbD44E6B7687471dd73D71FaBDC6)

Критические функции защищены мультиподписью и задержками. Средства не хранятся непосредственно на контракте Gauge Staker, и только авторизованные стратегии могут взаимодействовать со средствам в доходном фермерстве.

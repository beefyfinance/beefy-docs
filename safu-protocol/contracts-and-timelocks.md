# Смарт-контракты и задержки

## Смарт-контракты

Все действующие контракты Beefy Finance могут быть найдены на [dashboard.beefy.finance](https://dashboard.beefy.finance/).

Эту панель управления можно использовать, например для того, чтобы посмотреть как часто [хранилище производит сбор прибыли и реинвестирование](https://github.com/Karen094/beefy-docs/blob/ed9a10ea254b8fe582932252b851b8e86e7e87df/faq/how-to-guides/how-to-check-harvesting-compounding-rate.md).

## Задержки

Смарт-контракты защищены задержками (обязательный период времени, который должен пройти до того, как внесенные ранее изменения вступят в силу), а изменения вносятся через кошелек с мультиподписью.

* Arbitrum (6 часов): [0х6d28afD25a1FBC5409B1BeFFf6AEfEEe2902D89F](https://arbiscan.io/address/0x6d28afD25a1FBC5409B1BeFFf6AEfEEe2902D89F)
* Avalanche (6 часов): [0x37DC61A76113E7840d4A8F1c1B799cC9ac5Aa854](https://snowtrace.io/address/0x37DC61A76113E7840d4A8F1c1B799cC9ac5Aa854)
* BSC (6 часов): [0x65CF7E8C0d431f59787D07Fa1A9f8725bbC33F7E](https://bscscan.com/address/0x65cf7e8c0d431f59787d07fa1a9f8725bbc33f7e)
* Celo (6 часов): [0x5B96bbAca98D777cb736dd89A519015315E00D02](https://explorer.celo.org/address/0x5B96bbAca98D777cb736dd89A519015315E00D02/transactions)
* Cronos (6 часов): [0x4f4DB83d75876f34fd927d5fa78D5D7b4479E6ce](https://cronoscan.com/address/0x4f4DB83d75876f34fd927d5fa78D5D7b4479E6ce)
* Fantom (6 часов): [0x847298aC8C28A9D66859E750456b92C2A67b876D](https://ftmscan.com/address/0x847298aC8C28A9D66859E750456b92C2A67b876D)
* Fuse (6 часов): [0xa9E6E271b27b20F65394914f8784B3B860dBd259 ](https://explorer.fuse.io/address/0xa9E6E271b27b20F65394914f8784B3B860dBd259/transactions)
* HECO (6 часов): [0x587479672077fBD7cb08EE1fd13fca6a9ef69d9e](https://hecoinfo.com/address/0x587479672077fBD7cb08EE1fd13fca6a9ef69d9e)
* Metis (6 часов): [0xdf68Bf80D427A5827Ff2c06A9c70D407e17DC041](https://andromeda-explorer.metis.io/address/0xdf68Bf80D427A5827Ff2c06A9c70D407e17DC041/transactions)
* Moonriver (6 часов): [0xc8BD4Ae3d3A69f0d75e3788d2ee557E66EBC98D8](https://moonriver.moonscan.io/address/0xc8BD4Ae3d3A69f0d75e3788d2ee557E66EBC98D8)
* Harmony One (6 часов): [0x6d28afD25a1FBC5409B1BeFFf6AEfEEe2902D89F](https://explorer.harmony.one/address/0x6d28afd25a1fbc5409b1befff6aefeee2902d89f)
* Polygon (6 часов): [0x6fd13191539e0e13b381e1a3770f28d96705ce91](https://polygonscan.com/address/0x6fd13191539e0e13b381e1a3770f28d96705ce91)

## Кошельки разработчиков с мультиподписью

Эти кошельки используются для внесения изменений в контракты, предназначенные для обновления стратегий хранилищ. Такая система обеспечивает непрерывный и безопасный рабочий процесс, в котором каждое изменение подтверждается разработчиками Beefy.

* Arbitrum: [0xf7EC8986c660Fa8269f6440A631B22337f398Ccd](https://gnosis-safe.io/app/arb1:0xf7EC8986c660Fa8269f6440A631B22337f398Ccd/balances)
* Avalanche: [0xf7EC8986c660Fa8269f6440A631B22337f398Ccd](https://gnosis-safe.io/app/avax:0x3A0b8B7a3ea8D1670e000b1Da5bD41373bF8da42/balances)
* BSC: [0x44b74ED902e6423B51Bd9e44B6e5646749376943](https://gnosis-safe.io/app/bnb:0x44b74ED902e6423B51Bd9e44B6e5646749376943/balances)
* Fantom: [0x238dc3781DD668abd5135e233e395885657D304A](https://safe.fantom.network/#/safes/0x238dc3781DD668abd5135e233e395885657D304A/balances)
* Fuse: [0xe26a8aC2936F338Fd4DAebA4BD22a7ec86465fE1](https://gnosis-safe.fuse.io/fuse:0xe26a8aC2936F338Fd4DAebA4BD22a7ec86465fE1/)
* Harmony: [0xE3c985f5e317eFd4aca1f00aa5F1DFEC40b2Af74](https://multisig.harmony.one/#/safes/0xE3c985f5e317eFd4aca1f00aa5F1DFEC40b2Af74/)
* Polygon: [0x09dc95959978800E57464E962724a34Bb4Ac1253](https://gnosis-safe.io/app/matic:0x09dc95959978800E57464E962724a34Bb4Ac1253/)
* Metis: [0xFf9810A3dA8a554B84Ed79D67461eCA6Eb3fA9BD](https://metissafe.tech/metis-andromeda:0xFf9810A3dA8a554B84Ed79D67461eCA6Eb3fA9BD)
* Moonriver: [0x1fdd00b45eba7f6d35b92803eaddd68f7cc4a193](https://multisig.moonbeam.network/mriver:0x1fdd00b45eba7f6d35b92803eaddd68f7cc4a193/)

## Казначейские (Treasury) кошельки с мультиподписью

Расходы из казны Beefy защищены механизмом мультиподписи, который предполагает необходимость подтверждения транзакции доверенными членами сообщества. [Согласно итогам голосования ДАО](https://vote-archive.beefy.finance/#/beefy/proposal/QmR5mzwjs46b3YRYWtc12CqqxF6r7VfpPd6ZfiRXnR69go) (децентрализованной автономной организации), следующие лица представляют Совет Казны: sirbeefalot, Pablo, mjoaris, TheBeefyCow, DefiDebauchery and YR2150.

* Fantom: [0xdFf234670038dEfB2115Cf103F86dA5fB7CfD2D2](https://safe.fantom.network/#/safes/0xdFf234670038dEfB2115Cf103F86dA5fB7CfD2D2/balances)
* BSC:[ 0x7C780b8A63eE9B7d0F985E8a922Be38a1F7B2141](https://gnosis-safe.io/app/bnb:0x7C780b8A63eE9B7d0F985E8a922Be38a1F7B2141/balances)
* Polygon: [0xe37dD9A535c1D3c9fC33e3295B7e08bD1C42218D](https://gnosis-safe.io/app/matic:0xe37dD9A535c1D3c9fC33e3295B7e08bD1C42218D/balances)
* Arbitrum: [0x3f5eddad52C665A4AA011cd11A21E1d5107d7862](https://gnosis-safe.io/app/arb1:0x3f5eddad52C665A4AA011cd11A21E1d5107d7862/balances)
* Harmony:[ 0x523154a03180FD1CB26F39087441c9F91BcD0389](https://multisig.harmony.one/#/safes/0x523154a03180FD1CB26F39087441c9F91BcD0389/balances)
* Moonriver:[ 0x617f12E04097F16e73934e84f35175a1B8196551](https://multisig.moonbeam.network/mriver:0x617f12E04097F16e73934e84f35175a1B8196551/balances)
* Fuse:[ 0x1C124c2CaB83b3C3B5D0f0899CeeA5e06964599F](https://gnosis-safe.fuse.io/fuse:0x1C124c2CaB83b3C3B5D0f0899CeeA5e06964599F/balances)
* Avalanche: [0x26dE4EBffBE8d3d632A292c972E3594eFc2eCeEd/balances](https://gnosis-safe.io/app/avax:0x26dE4EBffBE8d3d632A292c972E3594eFc2eCeEd/balances)
* Metis: [0x0f9602B7E7146a9BaE16dB948281BebDb7C2D095](https://metissafe.tech/metis-andromeda:0x0f9602B7E7146a9BaE16dB948281BebDb7C2D095/balances)

## Книга адресов

Все используемые адреса имеют открытый исходный код и доступны для проверки. В этом репозитории на GitHub можно найти ряд адресов сетей, созданных на базе Виртуальной Машины Эфириума (EVM), которые поддерживаются платформой Beefy и могут быть полезны для развития DeFi: [Книга Адресов](https://github.com/beefyfinance/beefy-api/tree/master/packages/address-book)

---
description: Tradução feita a partir da atualização de fevereiro de 2023
---

# API da Beefy

Esta página fornece mais detalhes sobre a funcionalidade e operação da API REST da Beefy, que sustenta nosso aplicativo web, painel e páginas em sites de terceiros.

Você pode acessar a API no [https://api.beefy.finance/](https://api.beefy.finance/), e o repositório público está disponível no [GitHub da Beefy](https://github.com/beefyfinance/beefy-api). A API é mantida sob a licença MIT, com mais detalhes disponíveis no [repositório GitHub](https://github.com/beefyfinance/beefy-api/blob/master/LICENSE).

## Endpoints

Nossa API oferece uma variedade de endpoints públicos que cobrem a seleção completa de dados necessários para nosso aplicativo web, back-end e painel, bem como alguns serviços de terceiros.

### Endpoints dos Cofres Beefy

Endpoints desenvolvidos para uso do [aplicativo Beefy](https://app.beefy.finance/) para exibir as características ao vivo e o desempenho dos cofres para nossos usuários.

<details>

<summary>GET /vaults</summary>

Fornece informações ao vivo sobre cada cofre Beefy, incluindo cofres aposentados (eol).&#x20;

As informações incluem campos para o nome/ID do cofre relevante, rede, token, ativos subjacentes, contratos relacionados e status atual. Ele também inclui o campo "riscos", que lista os recursos do cofre retirados da matriz de fatores de risco usada para calcular a pontuação de segurança de um cofre.

```json
// Sample response for the /vaults endpoint (e.g. Polygon aTriCrypto3 vault)

{
  "id": "curve-poly-atricrypto3",
  "name": "aTriCrypto3",
  "token": "crvUSDBTCETH3",
  "tokenAddress": "0xdAD97F7713Ae9437fa9249920eC8507e5FbB23d3",
  "tokenDecimals": 18,
  "tokenProviderId": "curve",
  "earnedToken": "mooCurveATriCrypto3",
  "earnedTokenAddress": "0x5A0801BAd20B6c62d86C566ca90688A6b9ea1d3f",
  "earnContractAddress": "0x5A0801BAd20B6c62d86C566ca90688A6b9ea1d3f",
  "oracle": "lps",
  "oracleId": "curve-poly-atricrypto3",
  "status": "active",
  "platformId": "curve",
  "assets": [
    "DAI",
    "USDC",
    "USDT",
    "WBTC",
    "ETH"
  ],
  "strategyTypeId": "multi-lp",
  "risks": [
    "COMPLEXITY_LOW",
    "BATTLE_TESTED",
    "IL_LOW",
    "MCAP_LARGE",
    "PLATFORM_ESTABLISHED",
    "AUDIT",
    "CONTRACTS_VERIFIED",
    "OVER_COLLAT_ALGO_STABLECOIN"
  ],
  "addLiquidityUrl": "https://polygon.curve.fi/atricrypto3/deposit",
  "network": "polygon",
  "createdAt": 1652662923,
  "chain": "polygon",
  "strategy": "0x41D7529b4C9245a50ca6A169d39719DFF117f6CA",
  "lastHarvest": 1664612723,
  "pricePerFullShare": "1178961451902175914"
},
```

**Notas sobre os campos:**

* **id** - a string de identificação exclusiva atribuída a cada cofre, incluindo versões separadas do mesmo cofre.

<!---->

* **tokenAddress** - o endereço do contrato para o ativo principal de depósito, geralmente uma token LP.

<!---->

* **earnedTokenAddress** - o contrato da token que é ganha pela estratégia usada pelo cofre. Para a maioria dos cofres da Beefy, isso é o mesmo que o contrato do cofre, porque a estratégia é de composição automática. Para cofres de pool de ganhos (que não são compostos automaticamente), este será a token nativa da rede ou protocolo à qual o cofre está relacionado.

<!---->

* **earnContractAddress** - o endereço do contrato do cofre Beefy que lida com depósitos e saques e emite a token mooVault para os usuários.

<!---->

* **status** - mostra se um cofre está ativo ("active") ou desativado ("eol").

<!---->

* **assets** - os ativos subjacentes na base do cofre relevante (normalmente os ativos incluídos na LP no qual o cofre é construído).

<!---->

* **strategyTypeID** - indica que tipo de estratégia está sendo utilizada pelo cofre (por exemplo, ativo "único", "lp", "multi-lp", etc).

<!---->

* **risks** - uma lista dos recursos aplicáveis do cofre retirados da matriz de fatores usada para calcular a pontuação de segurança de um cofre.

<!---->

* **network** - a blockchain relevante na qual o cofre reside.

<!---->

* **createdAt** - o bloco da blockchain relevante onde o cofre foi criado.

<!---->

* **strategy** - o endereço do contrato de estratégia atualmente em uso pelo cofre.

<!---->

* **lastHarvest** - o bloco do blockchain relevante onde o cofre foi coletado pela última vez - ou seja, onde os lucros foram coletados da estratégia (e autocompostos, se aplicável).

<!---->

* **pricePerFullShare** - o preço médio atual (denominado no ativo de depósito, por exemplo, o token LP subjacente) de cada ação inteira do total de ações emitidas do cofre, refletindo o valor total investido no cofre ao longo de sua vida dividido pelo número de ações do cofre emitidas .

</details>

<details>

<summary>GET /apy</summary>

Fornece o percentual de rendimento anual atual e ao vivo de cada cofre da Beefy.

```json
// Sample response for the /apy endpoint

{
  ...
  "balancer-usdc-link-eth-bal-aave": 0.03705509745347668,
  "balancer-matic-usdc-eth-bal": 0.052770609595836904,
  "baby-wbnb-busd": 0.1612595689122669,
  "baby-usdc-wbnb": 0.16031283171896837,
  "balancer-vst-dai-usdt-usdc": 0.029489187277781825,
  "balancer-bal-eth": 0.024578537703132453,
  "curve-matic-stmatic": 0.08866966650936048,
  "sushi-poly-weth-sx": 0.7135292677781775,
  "sushi-poly-bct-klima": 0.0007036903322936716,
}
```

**Notas sobre os campos:**

* **APY do Cofre** -  Cada campo reflete a sequência de id exclusiva de um cofre e retorna um valor que representa o APY ativo como um decimal. Por exemplo, "0,037" representa 3,7% APY.

</details>

<details>

<summary>GET /apy/breakdown</summary>

Fornece informações mais detalhadas relacionadas ao rendimento de cada cofre Beefy, que é necessário para avaliar o APY esperado com base em fatores como APR, taxa de composição e taxas aplicáveis.

```json
// Sample response from the /apy/breakdown endpoint (e.g. Polygon Cometh UST-ETH LP)

{
  "bifi-maxi": {
    "totalApy": 0.07598675804818633
  },
  "cometh-must-eth": {
    "vaultApr": 1.186973388240745,
    "compoundingsPerYear": 2190,
    "beefyPerformanceFee": 0.045,
    "vaultApy": 2.1057844292858614,
    "lpFee": 0.005,
    "tradingApr": 0.22324214039526927,
    "totalApy": 2.8825691266420788
  }
}
```

**Notas sobre os campos:**

* **vaultApr** - o retorno percentual anual do cofre, calculado a partir das recompensas anuais esperadas do cofre, cotado em $USD, dividido pelo valor total investido no cofre, também em $USD.

<!---->

* **compoundingsPerYear** - o número atual estimado de eventos compostos (chamadas de "harvest") por ano.

<!---->

* **beefyPerformanceFee** - a taxa de performance da Beefy incluída no cálculo.

<!---->

* **vaultApy** - o rendimento percentual anual (APY) do cofre, calculado pela composição do vaultApr detalhado acima, usando o valor de compoundingsPerYear e ajustando para o beefyPerformanceFee.

<!---->

* **lpFee** - a taxa do Provedor de Liquidez (LP) cobrada em cada troca.

<!---->

* **tradingApr** - os juros anuais recebidos das taxas de trocas, sem aplicar ou contabilizar qualquer efeito composto.

<!---->

* **totalApy** - o APY total conhecido, calculado como totalApy = (1 + vaultApy) \* (1 + tradingApr) - 1.

</details>

<details>

<summary>GET /tvl</summary>

Fornece o valor total atual e ao vivo depositado em cada cofre da Beefy, que é a soma da capitalização de mercado atual de todos os ativos atualmente mantidos pelo cofre relevante, cotado em $USD.

```json
// Sample response from the /tvl endpoint

{
    ...
    "optimism-bifi-maxi": 37679.65,
    "velodrome-wsteth-weth": 295597.74,
    "beets-lido-shuffle": 101185.39,
    "beets-yellow-submarine": 5828.15,
    "beets-its-mai-life": 178994.42,
    "velodrome-usdc-mim": 488943.72,
    "velodrome-weth-bifi": 133635.5,
    ...
}
```

</details>

<details>

<summary>GET /fees</summary>

Fornece uma análise detalhada da estrutura de taxas atual para cada cofre da Beefy.

```json
// Sample response from the /fees endpoint (e.g. Celo BIFI Maxi vault)

{
  "celo-bifi-maxi": {
    "performance": {
      "total": 0.0005,
      "strategist": 0,
      "call": 0.0005,
      "treasury": 0,
      "stakers": 0
    },
    "withdraw": 0,
    "lastUpdated": 1665603844026
  },
  ...
}
```

**Notas sobre os campos:**

* **performance** - uma lista das configurações de taxas que juntas constituem a taxa de desempenho cobrada em cada evento composto ("harvest") de cada cofre.

<!---->

* **total** - a taxa de performance total cobrada, sendo a soma dos demais fatos da lista de "performance".

<!---->

* **strategist** - a taxa devida ao estrategista que desenvolve o cofre, como forma de incentivo às contribuições da comunidade.

<!---->

* **call** - a taxa a ser paga ao chamador da função de harvest que permite a composição do cofre.

<!---->

* **treasury** - a taxa a ser paga à tesouraria da Beefy para sustentar o protocolo.

<!---->

* **stakers** - a taxa a ser paga aos detentores e participantes da token BIFI, que é paga em nossos cofres Pool de Ganhos BIFI ou para recomprar tokens BIFI para nossos cofres BIFI Maxi.

<!---->

* **withdraw** - a taxa cobrada sobre o valor do seu depósito na retirada do cofre, para proteção contra ataques e abuso de nossos cofres.

<!---->

* **lastUpdated** - o bloco da blockchain relevante para o cofre do qual os dados na API foram atualizados pela última vez.

</details>

### Endpoints de Ativos Externos

Endpoints desenvolvidos para uso pelo [Aplicativo Web da Beefy](https://app.beefy.finance/) para exibir informações sobre os ativos subjacentes aos nossos cofres Beefy para nossos usuários.

<details>

<summary>GET /lps</summary>

Fornece os preços atuais em tempo real das pools de liquidez subjacentes usadas por cada cofre da Beefy.

```json
// Sample respones from the /lps endpoint

{
  ...
  "crow-crow-bnb": 17.913780228255288,
  "crow-crow-busd": 1.1650429579716788,
  "czf-czf-bnb": 0.0025782563297118174,
  "czf-czf-busd": 0.00013385738163789002,
  "dark-dark-cro": 0.07756021296662909,
  "dark-sky-cro": 1.6261613868777973,
  "dfx-nzds-usdc": 0.5422606115320028,
  "dfyn-aave-dfyn": 2.878265077862883,
  "dfyn-bifi-dfyn": 6.083434553784047,
  ...
}
```

**Notas sobre os campos:**

* **Preço LP** - cada campo reflete a string oracleId exclusiva de um cofre LP e retorna um valor que representa o preço real em USD. Por exemplo, "1,165" representa um preço de US$ 1,17.

</details>

<details>

<summary>GET /lps/breakdown</summary>

Fornece informações mais detalhadas relacionadas às pools de liquidez usadas por cada cofre da Beefy.

```json
// Sample response from the /lps/breakdown endpoint (eg. 2omb 2omb-2share LP)

{
  "2omb-2omb-2share": {
    "price": 0.29050984564246707,
    "tokens": [
      "0x7a6e4E3CC2ac9924605DCa4bA31d1831c84b44aE",
      "0xc54A1684fD1bef1f077a336E6be4Bd9a3096a6Ca"
    ],
    "balances": [
      "114463.728388652710537014",
      "391.331589320557497638"
    ],
    "totalSupply": "5873.360029904692639438"
  },
```

**Notas sobre os campos:**

* **price** - o preço atual e ao vivo por unidade completa da token LP, cotada em $USD.

<!---->

* **tokens** - uma lista dos endereços de contrato de cada um dos ativos/tokens subjacentes incluídos na LP.

<!---->

* **balances** - uma lista dos saldos atuais de cada uma das tokens no cofre, conforme listadas no campo anterior, denominadas na token subjacente.

<!---->

* **totalSupply** - o número atual e ativo de tokens LP emitidas.

</details>

<details>

<summary>GET /tokens</summary>

Fornece informações sobre todas as tokens utilizadas pela Beefy, incluindo ativos e moedas individuais, ativos depositados e LPs, classificados por blockchain em que cada uma está presente.

```json
// Sample response for /tokens endpoint (e.g. polygon spUSDC LP token)

{
  "polygon": {
    "spUSDC": {
      "name": "Stargate USD Coin LP",
      "symbol": "spUSDC",
      "address": "0x1205f31718499dBf1fCa446663B532Ef87481fe1",
      "decimals": 6
    },
    ...
}
```

**Notas sobre os campos:**

* **name** - uma string mostrando o nome completo da token associada ao ID relevante.

<!---->

* **symbol** - uma string mostrando o símbolo atribuído à token pelo emissor.

<!---->

* **address** - o endereço de contrato da token relevante.

<!---->

* **decimals** - o número de decimais permitido para a token pelo emissor, representando o quão divisível ela é na blockchain.

**GET /tokens/{blockchain}**

Para maior especificidade, você pode adicionar um parâmetro {blockchain} ao endpoint /tokens para retornar apenas tokens em uma determinada blockchain (por exemplo, /tokens/polygon retorna apenas tokens emitidas na blockchain Polygon).

</details>

### Outros Endpoints do Beefy App

Endpoints desenvolvidos para uso pelo [Aplicativo Web da Beefy](https://app.beefy.finance/) para exibir outras informações não relacionadas a cofres individuais.

<details>

<summary>GET /config</summary>

Fornece informações sobre os endereços da configuração atual de carteiras usadas para operar cada blockchain usada pelo aplicativo Beefy.

```json
// Sample response from /config endpoint (e.g. Polygon blockchain)

{
  "polygon": {
    "devMultisig": "0x09dc95959978800E57464E962724a34Bb4Ac1253",
    "treasuryMultisig": "0xe37dD9A535c1D3c9fC33e3295B7e08bD1C42218D",
    "strategyOwner": "0x6fd13191539e0e13B381e1a3770F28D96705ce91",
    "vaultOwner": "0x94A9D4d38385C7bD5715A2068D69B87FF81F4BF3",
    "keeper": "0x4fED5491693007f0CD49f4614FFC38Ab6A04B619",
    "treasurer": "0xe37dD9A535c1D3c9fC33e3295B7e08bD1C42218D",
    "launchpoolOwner": "0x09dc95959978800E57464E962724a34Bb4Ac1253",
    "rewardPool": "0xDeB0a777ba6f59C78c654B8c92F80238c8002DD2",
    "treasury": "0x09EF0e7b555599A9F810789FfF68Db8DBF4c51a0",
    "beefyFeeRecipient": "0x7313533ed72D2678bFD9393480D0A30f9AC45c1f",
    "bifiMaxiStrategy": "0xD126BA764D2fA052Fc14Ae012Aef590Bc6aE0C4f",
    "voter": "0x5e1caC103F943Cd84A1E92dAde4145664ebf692A",
    "beefyFeeConfig": "0x8E98004FE65A2eAdA63AD1DE0F5ff76d845f14E7"
  },
...
```

**Notas sobre os campos:**

* **devMultisig** - o endereço da carteira multiassinatura do desenvolvedor Beefy usada para gerenciar atualizações de desenvolvimento na rede.

<!---->

* **treasuryMultisig** - o endereço da carteira multiassinatura do tesouro Beefy usada para gerenciar o tesouro principal de fundos da Beefy na rede.

<!---->

* **strategyOwner** - o endereço da carteira Beefy padrão que atua como proprietária de contratos de estratégia na rede.

<!---->

* **vaultOwner** - o endereço da carteira Beefy padrão que atua como proprietária de contratos de cofre na rede.

<!---->

* **keeper** - o endereço da carteira Beefy padrão que atua como guardiã dos contratos de cofre na rede. Isso inclui gerenciar a whitelist de estratégias usadas pelo cofre e pausar ou colocar o cofre em "pânico", se necessário.

<!---->

* **treasurer** -o endereço da carteira Beefy padrão que atua como tesoureiro da rede. Isso inclui o gerenciamento de pagamentos do tesouro por vários motivos e geralmente é a mesma carteira do treasuryMultisig.

<!---->

* **launchpoolOwner** - o endereço da carteira Beefy padrão que atua como proprietária dos contratos de boost lançados na rede. Geralmente, é a mesma carteira que o devMultisig.

<!---->

* **rewardPool** - o endereço da carteira Beefy padrão que contém as recompensas alocadas para boosts na rede.

<!---->

* **treasury** - o endereço da carteira Beefy padrão que atua como tesouraria na rede e é gerenciada pelo tesoureiro e treasuryMultisig.

<!---->

* **beefyFeeRecipient** -o endereço da carteira Beefy padrão que atua e recebe taxas de desempenho cobradas nas coletas de todos os cofres Beefy da rede.

<!---->

* **bifiMaxiStrategy** - o endereço da estratégia anexada ao cofre $BIFI Maxi nativo na rede.

<!---->

* **voter** - o endereço da carteira Beefy padrão que é usada para direcionar o poder de votação da Beefy em vários protocolos terceiros.

<!---->

* **beefyFeeConfig** - endereço do contrato de proxy atualizável usado para definir a configuração das taxas de desempenho cobradas pelos cofres da rede.

**GET /config/{blockchain}**

Para maior especificidade, você pode adicionar um parâmetro {blockchain} ao endpoint /config para retornar os detalhes de configuração de uma determinada blockchain (por exemplo, /config/polygon retorna apenas os detalhes da blockchain Polygon).

</details>

<details>

<summary>GET /boosts</summary>

Fornece informações sobre todos os [Boosts](https://docs.beefy.finance/products/boost) hospedados pela Beefy no aplicativo, incluindo boosts ao vivo e passados.

```json
// Sample response from /boosts endpoint (e.g. Optimism BIFI-WETH LP token)

{
  "id": "moo_velodrome-weth-bifi-beefy",
  "poolId": "velodrome-weth-bifi",
  "name": "Beefy",
  "assets": [
    "BIFI",
    "ETH"
  ],
  "tokenAddress": "0x3532b6f723948eF39d5DCf44C16855239aF81082",
  "earnedToken": "OP",
  "earnedTokenDecimals": 18,
  "earnedTokenAddress": "0x4200000000000000000000000000000000000042",
  "earnContractAddress": "0x8F755873546F4D0EDf7d41fF8604C8A632113eB7",
  "earnedOracle": "tokens",
  "earnedOracleId": "OP",
  "partnership": true,
  "status": "active",
  "isMooStaked": true,
  "partners": [
    "beefy"
  ],
  "chain": "optimism",
  "periodFinish": 1667843632
},
...
```

**Notas sobre os campos:**

* **id** - a string de identificação exclusiva atribuída a cada cofre, incluindo versões separadas do mesmo cofre.

<!---->

* **poolId** - a string de identificação exclusiva atribuída a cada LP que Beefy já fez cofres sobre, incluindo versões separadas da mesma LP.

<!---->

* **name** - o nome completo do(s) parceiro(s) que financiaram o incentivo.

<!---->

* **assets** - uma lista dos ativos subjacentes usados para o cofre ou qualquer LP subjacente.&#x20;

<!---->

* **tokenAddress** - o endereço do contrato do cofre Beefy que lida com depósitos e saques e emite a token mooVault para os usuários.

<!---->

* **earnedToken** - o nome da token de recompensa recebida pelos participantes do boost.

<!---->

* **earnedTokenDecimals** - o número de casas decimais atribuídas e usadas para o earnedToken desde sua criação.

<!---->

* **earnTokenAddress** - o endereço de contrato da earnedToken.

<!---->

* **earnContractAddress** - o endereço do contrato do boost, que contém as recompensas do boost atribuídas e as distribui para os participantes do boost.

<!---->

* **isMooStaked** - se o boost exigir que os usuários depositem suas mooTokens em um contrato adicional com a Beefy para receber o boost.

<!---->

* **partners** - rótulo abreviado para o(s) parceiro(s) que financiaram o incentivo.

<!---->

* **periodFinish** - o bloco da blockchain hospedada onde o boost termina.

**GET /boosts/{blockchain}**

Para maior especificidade, você pode adicionar um parâmetro {blockchain} ao endpoint /boosts para retornar apenas boosts em uma determinada blockchain (por exemplo, /boosts/polygon retorna apenas boosts hospedados na blockchain Polygon).

</details>

<details>

<summary>GET /bifibuyback</summary>

Fornece detalhes da quantidade diária de recompra de BIFI realizada em cada blockchain.&#x20;

```json
// Sample response from the /bifibuyback endpoint (e.g. BSC data)

{
  "bsc": {
    "buybackTokenAmount": "0.377849674473987141",
    "buybackUsdAmount": "121.1485184178464957989921757592912"
  },
  ...
}
```

**Notas sobre os campos:**

* **buybackTokenAmount** - mostra a quantidade diária atual de tokens $BIFI recomprados de volta pelo protocolo na rede relevante.

<!---->

* **buybackUsdAmount** - mostra o valor do acima em USD.

</details>

### Endpoints do Painel

Endpoints desenvolvidos para o [Dashboard da Beefy](https://dashboard.beefy.finance/) para exibir informações abrangentes sobre o protocolo.

{% hint style="info" %}
Observe que o site Dashboard e o endpoint /earnings não são mais mantidos ativamente pela Beefy. Embora o site do Dashboard permaneça ativo, ele não reflete todos os cofres que foram lançados e todas as redes nas quais a Beefy foi lançada.
{% endhint %}

<details>

<summary>GET /holders</summary>

Fornece o número específico de detentores atuais da token $BIFI.

```json
// Sample respones from the /holders endpoint

{
  "holderCount": 36882
}
```

</details>

### Endpoints de Terceira Parte

Endpoints necessários ou utilizados por plataformas de terceiros para exibir informações sobre a Beefy ou seus produtos em seus sites.

<details>

<summary>GET /cmc</summary>

Fornece informações exigidas pelo [CoinMarketCap](https://coinmarketcap.com/) para exibir os cofres da Beefy em sua seção rendimento.

```json
// Sample response for the /cmc endpoint

{
  "provider": "Beefy",
  "provider_logo": "https://beefy.finance/img/beefy.svg",
  "links": [
    {
      "title": "Twitter",
      "link": "https://twitter.com/beefyfinance"
    },
    {
      "title": "Telegram",
      "link": "https://t.me/beefyfinance"
    },
    {
      "title": "Discord",
      "link": "https://discord.gg/yq8wfHd"
    },
    {
      "title": "Medium",
      "link": "https://medium.com/beefyfinance"
    },
    {
      "title": "Github",
      "link": "https://github.com/beefyfinance"
    }
  ],
  "pools": [
    {
      "name": "BIFI Maxi",
      "pair": "BIFI",
      "pairLink": "https://app.beefy.finance/",
      "logo": "https://beefy.finance/vaults/bifi/BIFI.png",
      "poolRewards": [
        "BIFI"
      ],
      "apyId": "bifi-maxi",
      "contract": "0xf7069e41C57EcC5F122093811d8c75bdB5f7c14e",
      "oracle": "tokens",
      "oracleId": "BIFI"
    },
    ...
  ]
}
```

</details>

<details>

<summary>GET /supply</summary>

Fornece as informações solicitadas pela [Coingecko](https://coingecko.com/) para exibir o fornecimento total e circulante da BIFI em seu site.

```json
// Sample response for the /supply endpoint

{
  "total": 80000,
  "circulating": 80000
}
```

</details>

## Subgraph

Por favor, note que a Beefy atualmente não opera ou mantém quaisquer subgraphs para o nosso protocolo.

Nossos amigos da Messari desenvolveram um subgraph para nossa presença na rede BSC, que está disponível em [https://api.thegraph.com/subgraphs/name/messari/beefy-finance-bsc](https://api.thegraph.com/subgraphs/name/messari/beefy-finance-bsc) e no [site do The Graph](https://thegraph.com/hosted-service/subgraph/messari/beefy-finance-bsc) (ID: QmfEtMEgjik9FSZdqAmp2DkNFG4M9TK4Go8uyCUj8EVxY6 ). Beefy não teve nenhum papel no desenvolvimento ou manutenção deste subgraph. Por favor, encaminhe quaisquer perguntas ou pedidos de assistência em relação a este subgraph diretamente à Messari.

## Outros Dados

Para todos os leitores que buscam mais informações sobre a Beefy e o desempenho de nosso protocolo, acesse o canal #📊-beefy-data em nosso [servidor Discord](https://discord.gg/yq8wfHd). Ficaremos felizes em responder a quaisquer perguntas que você possa ter lá e você pode inspecionar o histórico de nossas discussões nesse canal para obter mais informações sobre nosso trabalho de dados.

Você também encontrará nesse canal uma coleção de relatórios semanais sobre o detalhamento da nossa token $BIFI em nossas diferentes redes e cofres, que são cuidadosamente preparados pelo colaborador principal EPETE.

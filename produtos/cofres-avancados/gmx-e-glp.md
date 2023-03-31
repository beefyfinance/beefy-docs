---
description: Tradução feita a partir da atualização de Novembro de 2022
---

# GMX e GLP

{% hint style="info" %}
O termo _Escrow_ se refere a uma relação de garantia/caução sem tradução direta para o português. Se quer entender melhor essa relação veja [#o-que-e-escrow](../moedas-escrow-da-beefy/#o-que-e-escrow "mention")
{% endhint %}

<figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

## O que é GMX?

A [GMX](https://app.gmx.io/#/trade/?ref=beefy) é uma corretora descentralizada multi-rede na Arbitrum One e na Avalanche, deixando você trocar [Futuros Perpétuos](#user-content-fn-1)[^1] facilmente. Na DEX da GMX você pode trocar BTC, ETH, AVAX, LINK e UNI com até 30x de alavancagem a partir da sua própria carteira cripto.

Como um corretor, você entra e sai das suas posições com zero impacto no preço enquanto aproveita de [_spreads_](#user-content-fn-2)[^2] mínimos e grande liquidez. Os dados dos preços confiáveis são obtidos a partir da agregação de várias fontes de preços, assim usuários também se beneficiam de riscos de liquidação reduzidos.

## O que é GLP?

A GLP é uma moeda cunhada para os provedores de liquidez na GMX. A GLP representa um índice de ativos, utilizado para negociações alavancadas e trocas na plataforma GMX. Você pode cunhá-la usando qualquer um dos ativos do índice e queimá-la para resgatar qualquer um dos ativos do índice. O custo da cunhagem e do resgate é calculado com base:

_(o valor total dos ativos no índice incluindo lucros e perdas de posições abertas) / (fornecimento de GLP)_

Após a cunhagem da GLP ela é automaticamente depositada para ganhar GMX _escrowed_ (esGMX, uma versão _escrowed_ da moeda de utilidade e de governança da GMX), pontos de multiplicação e ETH ou AVAX dependendo da rede.

## Como funciona a estratégia da Beefy para a GLP?

A Beefy tem dois novos Cofres, cada um para receber depósitos de GLP na Arbitrum e na Avalanche. Para cunhar GLP, você vai precisar depositar algum dos dos ativos na GMX, como dito anteriormente. A GLP não é transferível entre as redes (Ethereum e Avalanche).

A estratégia funciona da seguinte forma:

1. Os usuários depositam GLP ou no [Cofre de GLP da Arbitrum](https://app.beefy.finance/vault/gmx-arb-glp) ou no [Cofre de GLP da Avalanche](https://app.beefy.finance/vault/gmx-avax-glp).
2. A Beefy resgata e deposita todas as esGMX e pontos de multiplicação ganhos.
3. A esGMX ganha é sempre utilizada para impulsionar os ganhos de mais moedas nativas (ETH ou AVAX).
4. Os pontos de multiplicação ganhos também são utilizados para impulsionar os ganhos de moedas nativas.
5. A beefy coleta as taxas e cunha mais GLP para ganhar ainda mais taxas.

## Quais são os benefícios da estratégia?

Detentores de GLP proveem liquidez para posições alavancadas e lucram quando os corretores perdem. Se os corretores lucram, os detentores de GLP perdem. Em um mercado sem grandes variações a longo prazo, esses cofres são essencialmente uma aposta contra os corretores sobre uma posição estável do índice.

## O intervalo entre transferências de GLP

Há um intervalo de 15 minutos entre cunhar e transferir as GLPs. O usuário só poderá depositar suas GLPs no cofre da Beefy com sucesso após a expiração do intervalo na conta do usuário. Este intervalo também afeta os saques do cofre de GLP da Beefy, já que toda coleta cunha novas GLPs para o endereço da estratégia do Cofre.

Assim, saques do Cofre só funcionarão 15 minutos após a coleta mais recente. Isso será mostrado na interface do Cofre. No nível do contrato, a Beefy tem salvaguardas para evitar má-fé no uso desse mecanismo.

## O link de indicação da Beefy para a GMX

Corretores que usam o nosso [link para a GMX](https://app.gmx.io/#/trade/?ref=beefy) ganham 5% de desconto e dão para o endereço de tesouro da Beefy uma comissão de 5%.&#x20;

[^1]: Em caso de dúvida leia: [https://academy.binance.com/pt/articles/what-are-perpetual-futures-contracts](https://academy.binance.com/pt/articles/what-are-perpetual-futures-contracts)

[^2]: O _spread_ é a diferença entre o preço de venda e o preço de compra de um ativo.

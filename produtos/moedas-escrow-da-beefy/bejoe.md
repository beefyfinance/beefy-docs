---
description: Joe Escrowed pela Beefy
---

# beJOE

{% hint style="warning" %}
A beJOE foi descontinuada em 6 de janeiro de 2023. Todas as beJOE podem ser queimadas 1 a 1 por JOE, e a Beefy não cobra mais nenhuma taxa.
{% endhint %}

{% hint style="info" %}
O termo _Escrow_ se refere a uma relação de garantia/caução sem tradução direta para o português. Se quer entender melhor essa relação veja [#o-que-e-escrow](./#o-que-e-escrow "mention")
{% endhint %}

## O que é JOE?

JOE é a moeda nativa da Trader Joe, uma corretora descentralizada na Avalanche. Ela recompensa portadores com uma parcela dos lucros da plataforma e age como moeda de governança. JOE tem um fornecimento fixo e modelo de emissão decadente.

Usuários podem depositar JOE para ganhar veJOE e receber recompensas impulsionadas de JOE em pools selecionadas da Trader Joe poder de voto de governança.

## O que é beJOE?

beJOE é uma versão Beefy do JOE depositado para ganhar veJOE, maximizando emissões em cofres impulsionados da Beefy. Depositadores de beJOE ganham 5% das emissões desses cofres impulsionados.

A moeda é completamente caucionada 1:1 em JOE e pode ser redimida em JOE guardado na reserva. Essa reserva só é preenchida quando um novo usuário deposita.

## Como se obtém beJOE?

Você pode cunhar beJOE na página do [cofre ](https://app.beefy.finance/#/vault/beefy-beJoe)ou da [pool de recompensas](https://app.beefy.finance/#/vault/beefy-beJoe-earnings) beJOE na proporção de 1:1. Não haverá liquidez incentivada para beJOE, ao vés, haverá uma reserva de retirada.

\[Image text translation. "One : One" to "Um : Um" and "Joe Reserve" to "Reserva JOE". Subtitles, "beJOE is minted and burned at a 1:1 rate with JOE" to "beJOE é cunhado e queimado na taxa de 1:1 com JOE".]

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption><p>beJOE é cunhado e queimado na taxa de 1:1 com JOE</p></figcaption></figure>

## Como beJOE funciona?

Quando você cunha beJOE, o contrato vai imediatamente tentar depositar o JOE em veJOE, sujeito a duas condições: (1) a reserva requerida precisa ser mantida e; (2) o depósito deve ativar um bônus "Speed Up" (aceleração).

Se as reservas de Joe do contrato no momento da cunhagem exceder a quantidade necessária da reserva (que, no momento, é 20% do JOE do contrato já depositado em veJOE), o contrato pode depositar o JOE em excesso em veJOE. Se as reservas de JOE estiverem abaixo na quantidade requerida, então o JOE depositado será adicionado na reserva para cobrir o déficit.

O bônus "Speed Up" na Trader JOE dobra a taxa de recompensas veJOE por 14 dias depois que o JOE é depositado, desde que a quantidade de JOE depositada acrescente 5% (ou mais) adicionais à quantidade total de JOE já depositado em veJOE. Então, o contrato checa, antes de depositar, se o saldo disponível (incluindo o depósito e qualquer excesso pré-existente da reserva) corresponde ou excede o limiar de 5% e vai depositar o saldo disponível apenas quando o fizer. Senão, ele espera outros depósitos de JOE para aumentar o saldo disponível antes de depositar.

Quando o JOE do contrato é depositado em veJOE, ele vai automaticamente receber recompensas veJOE. veJOE provê 2 benefícios: (1) recompensas impulsionadas em certas pools do Trader JOE e; (2) (futuro) direito de voto de governança na Trader JOE. A quantidade de cada benefício é proporcional à quantidade de veJOE mantida no contrato, logo o objetivo é acumular o máximo de veJOE possível.

Apesar das recompensas veJOE acumulares constantemente no JOE depositado do contrato, as recompensas precisam ser coletadas para ser adicionadas ao saldo de veJOE do contrato. Recompensas são automaticamente coletadas quando JOE é depositado em veJOE e, outrora, manualmente coletadas pelo contrato quando novo beJOE é cunhado, mas as condições para depositar não são correspondidas.

## Como eu ganho com o meu beJOE?

Quando você tiver beJOE, existem duas opções disponíveis. Você pode:

1. Depositar no cofre beJOE para ganhar mais beJOE ou;
2. depositar na pool de ganhos beJOE para ganhar JOE.

Em todo cofre Beefy de pools da Trader Joe que é impulsionada para detentores de veJOE, 5% do valor de todas as colheitas é direcionado para a pool de recompensas do beJOE para pagar os detentores de beJOE. isso reflete o valor adicionado pelo contrato do beJOE, que recolhe o veJOE necessário para impulsionar estes cofres.

Como as recompensas impulsionadas nas pools da Trader JOE são pagas em JOE, essas podem ser pagas de volta para os detentores de beJOE tanto diretamente em JOE, quanto cunhando mais beJOE com as recompensas JOE.

## Como funciona a estratégia beJOE?

\[IMAGE TRANSLATION: \*redeem beJOE at 1:1 from JOE reserves = resgate beJOE em 1:1 das reservas de JOE\
User = Usuário\
SMART MINT = CUNHAGEM INTELIGENTE\
STAKE = DEPOSITE\
CLAIM = RECOLHA\
OR = OU\
REINVESTED = REINVESTIDO\
JOE REWARDS = RECOMPENSAS JOE\
AUTOCOMPOUNDING = AUTO-REINVESTINDO\
Choose available beJOE vault - rewards pool (APR) or autocompound (APY) = Escolha um cofre de beJOE disponível - pool de recompensas (APR) ou auto-reinvestimento (APY)\
Mint beJOE (Beefy smart mint) = Cunhe beJOE (cunhagem inteligente da Beefy)\
Escrowed JOE staked to earn rewards = JOE caucionado depositado para ganhar recompensas\
Return to stake beJOE to earn rewards = Volte para depositar beJOE no cofre selecionado\
Earned rewards are sent to the earnings pool = Recompensas ganhas são enviadas para a pool de ganhos\
APY vault autocompounds at an optimal rate = O cofre de reinvestimento (APY) o faz de forma otimizada]

<figure><img src="../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

## Mas e as taxas?

A Beefy tem as menores taxas de otimização de rendimento na Avalanche. Com os novos cofres impulsionados por beJOE da Beefy, você ganha mais do que em qualquer outro lugar. A Beefy cobra sua taxa de perfomance de 4,5% em cofres impulsionados, mais um adicional de 5% entregue diretamente para os depositadores de beJOE.

## Como beJOE mantém o seu lastro?

Não há liquidez provida para beJOE, então ele sempre estará 1:1 com JOE. Usuários podem queimar beJOE por JOE enquanto a reserva restar. Essa reserva só é preenchida quando um novo usuário deposita.

Em um caso de última opção, todo o JOE trancado em beJOE pode ser destrancado e solto pata a reserva. Os competidores da Beefy não têm isso. No entanto, isso também terminaria os impulsos disponíveis para os cofres da Beefy e as recompensas direcionadas para a pool de recompensas beJOE, então dificilmente ocorrerá.

## Eu posso votar com beJOE?

Ainda não, mas beJOE implementa EIP-1271 (validação de assinatura para contratos), logo subornos/governança com a Trader JOE podem ser organizados.

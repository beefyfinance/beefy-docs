---
description: VELO Escrowed pela Beefy
---

# beVELO

{% hint style="info" %}
O termo _Escrow_ se refere a uma relação de garantia/caução sem tradução direta para o português. Se quer entender melhor essa relação veja [#o-que-e-escrow](./#o-que-e-escrow "mention")
{% endhint %}

## O que é VELO?

VELO é a moeda nativa da Velodrome Finance, uma corretora descentralizada e mercado de liquidez nativa da blockchain Optimism. Ela recompensa os detentores com uma parte das receitas da plataforma e também atua como uma moeda de governança para seu indicador semanal de incentivos de pools. A VELO tem um modelo de fornecimento fixo e emissões decrescentes.

Os usuários podem depositar e trancar suas moedas VELO na Velodrome por um período fixo entre 1 semana e 4 anos, para receber uma NFT _escrowed_ de voto ("veNFT"), que é usada para registrar a quantidade de veVELO detida pelo usuário. Os detentores de veVELO recebem três benefícios: (1) uma parte das taxas de trocas das trocas feitas nas pools de liquidez da plataforma; (2) a capacidade de direcionar as emissões de VELO distribuídas aos provedores de liquidez da plataforma; e (3) a oportunidade de ganhar subornos de partes externas votando em suas pools de liquidez incentivadas. O depósito de VELO pode ser feito através do [aplicativo web da Velodrome](https://app.velodrome.finance/vest).

A veVELO é intransferível e a quantidade detida pelo usuário diminui constantemente até zero na medida em que o período de tranca se aproxima do seu fim. Os usuários também não podem liquidar ou transferir suas moedas VELO trancadas até o final do período de tranca.

## O que é beVELO?

beVELO é uma versão de VELO depositado em troca de veVELO _escrowed_ pela Beefy para aproveitar os vários benefícios oferecidos aos depositadores da Velodrome.

A moeda é completamente caucionada 1:1 por VELO e pode ser resgatada por VELO guardado na reserva. Essa reserva é preenchida em diversas circunstâncias:

1. Quando um novo usuário deposita Velo em troca de beVELO e a reserva está abaixo do requerido;
2. quando o contrato coleta subornos e taxas de troca da Velodrome (que acontece quando a _epoch_ vira nas quintas-feiras às 00:00 UTC) e a reserva está abaixo do requerido ou;
3. Se o VELO depositado do contrato é deixado para destrancar gradualmente.

\[IMAGE TRANSLATION: "Introducing" to "Introduzindo". SUBTITLES: "beVELO is designed to capture the maximum possible rewards and benefits from Velodrome's vote escrow tokenomics" to "beVELO é desenhada para aproveitar o máximo de recompensas e benefícios possíveis da _veTokenomics_ da Velodrome."]

<figure><img src="../../.gitbook/assets/image (47).png" alt=""><figcaption><p>beVELO é desenhada para aproveitar o máximo de recompensas e benefícios possíveis da <em>veTokenomics</em> da Velodrome.</p></figcaption></figure>

## Como se obtém beVELO?

Você pode cunhar beVELO na [página do cofre da beVELO](https://app.beefy.finance/vault/beefy-bevelo) na proporção 1:1. Não há liquidez incentivada para beVELO, no lugar, existe uma reserva de VELO para saques.

## Como funciona a beVELO?

Quando você cunha beVELO, o contrato vai imediatamente tentar depositar e trancar o VELO depositado por veVELO, desde que as reservas estejam mantidas.

Se as reservas de VELO do contrato na hora da cunhagem excederem a quantidade requerida da reserva (que atualmente é 20% do veVELO do contrato), o contrato pode depositar a quantidade excedente de VELO em veVELO. Se as reservas de VELO estão abaixo da quantidade requerida de reserva, então o VELO depositado vai para a reserva para cobrir o desfalque.

Uma vez que o VELO do contrato está depositado e trancado por veVELO, ele recebe 3 benefícios: (1) uma parcela das tarifas de trocas pagas nas pools de liquidez da plataforma; (2) a habilidade de direcionar emissões de VELO distribuídas para depositadores de pools de liquidez e; (3) a oportunidade de receber subornos de partes terceiras votando nas suas pools de liquidez para incentivo.

Como o contrato da beVELO estende sua tranca de VELO perpetuamente, ele sempre busca o máximo de poder de voto e de benefícios. Taxas de troca e subornos são regularmente coletados, trocados por beVELO e redepositados no cofre de beVELO para auto-reinvestir o retorno para os depositadores de beVELO.

## &#x20;Como posso ganhar com a minha beVELO?

Quando você já tem beVELO você pode depositá-las no nosso cofre beVELO para ganhar mais beVELO.

Como nosso contrato beVELO ganha taxas de trocas e subornos por usar nosso veVELO no protocolo, essa receita é trocada por mais beVELO e redepositada no cofre de beVELO para gerar o efeito de auto-reinvestimento. Isso aumenta o rendimento comparado com o que os usuários conseguem sozinhos na plataforma.

<figure><img src="../../.gitbook/assets/image (58).png" alt=""><figcaption><p>beVELO pode ser depositada em nosso cofre beVELO, onde os rendimentos provenientes dos depósitos das VELO do contrato em veVELO são depositados novamente e autocompostos.</p></figcaption></figure>

## Mas e as taxas?

A Beefy busca manter umas das taxas mais baixas de otimização de rendimento e cobra a taxa padrão de performance nos cofres de beVELO.

## Como beVELO mantém o seu lastro?

Não há liquidez provida para beVELO, então sempre estará 1:1 com a VELO. Usuários podem queimar beVELO por VELO da reserva do contrato sem afetar o lastro.

## Como posso pegar minha VELO de volta?

Enquanto houver moedas VELO disponíveis na reserva, você poderá queimar as suas moedas beVELO (até a quantidade existente na reserva) para receber de volta a quantidade equivalente de VELO.

Quando a reserva não tem moedas VELO o suficiente para o saque solicitado, você será capaz de retirar até a quantidade disponível na reserva. Usuários podem então esperar até a próxima coleta de taxas de troca e de subornos, que irão para a reserva e permitirão que os usuários queimem suas beVELO. Outrora, o mecanismo de tranca da Velodrome não inclui um mecanismo de soltura de emergência.

Como a quantidade requerida da reserva está ligada a quantidade de veVELO que o contrato possui e todos os saldos de veVELO reduzem ao longo do tempo na medida em que o tempo da tranca reduz, a quantidade requerida de reserva também vai reduzir naturalmente com o tempo até que a tranca de veVELO seja estendida. Dessa forma, assumindo que outros depósitos de VELO não sejam feitos para reestabelecer a reserva, a quantidade requerida da reserva vai reduzir com o tempo, significando que a quantidade de VELO disponível para saque aumentará constantemente.

## Eu consigo votar com as minhas beVELO?

Não. Todo o poder de voto de VELO será usado pela Beefy para votar na indicação semanal de pools de liquidez.

Votos serão tipicamente dirigidos às pools de liquidez que oferecem mais taxas de troca e subornos, ou pools de liquidez que suportam a moeda BIFI (por exemplo, BIF-OP LP). O contrato beVELO vai coletar todas as taxas de troca e subornos e trocá-los por mais VELO para auto-reinvestir no cofre beVELO (assim aumentando o ganho dos usuários). Votos nas pools de liquidez incentivadas da Velodrome acontece no seu [aplicativo web](https://app.velodrome.finance/vote).

Se você está interessado em propor um suborno para a Beefy, por favor entre em contato com a equipe principal no Discord, Telegram ou Twitter para descobrir mais.

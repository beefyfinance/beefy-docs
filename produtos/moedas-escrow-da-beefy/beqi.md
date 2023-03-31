---
description: QI Escrowed pela Beefy
---

# beQI

{% hint style="info" %}
O termo _Escrow_ se refere a uma relação de garantia/caução sem tradução direta para o português. Se quer entender melhor essa relação veja [#o-que-e-escrow](./#o-que-e-escrow "mention")
{% endhint %}

## O que é QI?

QI é a moeda nativa da Mai Finance, um protoco de débito colateralizado nativo da Polygon. A Mai Finance é governada pela QiDao, na qual QI é a moeda de governança. QI também pode ser usada para participar em uma parcela dos dividendos do protocolo. QI tem um fornecimento fixo e um modelo de emissões decadentes.

Usuários podem depositar QI para ganhar eQI e receber até 4x dividendos impulsionados do protocolo e poder de votação de governança.

## O que é beQI?

beQI é uma versão Beefy do QI depositado para ganhar eQI, para impulsionar a proporção de dividendos do protocolo da Mai Finance que a Beefy ganha e participar dos votos em medidores de incentivos de cofres.

A moeda é completamente caucionada 1:1 em QI e pode ser redimida por QI na reserva. A reserva enche quando novos usuários depositam (se estiver abaixo da quantia requerida de reserva na hora) ou a quantia requerida da reserva gradualmente decresce na medida em que o eQI do contrato gradualmente decresce e é liberada.

## Como se obtém beQI?

Você pode cunhar beQI nas páginas do [cofre de beQI](https://app.beefy.finance/#/vault/beefy-beqi) ou da [pool de ganhos](https://app.beefy.finance/#/vault/beefy-beqi-earnings) na proporção de 1:1. Não haverá liquidez incentivada para beQI, no lugar, teremos as reservas para retiradas.

\[IMAGE TRANSLATION: Earn more = Ganhe mais. beQI VAULT = COFRE beQI. SUBTITLES: beQI is minted and burned at a 1:1 rate with Qi = beQI é cunhado e queimado na proporção de 1:1 com QI]

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption><p>beQI é cunhado e queimado na proporção de 1:1 com QI</p></figcaption></figure>

## Como funciona beQI?

Quando você cunha beQI, o contrato vai imediatamente tentar depositar e trancar o QI depositado em eQI, sujeito a reserva requerida sendo mantida.

Se as reservas de QI do contrato excederem a quantia de reserva requerida (que atualmente é  20% do eQI do contrato) no momento da cunhagem, o contrato vai depositar qualquer excesso de QI em eQI. Se as reservas de QI estão abaixo da quantia de reserva requerida, então o QI depositado será adicionado à reserva para cobrir o déficit atual.

Uma vez que o QI do contrato é depositado e trancado em eQI, ele recebe dois benefícios: (1) recompensas impulsionadas dos dividendos semanais do protocolo e; (2) direitos de voto na governança QiDao e votos nos medidores de incentivos de cofres. A abordagem da Beefy para votações com beQI está detalhada abaixo [#posso-votar-com-beqi](beqi.md#posso-votar-com-beqi "mention").

Dividendos do protocolo Mai Finance são pagos semanalmente e atualmente inclui 100% das recompensas vindas das taxas de depósito do protocolo, que são usadas na pool QI-MATIC, junto com 30% das taxas de pagamento de débito de todos os tipos de colaterais (mais 25% de bonus semanal). Recompensas individuais podem ser impulsionadas em até 4x onde um usuário tem a quantidade máxima de eQI (ou seja, trancou seu QI por 4 anos).

Como o contrato de beQI retranca perpetuamente seu QI, ele sempre busca o maior impulso. Todas as nossas recompensas recebidas são então distribuídas para nossos cofres beQI e a pool de ganhos com beQI da Beefy para beneficiar os detentores de beQI.

## Como posso ganhar com minhas beQIs?

Tendo beQI, você tem duas opções disponíveis. Você pode:

1. Depositar no cofre beQI para ganhar mais beQI ou;
2. Depositar na pool de ganhos de beQI para ganhar QI.

Como os dividendos do protocolo impulsionados por eQI é pago em moedas QI, essas podem ser pagas de volta para os detentores de beQI diretamente em QI (na pool de ganhos) ou reinvestindo em beQI (através do cofre) cunhando mais beQI com as recompensas de QI.

\[IMAGE TRANSLATION\
Return Maximizer = Maximizador de Retornos\
Stake beQI / Earn QI = Deposite beQI / Ganhe QI\
autocompounding beQI = auto-reinvestindo beQI\
beQI Earnings Pool = Pool de Ganhos beQI\
stake beQI earn QI = deposite beQI ganhe QI\
Earn more = Ganhe mais\
\*Quoted yield may change = Rendimentos citados podem variar\
SUBTITLES: beQI can be autocompounded or staked to earn Qi = beQI pode ser auto-reinvestido ou depositado para ganhar QI. END OF IMAGE TRANSLATION]

<figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption><p>beQI pode ser auto-reinvestido ou depositado para ganhar QI</p></figcaption></figure>

## Como funciona a estratégia do beQI?

\[IMAGE TRANSLATION: \* Resgate beQI em 1:1 das reservas de QI

* Escolha entre os cofres beQI disponíveis - pool de recompensas (APR) ou auto-reinvestimento (APY)
* Cunhe beQI (cunhagem inteligente da Beefy)
* Qi caucionado depositado para ganhar recompensas
* Volte para depositar beQI no cofre selecionado
* Recompensas ganhas são enviadas para a pool de recompensas
* cofre de APY reinveste automaticamente de forma otimizada

QI REWARDS = RECOMPENSAS DE QI\
AUTOCOMPOUNDING = AUTO-REINVESTINDO\
QI CLAIM / OR / beQI REINVESTED = COLETE QI / OU / beQI REINVESTIDO\
STAKE = DEPOSITE\
SMART MINT = CUNHAGEM INTELIGENTE\
User = Usuário\
Strat = Estratégia\
\
END OF IMAGE TRANSLATION]

<figure><img src="../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

## Mas e as taxas?

A Beefy busca manter umas das taxas mais baixas de otimização de rendimento. É cobrada a taxa padrão de performance nos cofres de beQI.

## Como que beQI mantém seu lastro?

Não há liquidez provida para beQI, então sempre estará 1:1 com QI. usuários podem queimar beQI por QI enquanto a reserva restar, sem afetar o lastro.

## Como posso pegar meu QI de volta?

Enquanto houverem moedas QI disponíveis na reserva, você poderá queimar suas moedas beQI existentes  (até a quantia da reserva) para receber de volta uma quantia de QI equivalente.

Quando a reserva não possuir moedas Qi  o suficiente para a retirada solicitada, você só poderá retirar até a quantia presente da reserva. Infelizmente, a tranca de eQI não inclui um mecanismo de liberação de emergência, neste cenário, nos detentores precisarão esperar até que a reserva seja preenchida.

Como a quantia requerida da reserva está ligada à quantidade de eQI contida no contrato e todos os saldos de eQI diminuem ao longo do tempo na medida em que o tempo restante da tranca diminui, a quantia requerida da reserva também vai diminuir naturalmente com o tempo até que a tranca de eQI seja extendida. Assim, assumindo que nenhum outro depósito de QI seja feito para preencher a reserva, a quantia requerida da reserva vai diminuir gradualmente com o tempo, significando que a quantia de QI disponível para retirada vai aumentar constantemente.

## Posso votar com beQI?

Não no momento. Todo o poder de votação de QI é atualmente usado pela Beefy para votar no medidor de incentivos de cofre semanal. Votos serão tipicamente direcionados para os colaterais da Beefy (ex: mooBIFI Fantom), que recompensa nossos usuários que depositam seus bens Beefy como colateral na Mai Finance.

Caso a qualificação dos nossos colaterais preferidos para o medidor de incentivos seja improvável, nós podemos também aceitar subornos de terceiros. Os ganhos de todos os subornos são então distribuídos diretamente para os detentores de beQI. Se você estiver interessado em propor um suborno para a Beefy, por favor, comunique nossa equipe no Discord, Telegram ou Twitter para saber mais.

\[IMAGE TRANSLATION: QI voting power = poder de votação de QI. Bribe to the beQI stakers = Suborno para os depositadores de beQI. SUBTITLES: Beefy's Qi voting power can also be used for bribes, which are paid directly to holders = poder de votação de QI da Beefy também pode ser subornado, que são pagos diretamente aos detentores.]

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption><p>poder de votação de QI da Beefy também pode ser subornado, que são pagos diretamente aos detentores</p></figcaption></figure>

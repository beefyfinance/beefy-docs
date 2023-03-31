---
description: inSPIRIT envelopado pela Beefy
---

# binSPIRIT

## O que é SPIRIT?

SPIRIT é a moeda nativa da SpiritSwap, uma corretora descentralizada na Fantom. Ela recompensa detentores com uma parcela dos lucros da plataforma e também age como moeda de governança. Spirit tem um fornecimento fixo e modelo de emissões decadentes.

Usuários podem depositar e trancar suas moedas SPIRIT na SpiritSwap por entre 1 semana e quatro anos, pelas quais eles recebem uma quantidade proporcional de inSPIRIT. Detentores de inSPIRIT recebem três benefícios adicionais: (1) uma proporção dos lucros do protocolo (que variam de semana a semana, mas têm sido tão altos quanto 80% APR); (2) direitos a voto na governança do protocolo e; (3) até 2,5X recompensas impulsionadas de pools da SpiritSwap, dependendo do saldo de inSPIRIT tido pelo usuário.&#x20;

inSPIRIT é intransferível e a quantidade tida pelo usuário diminui progressivamente para 0 quando o período de tranca se encerra. Usuários também não podem liquidar sua posição ou transferir suas SPIRITs trancadas até o final do tempo de tranca.

## O que é binSPIRIT?

binSPIRIT é a versão da inSPIRIT da Beefy que é depositado para acumular inSPIRIT. Detentores de binSPIRIT recebem todos os benefícios da inSPIRIT detalhados acima, mas sem estarem restringidos pelo mecanismo de tranca da SpiritSwap.

A moeda é caucionada 1:1 por SPIRIT, apesar de estar perpetuamente trancada por inSPIRIT, então não pode ser retirada de volta para SPIRIT. No entanto, binSPIRIT é uma moeda ERC-20 transferível, então pode ser trocada por outras moedas em corretoras descentralizadas, permitindo que os detentores liquidem suas posições a qualquer hora.

## Como se obtém binSPIRIT?

Usuários podem cunhar binSPIRIT na [página do cofre binSPIRIT](https://app.beefy.finance/#/vault/beefy-binspirit) na proporção 1:1. Se for mais lucrativo comprar binspirit, então a cunhagem inteligente da Beefy fará exatamente isso, adquirindo mais binSPIRIT para o usuário com a SPIRIT dele. Usuários também podem adquirir binSPIRIT comprando-a em uma corretora descentralizada.

\[image translation: "1. Use SPIRIT to MINT binSPIRIT" to "Use SPIRIT para CUNHAR binSPIRIT". "2. Smart MINT will calculate & execute most profitable strategy" to " A CUNHAGEM inteligente vai calcular e executar a estratégia mais lucrativa". "or" in the middle is translated to "ou". "Mint" and "buy" are translated to "cunhar" and "comprar" respectively. "3. Stake binSPIRIT in the vault" to "Deposite binSPIRIT no cofre". Subtitles: "beMINT determines the most profitable strategy" to "A cunhagem inteligente determina a estratégia mais lucrativa"]

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption><p>A cunhagem inteligente opera pela estratégia mais lucrativa</p></figcaption></figure>

## Como binSPIRIT funciona?

A Beefy usa a SPIRIT depositada para acumular o máximo de inSPIRIT que puder, depositando imediatamente e trancando perpetuamente todos os depósitos na SpiritSwap pelo maior período de tempo disponível. Então, usa a inSPIRIT acumulada para resgatar os lucros do protocolo da SpiritSwap, impulsionar seus cofres da SpiritSwap e votar nas emissões de incentivos da SpiritSwap.

Todos os lucros do protocolo são pagos em SPIRIT, que é automaticamente resgatado pela Beefy e então retornados para o cofre de binSPIRIT, seja cunhando mais binSPIRIT (se binSPIRIT estiver acima do lastro) ou comprando binSPIRIT em uma corretora descentralizada (se estiver abaixo do lastro). Em qualquer caso, a binSPIRIT é redepositada no cofre.

Todos os depósitos, retiradas e coletas de recompensas dos cofres da SpiritSwap impulsionados na Beefy são roteados através do contrato da binSPIRIT, assim conseguem receber os benefícios do impulso da inSPIRIT. Mantendo toda a inSPIRIT acumulada em um contrato e gerindo todos os cofres de pools da SpiritSwap por esse contrato, a binSPIRIT assegura que cada cofre receba o impulso máximo disponível. Todas as recompensas impulsionadas são retidas pelos cofres individuais da Beefy.

O contrato binSPIRIT também submite votos em nome da Beefy nas propostas de governança da SpiritSwap e nos medidores de incentivos. Detentores de binSPIRIT podem votar\* em medidores de incentivos, como descrito mais abaixo.

Para mais detalhes sobre as funcionalidades específicas e métodos da binSPIRIT, vejam a descrição do seu principal contrato inteligente GaugeStaker\*.

## Como posso ganhar com as minhas binSPIRITs?

Tendo binSPIRIT, você tem algumas opções. Você pode:

1. Depositar no cofre binSPIRIT da Beefy para ganhar dividendos do protocolo, que são automaticamente redepositados em mais binSPIRIT;
2. Depositar em uma pool de liquidez de binSPIRIT de uma corretora descentralizada para ganhar com taxas de troca e possíveis recompensas ou;
3. Depositar na pool de liquidez SPIRIT na SpiritSwap e depositar no [cofre SPIRIT-binSPIRIT LP da Beefy](https://app.beefy.finance/#/vault/spirit-binspirit-spirit) para ganhar juros compostos nas taxas de troca e de recompensas.

## Mas e as taxas?

A Beefy tem as taxas de otimização de rendimento mais baixas da Fantom. É cobrada uma taxa padrão de performance de 4,5% nos cofres binSPIRIT e SPIRIT-binSPIRIT LP. Não cobramos nenhuma taxa no uso da cunhagem inteligente da Beefy para converter SPIRIT em binSPIRIT.

## Como a binSPIRIT mantém seu lastro?

Se um usuário quiser liquidar sua posição, ele poderá trocar binSPIRIT em uma corretora. Ao contrário da inSPIRIT, os usuários nunca ficam presos e podem liquidar suas posições a qualquer momento. Isso também significa que a binSPIRIT nem sempre estará corretamente lastreada à SPIRIT, mas visa manter um lastro frouxo.&#x20;

Se a binSPIRIT cair abaixo do lastro, o contrato vai usar os dividendos resgatados da SpiritSwap para comprar de volta mais binSPIRIT. Isso aumenta proporcionalmente a parcela de SPIRIT depositada de cada detentor de binSPIRIT, deixando-os com mais do que teriam se trancassem a mesma SPIRIT diretamente na SpiritSwap.

Se a binSPIRIT estiver acima do lastro, o contrato usará os dividendos do protocolo para cunhar mais binSPIRIT.

## Posso votar com binSPIRIT?

Não. Apesar da Beefy ter preparado um sistema de votação de binSPIRIT com uma [página Snapshot](https://snapshot.org/#/binspirit.eth) dedicada, a mudança para a SpiritSwap V2 permitiu automatizar o processo dos subornos para que obtivéssemos o maior retorno para os detentores. A Beefy pega os subornos ganhos e os retorna diretamente para os cofres de binSPIRIT, facilitando grandes retornos com o mínimo de esforço.

Mesmo que a Beefy tenha o processo automatizado, ainda estamos abertos a receber ofertas diretas para subornos de binSPIRIT. Por favor, entre em contrato com a equipe principal no Discord, Telegram ou Twitter para saber mais.

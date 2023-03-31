---
description: OPX Escrowed da Beefy
---

# beOPX

{% hint style="info" %}
O termo _Escrow_ se refere a uma relação de garantia/caução sem tradução direta para o português. Se quer entender melhor essa relação veja [#o-que-e-escrow](./#o-que-e-escrow "mention")
{% endhint %}

## O que é OPX?

OPX é a moeda nativa da OPX Finance, uma corretora descentralizada de spot e perpétuos nativa da blockchain Optimism. A moeda OPX é usada para recompensar detentores com uma parcela da receita do protocolo, também provendo poder de voto para uso na governança do protocolo. A OPX adotou um modelo de fornecimento fixo da moeda, apesar da atual moeda OPX incorporar métodos tanto de cunhagem quanto de queima.

A OPX oferece uma nova forma de Tokenomics de _Escrow_ de voto para a sua governança e mecanismos de divisão de lucros. Ela requer que os detentores depositem e tranquem no protocolo suas moedas OPX e uma NFT da OPX. Após isso, detentores recebem veOPX, que reflete o direito do detentor de participar da governança do protocolo e dos lucros. As NFTs da OPX só podem ser obtidas por uma Caixa Misteriosa da OPX (ou se vendidas por um terceiro) e são emitidas com um nível de aleatoriedade que determina o impulso aplicado ao veOPX do detentor.

O objetivo da governança por veOPX é decidir a distribuição de moedas OPX entre: (1) provedores de liquidez da OPX(OLP); (2) parcela de lucro dos depositadores de OPX; (3) liquidez de OPX sob posse do protocolo; (4) tesouro dos desenvolvedores da OPX; (5) programa de recompra e queima da OPX e; (6) parcela de lucro da DarkCrypto DAO - criadores da OPX. Os [depósitos](https://www.opx.finance/#/stake) e [votos](https://www.opx.finance/#/vote) na OPX podem ser feitos em seu aplicativo web.

A veOPX não é transferível e a quantidade em posse do usuário decresce regularmente até zero na medida em que o período da tranca se aproxima da soltura. Usuários não podem liquidar ou transferir suas posições OPX trancadas até o final do tempo da tranca.

## O que é beOPX?

A beOPX é uma versão _Escrowed_ da Beefy de OPX depositado para veOPX para aproveitar os vários benefícios oferecidos aos depositadores de OPX. Como a Beefy possui uma NFT da OPX da mais alta raridade (nível 5), a beOPX dá aos usuários acesso à parcela dos lucro com o maior impulso, que outrora seria reservada aos poucos sortudos que adquiriram uma NFT de raridade semelhante.

A moeda é caucionada 1:1 com OPX e pode ser resgatada pelas OPX presentes na reserva. Essa reserva é preenchida em diversas circunstâncias:

1. quando novos usuários depositam OPX em troca de beOPX e as reservas estão abaixo da quantidade requerida;
2. quando o contrato coleta sua parcela de lucros da OPX e as reservas estão abaixo da quantidade requerida e;
3. se o OPX depositado do contrato é configurado para gradualmente ser destrancado.

\[IMAGE TRANSLATION: "Introducing" to "Introduzindo". SUBTITLES: "beOPX is designed to capture the maximum possible rewards and benefits from OPX's vote escrow tokenomics." to "A beOPX é desenhada para aproveitar o máximo possível das recompensas e benefícios da _veTokenomics_ da OPX." END OF TRANSLATION]

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>A beOPX é desenhada para aproveitar o máximo possível das recompensas e benefícios da <em>veTokenomics</em> da OPX.</p></figcaption></figure>

## Como se obtém beOPX?

Você pode cunhar beOPX na [página do cofre beOPX](https://app.beefy.com/vault/beefy-beopx) na proporção 1:1. Não há liquidez incentivada para beOPX, tendo em seu lugar uma reserva para saques.

## Como funciona a beOPX?

Quando você cunha beOPX, o contrato vai imediatamente tentar depositar e trancar o OPX depositado em veOPX, desde que a reserva requerida seja mantida.

Se as reservas de OPX do contrato excederem a a quantidade requerida de reserva (atualmente 30% do veOPX do contrato) na hora da cunhagem, o contrato vai depositar o OPX em excesso em veOPX. Se a reserva de OPX estiver abaixo da quantidade requerida, então o OPX depositado será acrescentado a reserva para cobrir o desfalque do momento.

Uma vez que o OPX do contrato está depositado e trancado em veOPX, ele recebe uma proporção dos lucros do protocolo da OPX que são alocados para os depositadores, junto com a habilidade de votar em futuras distribuições do lucro do protocolo entre as opções diferentes disponíveis.

Como o contrato da beOPX estende sua tranca de OPX perpetuamente, ele sempre busca o máximo de poder de voto e de benefícios. Taxas de troca e subornos são regularmente coletados, trocados por beOPX e redepositados no cofre de beOPX para auto-reinvestir o retorno para os depositadores de beOPX.

## Como posso ganhar com as minhas beOPX?

Quando você já tem beOPX você pode depositá-las no nosso cofre beOPX para ganhar mais beOPX.

Como nosso contrato beOPX ganha lucros do protocolo por usar nosso veOPX no protocolo, essa receita é trocada por mais beOPX e redepositada no cofre de beOPX para gerar o efeito de auto-reinvestimento. Isso aumenta o rendimento comparado com o que os usuários conseguem sozinhos na plataforma.

## Mas e as taxas?

A Beefy busca manter umas das taxas mais baixas de otimização de rendimento e cobra a taxa padrão de performance nos cofres de beOPX.

## Como beOPX mantém o seu lastro?

Não há liquidez provida para beOPX, então sempre estará 1:1 com a OPX. Usuários podem queimar beOPX por OPX da reserva do contrato sem afetar o lastro.

## Como posso pegar minha OPX de volta?

Enquanto houver moedas OPX disponíveis na reserva, você poderá queimar as suas moedas beOPX (até a quantidade existente na reserva) para receber de volta a quantidade equivalente de OPX.

Quando a reserva não tem moedas OPX o suficiente para o saque solicitado, você será capaz de retirar até a quantidade disponível na reserva. Usuários podem então esperar até a próxima coleta dos lucros do protocolo, que irão para a reserva e permitirão que os usuários queimem suas beOPX. Outrora, o mecanismo de tranca da OPX não inclui um mecanismo de soltura de emergência.

Como a quantidade requerida da reserva está ligada a quantidade de veOPX que o contrato possui e todos os saldos de veOPX reduzem ao longo do tempo na medida em que o tempo da tranca reduz, a quantidade requerida de reserva também vai reduzir naturalmente com o tempo até que a tranca de veOPX seja estendida. Dessa forma, assumindo que outros depósitos de OPX não sejam feitos para reestabelecer a reserva, a quantidade requerida da reserva vai reduzir com o tempo, significando que a quantidade de OPX disponível para saque aumentará constantemente.

## Posso votar com as minhas beOPX?

Não. Todo o poder de voto em OPX será usado pela Beefy para votar nas distribuições de lucros do protocolo. As votações ocorrem na [aplicação web da OPX](https://www.opx.finance/#/vote).

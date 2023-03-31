# Cofres

## O que é um Cofre?

Os cofres são instrumentos de investimento que empregam um conjunto específico de estratégias para adquirir rendimento. Eles fazem uso de automação para investir e reinvestir continuamente os fundos depositados, o que ajuda a alcançar altos níveis de juros compostos. Ao usar um cofre Beefy para reinvestir seus ganhos, você economiza milhares de transações com seus custos de gás associados e tempo pessoal precioso. Em vez de colher e vender recompensas manualmente, comprar mais tokens e reinvestir isso continuamente, um cofre faz tudo isso automaticamente em alta frequência.

Os cofres são o centro do ecossistema Beefy. Em um cofre Beefy, você ganha mais do ativo que você deposita, independentemente de ser uma moeda de pool de liquidez (LP) ou um único ativo. Por exemplo, cofres onde se pode depositar BTC-BNB LP resultarão em mais BTC-BNB LP ao longo do tempo, aumentando efetivamente sua parte no cofre e, assim, permitindo mais e mais recompensas ao longo do tempo.

Apesar do que o nome 'Cofre' sugere, os fundos dos usuários nunca ficam trancados em nenhum cofre na Beefy. Você pode retirar seus fundos de um cofre a qualquer momento. A Beefy também não é proprietária dos fundos de usuários depositados nos cofres. No entanto, geralmente é melhor ver os cofres como ferramentas de investimento para armazenar fundos a médio e longo prazo, para que os efeitos dos reinvestimentos realmente aconteçam.

Ao navegar pelos cofres da plataforma, você verá o rendimento percentual anual (APY), que leva em consideração o reinvestimento frequente em comparação com a taxa percentual anual (APR), que não o faz. Você também verá porcentagens de juros diárias e o valor total investido em um cofre por todos os usuários (TVL). Além disso, pode-se ver qual plataforma subjacente o cofre está usando como fonte de receita.

Cada cofre pode se referir a um par de moedas investidas em pools de liquidez, como moedas CAKE-BNB LP dentro do ecossistema Binance Smart Chain, ou uma única moeda investida em plataformas de empréstimo ou pools de recompensa de uma única moeda. Depois de depositar moedas em um cofre, o usuário recebe moedas 'moo' específicas do cofre que representam a sua parte no cofre. Vamos elaborar sobre as moedas 'moo' na próxima seção.

Qualquer pessoa da comunidade pode trabalhar em conjunto para construir novas estratégias e submetê-las à governança para votação. No entanto, um novo cofre não será aceito se a plataforma subjacente não aderir às [beefy-safu-practices.md](../protocolo-safu/beefy-safu-practices.md "mention") da Beefy.

Resumindo, os cofres podem:&#x20;

* Executar com eficiência estratégias de aquisição de rendimento.&#x20;
* Recompensas compostas no valor da moeda inicialmente depositada.&#x20;
* Usar qualquer ativo como liquidez.&#x20;
* Fornecer um ativo como garantia para outro.&#x20;
* Gerenciar os colaterais em um nível seguro para mitigar liquidação.&#x20;
* Colocar qualquer ativo a trabalho para gerar rendimento.&#x20;
* Reinvestir os lucros obtidos.&#x20;

Os usuários podem sentar, relaxar e ver seu investimento crescer!

## **O que são moedas moo?**

Uma moeda moo é um comprovante de depósito com juros em forma de moeda que você receberá no momento em que depositar em um cofre da Beefy. Uma moeda moo é única por cofre, por exemplo você recebe moedas mooBIFI quando deposita BIFI no cofre BIFI Maxi. Pode-se ver as moedas moo como o recibo do seu depósito no cofre.

{% hint style="info" %}
Os usuários da Beefy devem manter suas moedas moo em sua carteira e não vendê-las ou trocá-las, pois você perderá seus ativos depositados nos cofres se o fizer!
{% endhint %}

## **Como as moedas moo ganham juros?**

Os cofres da Beefy criam automaticamente mais do seu ativo depositado na forma de juros compostos. Ao manter as moedas moo em sua carteira, elas estão aumentando em valor em relação ao ativo do cofre correspondente. O número de moedas moo em sua carteira permanecerá constante, mas a quantidade de moedas do cofre que podem ser resgatadas aumenta. Esta é também a razão pela qual as moedas moo não batem 1:1 com o valor da moeda inicialmente depositada.

## **Como resgato moedas moo pelas moedas inicialmente depositadas?**

Sempre que você quiser retirar as moedas que estão depositadas no cofre da Beefy, basta iniciar uma transação de retirada para trocá-las. As moedas moo são então retiradas da sua carteira e queimadas, e seus ativos depositados mais o rendimento serão devolvidos a você.

## **Quais são as vantagens do sistema de moedas moo?**

O sistema de moedas moo da Beefy tem algumas vantagens importantes:&#x20;

1. Moedas moo permitem que qualquer usuário retire sua parte justa dos fundos depositados;
2. o sistema permite que você deposite as moedas moo em uma carteira fria ou de hardware para maior segurança;
3. sua privacidade é mantida, pois você permanece anônimo à Beefy. Seus fundos no cofre não estão vinculados ao endereço da carteira a partir do qual você fez o depósito, pois as moedas moo são as únicas evidências da sua participação no cofre. Portanto, você pode retirar sua parte dos fundos de um endereço diferente se mover suas moedas moo para ele;
4. moedas moo têm benefícios fiscais: como você não está vendendo recompensas, nem recebendo recompensas de depósito direto para seu endereço, você não tem eventos tributáveis ​​quando tem fundos depositados em um cofre;
5. Por fim, as moedas moo podem ser usadas ​​como garantia com juros.

## **Com que frequência os cofres colhem seus lucros e reinvestem?**

Os cofres são normalmente colhidos várias vezes ao dia e os lucros são automaticamente reinvestidos (compostos). Você pode verificar a taxa de colheita e composição de um cofre usando [este guia de instruções](../faq-perguntas-frequentes/guias-praticos/how-to-check-harvesting-compounding-rate.md).

## **Por que alguém não pode fazer isso sozinho?**

Eles podem, mas os cofres ajudam você a economizar tempo pessoal e taxas de transação, manter índices saudáveis ​​de garantia para dívida, auto-otimizar para obter os melhores rendimentos possíveis e reinvestir os ganhos automaticamente. A tentativa de fazer isso manualmente resultaria em grandes ineficiências. Na Beefy gostamos de dizer: "Sente-se e relaxe, o cofre faz todo o trabalho para você."

## **Qual é a estrutura de taxas do cofre?**

A maioria dos cofres tem uma estrutura de taxa de desempenho, recebendo um percentual das recompensas da colheita. Essa taxa sobre os lucros é distribuída de volta à pool de recompensas e a aqueles que depositam BIFI, alocada ao tesouro, para o estrategista que desenvolveu o cofre e para quem ativa a função de colheita. Essas taxas já estão incorporadas ao APY de cada cofre e taxa diária. Você não precisa calculá-los sozinho. A taxa de desempenho e a estrutura de taxas são mostradas dentro do módulo de Depósito e Saque em um cofre.

A taxa de desempenho sobre o rendimento adicional, ou seja, os lucros do cofre, são em parte distribuídos de volta a aqueles que depositam BIFI e é a principal fonte de receita da plataforma da Beefy. Uma parte também financia o tesouro que é usado para financiar ainda mais o desenvolvimento de plataformas, segurança e outras iniciativas. A taxa de desempenho também foi implementada para promover o engajamento da comunidade e a participação na governança. Uma comunidade bem-sucedida e engajada é fundamental para nosso crescimento futuro, o que, por sua vez, recompensa ainda mais os usuários da plataforma.

Além disso, alguns cofres têm uma taxa de retirada. O principal objetivo dessa taxa é evitar possíveis hacks de pessoas de má-fé. Sem a taxa, alguém poderia depositar logo antes da execução da função harvest() e sacar logo após esse evento, recebendo uma % dos ganhos gerados por apostadores legítimos. As taxas de saque permanecem no cofre e são compartilhadas entre os fundos do cofre.

Finalmente, para os usuários de nossa ferramenta Beefy ZAP V2, cobramos uma taxa zap de 0,05% sobre seus valores depositados ao entrar ou sair de um cofre. Estas taxas são devolvidas à tesouraria da Beefy por meio de uma tesouraria de lotes intermediários, o que permite que as taxas sejam agregadas e trocadas em estábulos antes de serem depositadas. Veja [how-to-beefy-zap.md](../faq-perguntas-frequentes/guias-praticos/how-to-beefy-zap.md "mention") para mais detalhes sobre a ferramenta ZAP V2.

## O que é "coleta no depósito"?

Muitos dos cofres da Beefy "coletam no depósito". isso significa que quando você deposita no cofre, você também está chamando a função de coleta na estratégia do cofre. Chamando a função de coleta, você ativa a coleta de recompensas pendentes e o reinvestimento dessas recompensas de volta nas moedas do cofre para todo mundo.

A Beefy faz isso para que seja impossível que pessoas má-intencionadas  roubem os rendimentos, logo uma taxa de retirada não é necessária. Isso beneficia bastante os investidores de longo prazo.

Quase todos os cofres em redes mais baratas como Fantom e Polygon coletam no depósito. Você tem como dizer ser um cofre coleta no depósito se ele não tem taxa de retirada.

Por depositar e chamar a função de depósito, você receberá uma recompensa na forma da moeda nativa da rede (ex: WFTM ou WMATIC) devido a taxa da chamada de função de coleta.

## Coletando na Ethereum

Como as taxas de transação no Ethereum são caras, a Beefy introduziu algumas regras que determinam a frequência da colheita do cofre.

* O TVL do cofre está acima de $100k: o cofre fará a coleta a cada 3 dias.
* O TVL do cofre está abaixo de $100k, mas acima de $10k: o cofre fará a coleta a cada 15 dias.
* O TVL do cofre está abaixo de $10K: coleta comunitária.

A coleta comunitária implica que a função de coleta no contrato estratégico tem que ser chamada manualmente, e as taxas de transação para isso não serão subsidiadas pela Beefy.

Outra regra vigia os preços do _gas_ no Ethereum. Se o `maxGasPrice` for de 20 GWei ou mais, as coletas não serão executadas, pois serão muito caras. Isto é independente do TVL de um cofre.

O _Gelato Off-Chain Resolver_ que processa as coletas na Ethereum com base nas regras acima mencionadas pode ser encontrado seguindo este link: [Gelato Automate](https://beta.app.gelato.network/task/0xe27256b6b3109b9d53e2aded267c1be317e53dce78021d374e02284d144d44c3?chainId=1). O contrato inteligente e seus parâmetros, assim como Execuções passadas e Registros de Tarefas, também são facilmente acessíveis lá.

## Coletando na BNB Chain

Também temos uma restrição de coleta ativa na BNB Chain:

* Se o TVL do cofre está abaixo de $10K a mais de 2 semanas: coleta comunitária

## **A taxa de desempenho é retirada quando eu retiro meus fundos?**

* Não, as taxas de desempenho são sobre os lucros e são cobradas toda vez que alguém ativa a função harvest().

## **A página do cofre mostra o APY?**

Sim. Nossos valores APY exibidos refletem a taxa prevista obtida em um cofre em um ano. Essa taxa é determinada pela plataforma subjacente que ela usa, a estratégia com a qual está interagindo no momento, a quantidade total de fundos no cofre e também leva em consideração o efeito da composição. Como recurso exclusivo, também incluímos todas as taxas do cofre no cálculo do APY. O que você vê é o que você recebe!

## **Quais são os riscos dos cofres?**

Os cofres são auditados, mas isso não significa que um cofre seja totalmente livre de riscos. Abaixo estão alguns dos riscos gerais dos cofres:

* Os ativos depositados no cofre não têm risco de diminuir em quantidade, mas podem diminuir em valor monetário.
* Como em qualquer contrato inteligente, o risco mais temido é que os fundos de um investidor acabem sendo roubados ou não possam ser sacados. A equipe toma medidas para quantificar os riscos de segurança dos contratos inteligentes e só interage com aqueles que atendem a um conjunto específico de requisitos após testes excessivos para garantir que a plataforma subjacente não contenha as chamadas funções 'puxa-tapete'. Para uma explicação detalhada das etapas que a Beefy toma antes de adicionar um cofre novo, por favor, consulte as [beefy-safu-practices.md](../protocolo-safu/beefy-safu-practices.md "mention") da Beefy.

Riscos mais detalhados dos cofres, ou melhor ainda, informações sobre a segurança de cofre do Beefy expressas pelo Beefy Safety Score podem ser encontradas aqui: [Escore de Segurança Beefy.](../protocolo-safu/beefy-safety-score.md)

## **Quais são os diferentes cofres?**

* **Money Market :** utiliza plataformas de empréstimo, como Venus na BNB Chain, para gerar o maior rendimento possível para essas moedas (por exemplo, BUSD, BNB, LINK, DOT, DAI, USDT, ETH ou BTCB).
* **Farm de Moeda Nativa :** Aproveita o alto rendimento em "fazendas" de rendimento populares depositando outro ativo para ganhar, vender e aumentar os lucros da moeda de recompensa nativa.

## O que vou ganhar quando fizer uma retirada do cofre?

Você sempre retirará o tipo de moeda que depositou, porque na Beefy você ganha na moeda que deposita. Você receberá a quantidade que depositou mais o rendimento gerado menos as taxas de retirada do cofre. No caso de cofres que suportam Beefy ZAP, usuários podem retirar diretamente em uma das moedas que compõem o par da LP pelo ZAP V1 e em uma das moedas bluechip, nativas ou estáveis suportadas pelo ZAP V2.

## **Como funcionam os cofres de LP?**

Os cofres de pools de liquidez (LP) funcionam reinvestindo as taxas concedidas aos participantes do LP. Em troca de fornecer liquidez às pools, muitas plataformas recompensam os investidores com moedas. Nossos cofres coletam regularmente essas recompensas, vendem, compram mais dos ativos subjacentes da LP e depois reinvestem para completar o ciclo.

Isso compõe as recompensas obtidas com uma pool de liquidez. A Beefy cria estratégias que automatizam esse processo, economizando tempo e taxas de gás em comparação com  fazer isso manualmente. Tudo isso é feito por uma pequena taxa que é distribuída de volta para aqueles que participam da pool de governança da Beefy ou do cofre BIFI Maxi. Uma pequena porcentagem também vai para o tesouro da Beefy.

## **Com que frequência os saldos são atualizados no vaults?**

As recompensas pendentes não são refletidas no saldo até que sejam trocadas pela moeda depositada inicialmente. Isso pode variar dependendo da estratégia em execução.

## **Como os cofres são adicionados na Beefy?**

Novos cofres em potencial podem ser discutidos em nosso Discord no canal #whiteboard. Nossos estrategistas adicionam a estratégia de investimento potencial à nossa lista de estratégias. Uma prioridade é atribuída a cada nova estratégia potencial com base em seu APY, TVL e sustentabilidade. Nossos desenvolvedores/estrategistas então atacam a lista da maior prioridade para a inferior. O fórum oficial é usado para enviar [solicitações de cofre](https://forum.beefy.finance/c/vault-requests/6).

Então, a plataforma que no qual cofre vai potencialmente depositar é minuciosamente inspecionada, verificando se tem contratos inteligentes seguros e nenhuma característica perigosa. Para mais informações sobre isso, por favor, leia as [beefy-safu-practices.md](../protocolo-safu/beefy-safu-practices.md "mention") da Beefy.

## **Qual é o seu processo de nomenclatura dos cofres?**

Cada cofre na plataforma tem o nome da moeda que os usuários podem depositar nele. Por exemplo, o cofre CAKE-BNB LP usa moedas CAKE-BNB LP para sua estratégia de investimento. Um cofre BTC usa a moeda BTC, etc.&#x20;

Abaixo do nome do cofre, você pode encontrar a plataforma usada para investir a moeda e obter seus rendimentos. Por exemplo, usos: Venus significa que esse cofre específico investe a moeda na Venus, um mercado monetário (Money Market) algorítmico DeFi e protocolo de moeda estável sintética.

## **Como funcionam os cofres de empréstimo?**

_O seguinte se aplica a: Aave, Banker Joe, Blizz, Geist, Scream, Venus e plataformas de empréstimo semelhantes._

A maioria dos cofres de ativos únicos da Beefy utiliza mercados descentralizados para credores e mutuários. Ao depositar seu ativo inicial no cofre, a Beefy o deposita no mercado de empréstimos e empresta sua moeda em níveis seguros de garantia.&#x20;

As moedas emprestadas são redepositadas na plataforma e mais uma vez usadas ​​como garantia para emprestar mais moedas. Esse ciclo é repetido várias vezes para gerar o máximo de juros possível dos juros do empréstimo e da moeda de recompensa, que é usada para comprar mais de seus ativos originalmente depositados. Essa estratégia também é conhecida como estratégia de dobra. Vale ressaltar que esses empréstimos múltiplos "alavancados" são apenas com a moeda do cofre depositado, portanto, não há risco de liquidação devido a oscilações de preço da moeda.

{% hint style="info" %}
Taxas de transação: devido ao ciclo múltiplo de fornecimento e empréstimo, a taxa de transação para um depósito ou retirada desses cofres geralmente é mais alta em comparação com outros cofres.
{% endhint %}

{% hint style="warning" %}
Risco de comercialização: quando a moeda subjacente na plataforma de empréstimo fica emprestada em excesso, pode impedir que a estratégia do cofre seja desalavancada (desdobrada) para acomodar uma retirada. Isso geralmente acontece quando o mercado está mais volátil ou quando há um evento em andamento para o qual as pessoas desejam emprestar fundos da plataforma de empréstimos. A condição de endividamento excessivo se resolverá naturalmente quando a liquidez retornar à plataforma de empréstimo, um processo que pode levar horas ou, às vezes, alguns dias. Enquanto isso, os fundos sempre permanecem seguros.
{% endhint %}

Devido ao acúmulo de juros de dívida/fornecimento, pode-se notar que o valor da moeda depositada pode diminuir ligeiramente entre as colheitas. Após o evento de colheita, você verá o valor da moeda depositada aumentar à medida que os rendimentos são compostos novamente. A mudança no valor da moeda depositada ao longo do tempo de um cofre de estilo de empréstimo típico é o seguinte:

![Depois de uma colheita, o lucro é adicionado à moeda depositada.](../.gitbook/assets/venus-style-vault.png)


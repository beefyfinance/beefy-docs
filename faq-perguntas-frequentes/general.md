# Geral

## A Beefy é auditada?

Nosso primeiro auditor foi a DefiYield, que auditou a moeda $BIFI, a RewardPool e todas as nossas trancas de tempo.

A Beefy agora também foi auditada pela Certik, o que garante a robustez de nossos contratos inteligentes e a segurança dos fundos investidos pela Beefy.

A Certik também auditou algumas das estratégias de investimento reutilizáveis mais complexas ​​usadas na plataforma. Isso garante a segurança e a robustez de aspectos importantes de contratos inteligentes com os quais a maioria de nossos usuários interagem.

[Todas as auditorias da Beefy podem ser encontradas aqui](https://github.com/beefyfinance/beefy-audits).

## **O que é um otimizador de rendimento?**

Um otimizador de rendimento é um serviço automatizado que busca obter o máximo retorno possível de investimentos em criptomoedas, de forma muito mais eficiente do que tentar maximizar o rendimento por meios manuais.

Cada cofre tem sua própria estratégia exclusiva para gerência de rendimentos, que normalmente envolve o reinvestimento de criptomoedas depositadas em pools de liquidez. No nível mais simples, ele coleta as recompensas dadas pelos fundos depositados e os reinveste de volta na pool de liquidez. Isso aumenta o valor dos juros recebidos e aumenta o o depósito no qual o rendimento se baseia. Um otimizador de rendimento pode repetir esse processo milhares de vezes por dia.&#x20;

Este método bastante simples é a principal razão por trás dos grandes APYs encontrados na Beefy. As taxas de composição são amortizadas entre todos os participantes do cofre, tornando-as mais baratas para os usuários.

## **Qual é a diferença entre APR e APY?**

APR é o juros anual, menos as taxas. Isso não inclui efeitos de composição que ocorrem a partir do reinvestimento de lucros (juros compostos). Se você investisse $100 com 100% APR, você faria $100 em lucro em um ano.

Se, no entanto, você reinvestir seus lucros regularmente, você aumentará seus juros. Isso calculado ao longo de um ano fornece seu APY. Quanto mais vezes você capitalizar seus juros, maior será a diferença entre APR e APY.&#x20;

## **Como funciona o APY?**

APY é o rendimento percentual anual oferecido a partir de um determinado investimento. Isso leva em conta juros compostos, dando a você uma ideia precisa de seus retornos em comparação com os juros simples.&#x20;

Grandes APYs na porcentagem de milhares são possíveis com investimentos que fornecem rendimentos diários de 1% ou mais. Devido às recompensas das suas pool de liquidez serem constantemente coletadas e reinvestidas, os juros se acumulam em quantias cada vez maiores.

## **O que significam o Vault Daily e o Trading Daily?**

![](../.gitbook/assets/vault-trading-daily.png)

Trading Daily significa quanto suas moedas em uma pool de liquidez aumentarão em valor. As pools de liquidez compartilham as taxas de trocas entre todos os provedores de liquidez, conforme o [modelo de liquidez Uniswap](https://docs.uniswap.org/protocol/V2/concepts/advanced-topics/fees). O Trading Daily é afetado pelo volume de trocas e pela porcentagem das taxas de trocas alocadas aos provedores de liquidez.

Vault Daily significa quanto a sua aumentará em número. Devido ao cofre constantemente coletar e reinvestir as recompensas, o valor do seu depósito aumentará. O Vault Daily é afetado pelas recompensas (ou seja, incentivos adicionais além das taxas de trocas), como a CAKE na Pancakeswap.

Trading Daily e Vault Daily podem ser multiplicados por 365 para calcular o Trading APR e o Vault APR. O Vault APR (APR do cofre) é então convertido em Vault APY (APY do cofre) para levar em consideração os juros compostos. A porcentagem total de APY exibida é calculada da seguinte forma:

$$
APY = (1 + vaultAPY) * (1 + tradingAPR) - 1
$$

{% hint style="info" %}
Para calcular o Trading APR, a Beefy usa dados da rede e um período de 24h para determinar o volume de troca e as taxas subsequentes, enquanto a maioria das DEXes usa um período de 7 dias. Isso pode levar a diferenças de APY exibido quando comparado com uma corretora descentralizada, mas saiba que isso é devido ao método de cálculo. Na verdade, nós diríamos que a Beefy é mais precisa por usar um menor período de tempo que reflete as mudanças no Trading APR mais cedo.
{% endhint %}

Uma ferramenta útil para converter APR para APY é: [APRtoAPY.com](https://www.aprtoapy.com/)

## **Como eu contribuo para a Beefy?**

A Beefy é um projeto desenvolvido pela comunidade desde o primeiro dia. Se você quiser se juntar ao nosso grupo de colaboradores, depende do que você gostaria de fazer. Temos vagas abertas para desenvolvedores de Solidity, ou desenvolvedores que desejam iniciar uma carreira em Solidity, para ingressar como estrategista e implementar cofres (e ganhar renda passiva com as taxas de estrategista). A Beefy está em várias redes e há frequentes oportunidades para cofres simples e complexos. Você pode começar com os mais simples e depois progredir para os mais difíceis à medida que seu conhecimento de Solidity cresce. Você não precisa ser o melhor desde o início e tenha certeza de que existe um processo de revisão rigoroso para garantir a segurança e a qualidade. Você pode entrar em contato com nossos estrategistas líderes no[ Discord](https://discord.gg/yq8wfHd) da Beefy em #strategy-devs.

A Beefy também gostaria que as pessoas trabalhassem em projetos não estratégicos; qualquer coisa que se possa pensar pode ser formulada em um subsídio. Fale com outras pessoas no nosso cowmoonity sobre projetos e junte-se a uma das equipes ou lidere uma você mesmo, você pode ser pago por qualquer trabalho que fizer para tornar a Beefy melhor. Uma lista rápida de subsídios anteriores: [aqui](https://forum.beefy.finance/c/grant-ideas/11) e [aqui](https://forum.beefy.finance/c/grant-requests-b1/10). A Beefy V2 foi um projeto que requereu todos os tipos de desenvolvedores, não apenas técnicos; a contribuição no design foi crucial para melhorar a UI/UX.

O [GitHub da Beefy](https://github.com/beefyfinance) abrange a ideia de colaboração aberta, por isso que muitos dos repositórios são de código aberto. Usamos arquivos CONTRIBUTING.md para permitir que pessoas apenas façam contribuições ou recomendações por meio de Pull-Requests no Github. Você pode começar mesmo apenas atualizando o Git docs ou corrigir um erro de digitação, isso ajuda você a se aproximar da equipe de colaboradores.

Se você tem interesse em desenvolvimento de negócios, pode ajudar com parcerias e propondo decisões de negócios à DAO. A Beefy ainda é relativamente nova aos negócios e se beneficiaria de pessoas talentosas para ajudar a aconselhar a equipe principal.&#x20;

Há marketing para o qual você também pode contribuir, se você souber escrever um tweet decente, poderá ajudar no #tweet-development. O [Discord](https://discord.gg/yq8wfHd) tem um canal #social-watch onde são postados links para menções da Beefy nas redes sociais, você pode ajudar nas dúvidas dos usuários lá ou no próprio [Discord ](https://discord.gg/yq8wfHd)ou [Telegram](https://t.me/beefyfinance). Os moderadores do Discord e do Telegram também são (variavelmente) cargos pagos e geralmente são a primeira linha de suporte ao cliente.

A melhor maneira de se envolver é seguir em frente e começar, ajudar onde puder, contribuir com discussões e colaborar com todos.

## Qual a diferença entre um Cofre e uma Pool de Ganhos?

Em um cofre, você ganha mais do que você depositou nele, com juros compostos (APY). Em uma pool de ganhos, você ganha uma moeda diferente do que aquela que você depositou, com juros simples (APR).

Um exemplo é o cofre BIFI Maxi, no qual você ganha mais BIFI exponencialmente, e as Pools de Ganhos BIFI, nas quais você ganha juros simples na forma de $ETH, $BNB, $AVAX e mais.

## Por que custa tanto _gas_ para depositar em um cofre Beefy?

Muitos cofres da Beefy "coletam no depósito". Isso significa que, quando você deposita no cofre, também está chamando a função de coleta. Chamar a função Harvest é algo mais complexo do que um simples depósito e, portanto, tem uma taxa de _gas_ mais alta. A Beefy faz isso para que seja impossível que agentes maliciosos roubem o rendimento, de modo que uma taxa de retirada não seja necessária. Isso beneficia muito os investidores de longo prazo.

Quase todos os cofres de redes mais baratas, como a Fantom e a Polygon, são coletados em depósito. Você também pode dizer se um cofre coleta no depósito se não houver taxa de retirada.

Como o coletor, você também receberá algumas das moedas nativas da rede embrulhadas como recompensa por chamar a coleta. Consulte o detalhamento das taxas do Beefy Finance para obter mais informações sobre a chamada de coleta. Veja [beefy-finance-fees-breakdown.md](../ecosystem/beefy-bulletins/beefy-finance-fees-breakdown.md "mention") para mais informações sobre o _Harvest Caller_.

## Como posso saber quantos ganhos acumulei?

Suas recompensas são adicionadas à quantidade da moeda depositada em cada coleta e ciclo composto. Você pode usar um painel DeFi que poderá calcular exatamente quanto lucro você obteve em seus investimentos. Ferramentas externas, como a [TopDeFi](https://thetopdefi.com/), lerão o endereço da sua carteira e fornecerão uma imagem precisa do seu investimento inicial e ganhos atuais.

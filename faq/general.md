# Geral

## A Beefy é auditada?

Nosso primeiro auditor foi o DefiYield, que auditou o token $BIFI, o RewardPool e todos os timelocks.

O Beefy agora também é auditado pela Certik, o que garante a robustez de nossos smart contracts e a segurança dos fundos investidos por meio do Beefy. A Certik já forneceu auditorias para projetos como Ocean Protocol, NEO, Ontology e Waves.

A Certik tambem auditou algumas das estratégias de investimento mais complexas e reutilizáveis ​​usadas na plataforma. Isso garante a segurança e a robustez de aspectos importantes da plataforma com os quais a maioria de nossos usuários interagem.

[Todas as auditorias do Beefy podem ser encontradas aqui](https://github.com/beefyfinance/beefy-audits).

## **O que é um otimizador de rendimento?**

Um otimizador de rendimento é um serviço automatizado que busca obter o máximo retorno possível sobre investimentos em criptomoedas, de forma muito mais eficiente do que tentar maximizar o rendimento por meios manuais.

Cada cofre tem sua própria estratégia exclusiva para farming, que normalmente envolve o reinvestimento de ativos criptográficos staked em pools de liquidez. No nível mais simples, ele cultiva as recompensas dadas pelos ativos staked e os reinveste de volta no pool de liquidez. Isso aumenta o valor dos juros recebidos e aumenta o valor apostado no qual o rendimento se baseia. Um otimizador de rendimento pode repetir isso para processar até milhares de vezes por dia. Isso gera juros compostos.

Este método bastante simples é a principal razão por trás dos grandes APYs encontrados no Beefy. As taxas de composição são amortizadas entre todos os participantes do cofre, tornando-o mais barato para o usuário.

## **Qual é a diferença entre APR e APY?**

APR é o juro anual, menos as taxas. Isso não inclui efeitos de composição que ocorrem a partir do reinvestimento de lucros (juros compostos). Se você investisse $100 com 100% APR, você faria $100 em lucro em um ano.

Se, no entanto, você reinvestir seus lucros regularmente, você aumentará seus juros. Isso calculado ao longo de um ano fornece seu APY. Quanto mais vezes você capitalizar seus juros, maior será a diferença entre APR e APY. O beefy automatiza este processo de reinvestimento.

## **Como funciona o APY?**

APY é o rendimento percentual anual oferecido a partir de um determinado investimento. Isso leva em consideração os juros compostos, dando a você uma ideia precisa de seus retornos em comparação com os juros simples.&#x20;

Grandes APYs na porcentagem de milhares são possíveis com investimentos que fornecem rendimentos diários de 1% ou mais. Devido às recompensas do seu pool de liquidez serem constantemente reinvestidas, os juros se acumulam em quantias cada vez maiores.

## **O que significam o Vault Daily e o Trading Daily?**

![](../.gitbook/assets/vault-trading-daily.png)

Trading Daily significa quanto seus tokens de liquidez aumentarão em valor. Os pools de liquidez compartilham as taxas de negociação entre todos os provedores de liquidez, conforme introduzido pelo [modelo de liquidez Uniswap](https://docs.uniswap.org/protocol/V2/concepts/advanced-topics/fees).

O Trading Daily é afetado pelo volume de negociação e pela porcentagem de taxas de swap alocadas aos provedores de liquidez.

Vault Daily significa quanto seu token aumentará em número. Devido ao cofre constantemente cultivar e reinvestir as recompensas, o valor do seu token depositado aumentará. O Vault Daily é afetado pelas recompensas do farming (ou seja, incentivos adicionais além das taxas de negociação), como CAKE no Pancakeswap. Trading Daily e Vault Daily podem ser multiplicados por 365 para calcular o Trading APR e o Vault APR. A APR do Vault é então convertida em Vault APY para levar em consideração os juros compostos. A porcentagem total de APY exibida é calculada da seguinte forma:

$$
APY = (1 + vaultAPY) * (1 + tradingAPR) - 1
$$

Uma ferramenta útil para converter APR para APY é: [APRtoAPY.com](https://www.aprtoapy.com/)

## **Como posso contribuir para o Beefy?**

O Beefy Finance é um projeto desenvolvido pela comunidade desde o primeiro dia. Se você quiser se juntar ao nosso grupo de colaboradores, depende do que você gostaria de fazer. Temos vagas abertas para desenvolvedores de Solidity, ou desenvolvedores que desejam iniciar uma carreira em Solidity, para ingressar como estrategista e implementar cofres (e ganhar renda passiva com as taxas de estrategista). Beefy está em várias chains e muitas vezes há oportunidades para cofres simples e complexos. Você pode começar com os mais simples e depois progredir para os mais difíceis à medida que seu conhecimento de Solidity cresce. Você não precisa ser o melhor desde o início e tenha certeza de que existe um processo de revisão rigoroso para garantir a segurança e a qualidade. Você pode entrar em contato com nossos estrategistas líderes no [Beefy's Discord](https://discord.gg/yq8wfHd) em #strategy-devs.

Beefy também gostaria que as pessoas trabalhassem em projetos não estratégicos; qualquer coisa que você possa pensar pode ser formulada em uma doação. Fale com outras pessoas no nosso cowmoonity sobre projetos e junte-se a uma das equipes ou lidere uma você mesmo, você pode ser pago por qualquer trabalho que fizer para tornar o Beefy melhor. Uma lista rápida de bolsas anteriores: [aqui](https://forum.beefy.finance/c/grant-ideas/11) e [aqui](https://forum.beefy.finance/c/grant-requests-b1/10). Beefy V2 é um projeto em andamento que requer todos os tipos de desenvolvedores, não apenas técnicos; a entrada de design é crucial para melhorar a UI/UX.

O [GitHub da Beefy](https://github.com/beefyfinance) abraça a ideia de colaboração aberta; portanto, muitos dos repositórios são de código aberto. Usamos arquivos CONTRIBUTING.md para permitir que as pessoas apenas façam contribuições ou recomendações por meio de Pull-Requests no Github. Você pode começar mesmo apenas atualizando o Git docs ou corrigir um erro de digitação, ajuda você a se aproximar da equipe de colaboradores.

Se você tem interesse em desenvolvimento de negócios, pode ajudar com parcerias e propondo decisões de negócios ao DAO. A Beefy ainda é um negócio relativamente novo que pode usar pessoas talentosas para ajudar a aconselhar a equipe principal.&#x20;

Há marketing para o qual você também pode contribuir, se você souber escrever um tweet decente, poderá ajudar no desenvolvimento de #tweet. O [Discord](https://discord.gg/yq8wfHd) tem um canal #social-watch onde são postados links para menções do Beefy nas redes sociais, você pode ajudar nas dúvidas dos usuários lá ou no próprio Discord ou Telegram. Os moderadores do [Discord](https://discord.gg/yq8wfHd) e do [Telegram](https://t.me/beefyfinance) também são (variavelmente) cargos pagos e geralmente são a primeira linha de suporte ao cliente.

A melhor maneira de se envolver é seguir em frente e começar, ajudar onde puder, contribuir com discussões e colaborar com todos.

## Por que custa tanto gás para depositar em um cofre Beefy?

Os cofres de Beefy implementam uma função chamada "Harvest". Isso significa que, quando você deposita no cofre, também está chamando essa função Harvest de colheita. Chamar a função Harvest é mais complexo do que um simples depósito e, portanto, tem um limite/taxa de gás mais alto.&#x20;

O Beefy faz isso para que seja impossível que agentes maliciosos roubem o rendimento, de modo que uma taxa de retirada não seja necessária. Isso beneficia muito os investidores de longo prazo. Quase todos os cofres de cadeias mais baratas, como Fantom e Polygon, são coletados em depósito. Você também pode saber se um cofre coleta em depósito se não houver taxa de retirada.

Como o Harvest, você também receberá alguns dos tokens de cadeia nativa embrulhados como recompensa por chamar a colheita. Consulte o detalhamento das taxas do Beefy Finance para obter mais informações sobre o Harvest.

## Como posso saber quantos ganhos acumulei?

Suas recompensas são adicionadas ao valor do token depositado em cada colheita e ciclo composto. Você pode usar um painel DeFi que poderá calcular exatamente quanto lucro você obteve em seus investimentos. Ferramentas externas, como o [TopDeFi](https://thetopdefi.com/), lerão o endereço da sua carteira e fornecerão uma imagem precisa do seu investimento inicial e ganhos atuais.

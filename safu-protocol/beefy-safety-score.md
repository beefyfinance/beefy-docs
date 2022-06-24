# Beefy Safety Score

Este documento descreve o design do Beefy Safety Score. O objetivo da pontuação de segurança é educar os usuários ao tomar a decisão de entrar em um determinado cofre do Beefy. O Safety Score não é necessariamente perfeito, mas é mais uma ferramenta que auxilia o usuário.

A pontuação de segurança que um salto pode obter vai de 0 a 10. A melhor pontuação possível é 10 e a pior é 0. É tecnicamente possível que os saltos tenham pontuação inferior a 0, caso em que 0 será exibido.&#x20;

Os riscos são distribuídos em três categorias principais:

* Beefy Risks: Riscos que adicionamos servindo como plataforma.&#x20;
* Riscos do Ativo: Riscos do ativo sendo manuseado pelo cofre.&#x20;
* Riscos da plataforma: riscos do farm ou plataforma subjacente usada.

Cada categoria é responsável por uma porcentagem da pontuação total. Cada categoria é dividida em várias subcategorias.&#x20;

Todos os saltos começam com uma pontuação perfeita de 10 e são subtraídos pontos sempre que possuem qualidades que aumentam o risco.

## Categoria: Riscos Beefy

São riscos relacionados à própria plataforma Beefy Finance. Esses podem ser riscos adicionados pela complexidade da estratégia do vault, se for uma implantação experimental, se tiver sido auditada por outros, etc. Vinte por cento da pontuação de segurança é determinada pelos Beefy Risks.

### Subcategory: Complexity

Rastreia a complexidade da estratégia por trás de um cofre.

#### COMPLEXITY\_LOW

* Título: Estratégia de baixa complexidade
* Explicação: As estratégias de baixa complexidade têm poucas partes móveis, se houver, e seu código é fácil de ler e depurar. Existe uma correlação direta entre a complexidade do código e o risco implícito. Uma estratégia simples reduz efetivamente os riscos de implementação.&#x20;
* Citérios de Qualificação: Uma estratégia de baixa complexidade deve interagir com apenas um contrato inteligente auditado e conhecido, por exemplo. Mestre cozinheiro. A estratégia serve de fachada para esse contrato inteligente, encaminhando chamadas de depósito, colheita e saque usando uma única linha de código.

#### COMPLEXITY\_MID

* Título: A estratégia Beefy é de média complexidade&#x20;
* Explicação: Estratégias de média complexidade interagem com dois ou mais contratos inteligentes auditados e conhecidos. Seu código ainda é fácil de ler, testar e depurar. Ele mitiga a maioria dos riscos de implementação mantendo as coisas simples, no entanto, as interações entre 2 ou mais sistemas adicionam uma camada de complexidade.&#x20;
* Critérios de Qualificação: Uma estratégia de média complexidade interage com 2 ou mais contratos inteligentes conhecidos. Essa estratégia automatiza a execução de uma série de etapas sem caminhos de bifurcação. Toda vez que deposit(), harvest() e retirar() são chamados, o mesmo caminho de execução é seguido.

#### COMPLEXITY\_HIGH

* Título: Estratégia Beefy é complexa&#x20;
* Explicação: As estratégias de alta complexidade interagem com um ou mais contratos inteligentes conhecidos. Essas estratégias avançadas apresentam caminhos de execução ramificados. Em alguns casos, vários contratos inteligentes são necessários para implementar a estratégia completa.&#x20;
* Critérios de Qualificação: Uma estratégia de alto nível de complexidade pode ser identificada por um ou mais dos seguintes fatores: alta complexidade ciclomática, interações entre duas ou mais plataformas de terceiros, implementação dividida entre vários contratos inteligentes.

### Subcategory: Time in Market

Rastreia há quanto tempo essa estratégia está em execução sem grandes problemas.

#### BATTLE\_TESTED

* Título: Estratégia Beefy é testada em batalha&#x20;
* Explicação: Quanto mais tempo uma estratégia específica estiver em execução, maior a probabilidade de que quaisquer bugs em potencial tenham sido encontrados e corrigidos. Essa estratégia já está exposta a ataques e uso há algum tempo, com pouca ou nenhuma alteração. Isso o torna mais resistente.&#x20;
* Critérios de qualificação:&#x20;
  * Foi implantado usando um BeefyStratFactory&#x20;
  * Mais de 10 estratégias que compartilham o mesmo código implantado&#x20;
  * 3 meses trabalhando como esperado sem atualizações

#### NEW\_STRAT

* Título: A estratégia está em execução há menos de um mês&#x20;
* Explicação: Quanto mais tempo uma estratégia específica estiver em execução, maior a probabilidade de que quaisquer bugs potenciais tenham sido encontrados e corrigidos. Esta estratégia é uma modificação ou iteração de uma estratégia anterior. Não foi testado em batalha tanto quanto outros.&#x20;
* Critérios de Qualificação: -

#### EXPERIMENTAL\_STRAT

* Título: A estratégia tem algumas características que são novas&#x20;
* Explicação: Quanto mais tempo uma estratégia específica estiver em execução, maior a probabilidade de que quaisquer bugs em potencial tenham sido encontrados e corrigidos. Essa estratégia é nova e tem pelo menos um recurso experimental. Use-o com cuidado a seu próprio critério.&#x20;
* Critérios de Qualificação: -

## Category: Asset Risks

Riscos relacionados ao ativo ou ativos manipulados pelo cofre. Entrar em um cofre com BTC tem um conjunto diferente de riscos do que entrar em um cofre com uma moeda mais nova e menor. Vinte por cento da pontuação é determinada por esta categoria.

### Subcategory: Impermanent Loss

Rastreia o risco de perda temporária dentro do cofre

#### IL\_NONE

* Título: IL projetado muito baixo ou zero&#x20;
* Explicação: O ativo neste cofre tem muito pouca ou nenhuma perda temporária esperada. Isso pode ser porque você está apostando em um único ativo ou porque os ativos no LP estão fortemente correlacionados, como USDC-USDT ou WBTC-renBTC.&#x20;
* Critérios de qualificação: cofres de ativos únicos e cofres que gerenciam stablecoins com um peg que não é experimental: USDT, USDC, DAI, sUSD, etc.

#### IL\_LOW

* Título: IL projetada baixa&#x20;
* Explicação: Quando você está fornecendo liquidez em um par de tokens, por exemplo, ETH-BNB, existe o risco de que esses ativos se desvinculem de preço. O BNB pode cair consideravelmente em relação ao ETH. Você perderia alguns fundos como resultado, em comparação com apenas manter ETH e BNB por conta própria. Os ativos neste cofre têm alguns riscos de perda temporária.&#x20;
* Critérios de qualificação: Cofres que lidam com o que normalmente são chamados de LPs “Pool 1” se encaixam aqui: ETH-USDC, MATIC-AAVE, etc. Os tokens de governança para projetos menores são normalmente conhecidos como “Pool 2” e, portanto, excluídos.

#### IL\_HIGH

* Título: IL de alta projeção&#x20;
* Explicação: Quando você está fornecendo liquidez em um par de tokens, por exemplo, ETH-BNB, existe o risco de que esses ativos se desvinculem de preço. O BNB pode cair consideravelmente em relação ao ETH. Você perderia alguns fundos como resultado, em comparação com apenas manter ETH e BNB por conta própria. Os ativos neste cofre têm um risco alto ou muito alto de perda temporária.&#x20;
* Critérios de qualificação: Vaults que lidam com LPs “Pool 2” vão aqui. Esses LPs normalmente incluem o token de governança do próprio farm.

#### ALGO\_STABLE

* Título: Estável algorítmico, peg experimental
* Explicação: Quando você está fornecendo liquidez em um par de tokens, por exemplo, ETH-BNB, existe o risco de que esses ativos se desvinculem de preço. O BNB pode cair consideravelmente em relação ao ETH. Você perderia alguns fundos como resultado, em comparação com apenas manter ETH e BNB por conta própria. Pelo menos uma das stablecoins mantidas por este cofre é um estável algorítmico. Isso significa que o peg estável é experimental e altamente arriscado. Use-o com cuidado a seu próprio critério.&#x20;
* Critérios de Qualificação: “Stablecoins” com pegs experimentais, ou tokennomics que falharam repetidamente em manter seu peg no passado, acesse aqui.

### Subcategory: Liquidity

Tracks how difficult it is to buy/sell the vault's token.

#### LIQ\_HIGH

* Título: Alta liquidez comercial&#x20;
* Explicação: A liquidez de um ativo afeta o risco de mantê-lo. Os ativos líquidos são negociados em muitos lugares e com bom volume. O ativo detido por este cofre tem alta liquidez. Isso significa que você pode trocar seus ganhos facilmente em muitos lugares.&#x20;
* Critérios de Qualificação: -

#### LIQ\_LOW

* Título: Baixa liquidez comercial&#x20;
* Explicação: A liquidez de um ativo afeta o risco de mantê-lo. Os ativos líquidos são negociados em muitos lugares e com bom volume. O ativo detido por este cofre tem baixa liquidez. Isso significa que não é tão fácil trocar e você pode incorrer em alta derrapagem ao fazê-lo.&#x20;
* Critérios de Qualificação: -

### Subcategory: Market Cap

Valor total de todas as moedas em circulação. Indiretamente rastreia quão volátil é o ativo subjacente do cofre.

#### MCAP\_LARGE

* Título: Alta capitalização de mercado, ativo de baixa volatilidade&#x20;
* Explicação: A capitalização de mercado do ativo criptográfico afeta diretamente o risco de mantê-lo. Normalmente, um valor de mercado pequeno implica alta volatilidade e baixa liquidez. O ativo detido por este cofre tem uma grande capitalização de mercado. Isso significa que é potencialmente um ativo altamente seguro para manter. O ativo tem um alto potencial para permanecer e crescer ao longo do tempo.&#x20;
* Critérios de qualificação: Top 50 MC por Gecko/CMC

#### MCAP\_MEDIUM

* Title: Valor médio de mercado, ativo de volatilidade média&#x20;
* Explicação: A capitalização de mercado do ativo criptográfico afeta diretamente o risco de mantê-lo. Normalmente, um valor de mercado pequeno implica alta volatilidade e baixa liquidez. O ativo detido por este cofre tem uma capitalização de mercado média. Isso significa que é potencialmente um ativo seguro para manter. O ativo tem potencial para permanecer e crescer ao longo do tempo.&#x20;
* Critérios de Qualificação: Entre 50 e 300 MC por Gecko/CMC

#### MCAP\_SMALL

* Título: Pequena capitalização de mercado, ativo de alta volatilidade&#x20;
* Explicação: A capitalização de mercado do ativo criptográfico afeta diretamente o risco de mantê-lo. Normalmente, um valor de mercado pequeno implica alta volatilidade e baixa liquidez. O ativo detido por este cofre tem uma pequena capitalização de mercado. Isso significa que é potencialmente um ativo arriscado para manter. O ativo tem baixo potencial para permanecer e crescer ao longo do tempo.&#x20;
* Critérios de Qualificação: Entre 300 e 500 MC por Gecko/CMC

#### MCAP\_MICRO

* Título: Micro capitalização de mercado, ativo de extrema volatilidade&#x20;
* Explicação: A capitalização de mercado do ativo criptográfico afeta diretamente o risco de mantê-lo. Normalmente, um valor de mercado pequeno implica alta volatilidade e baixa liquidez. O ativo detido por este cofre tem um micro valor de mercado. Isso significa que é potencialmente um ativo altamente arriscado para manter. O ativo tem baixo potencial de permanência.&#x20;
* Critérios de Qualificação: +500 MC por Gecko/CMC

### Subcategory: Supply

Rastreia riscos relacionados ao fornecimento de ativos. Pode ser alterado por qualquer pessoa? Quão centralizado é?

#### SUPPLY\_CENTRALIZED

* Título: Poucas baleias muito poderosas&#x20;
* Explicação: Quando a oferta está concentrada em poucas mãos, elas podem afetar bastante o preço de venda. As baleias podem manipular o preço da moeda. Quanto mais pessoas tiverem interesse em uma moeda, melhor e mais orgânica será a ação do preço.&#x20;
* Critérios de Qualificação: Menos de 50 contas detêm mais de 50% da oferta.

## Category: Platform Risks

Riscos relacionados às plataformas de terceiros usadas pelo cofre. Quanto histórico eles têm, quão sólido é o código, há alguma ação perigosa que um administrador pode tomar, etc. Sessenta por cento da pontuação é determinada por esta categoria.

### Subcategory: Reputation

Tenta dar pistas sobre o histórico da equipe e da comunidade. Qual a probabilidade de eles tapete, por exemplo.

#### PLATFORM\_ESTABLISHED

* Título: A plataforma tem um histórico conhecido&#x20;
* Explicação: Ao participar de um farm, pode ser útil saber há quanto tempo a plataforma existe e o grau de sua reputação. Quanto maior o histórico, mais investimento a equipe e a comunidade têm por trás de um projeto. Este cofre armazena um projeto que existe há muitos meses.&#x20;
* Critérios de Qualificação: O farm subjacente existe há pelo menos 3 meses.

#### PLATFORM\_NEW

* Título: A plataforma é nova com pouco histórico&#x20;
* Explicação: Ao participar de um farm, pode ser útil saber há quanto tempo a plataforma existe e o grau de sua reputação. Quanto maior o histórico, mais investimento a equipe e a comunidade têm por trás de um projeto. Este cofre cultiva um novo projeto, com menos de alguns meses em aberto.&#x20;
* Critérios de Qualificação: O farm subjacente existe há menos de 3 meses.

### Subcategory: Security

Acompanha várias boas práticas de contratos inteligentes.

#### NO\_AUDIT

* Título: A plataforma nunca foi auditada por auditores confiáveis de terceiros&#x20;
* Explicação: As auditorias são revisões de código por um grupo de desenvolvedores terceirizados.&#x20;
* Critérios de Qualificação: -

#### AUDIT

* Título: A plataforma tem uma auditoria de pelo menos um auditor confiável&#x20;
* Explicação: As auditorias são revisões de código por um grupo de desenvolvedores terceirizados.&#x20;
* Critérios de Qualificação: Uma ou mais auditorias de um auditor que tenha algum histórico positivo no espaço.

#### CONTRACTS\_VERIFIED

* Título: Todos os contratos relevantes são verificados publicamente&#x20;
* Explicação: O código em execução em um contrato específico não é público por padrão. Os exploradores de blocos permitem que os desenvolvedores verifiquem o código por trás de um contrato específico. Essa é uma boa prática porque permite que outros desenvolvedores auditem se o código faz o que deveria. Todos os contratos de terceiros que este cofre usa são verificados. Isso o torna menos arriscado.&#x20;
* Critérios de Qualificação: -

#### CONTRACTS\_UNVERIFIED

* Título: Alguns contratos não são verificados&#x20;
* Explicação: O código em execução em um contrato específico não é público por padrão. Os exploradores de blocos permitem que os desenvolvedores verifiquem o código por trás de um contrato específico. Essa é uma boa prática porque permite que outros desenvolvedores auditem se o código faz o que deveria. Alguns dos contratos de terceiros que este cofre usa não são verificados. Isso significa que há certas coisas que os desenvolvedores do Beefy não foram capazes de inspecionar.&#x20;
* Critérios de Qualificação: -

#### ADMIN\_WITH\_TIMELOCK

* Título: Funções perigosas estão por trás de um timelock&#x20;
* Explicação: Às vezes, o proprietário do contrato ou administrador pode executar determinadas funções que podem colocar os fundos do usuário em risco. A melhor coisa é evitá-los completamente. Se eles devem estar presentes, é importante mantê-los atrás de um timelock para dar o aviso adequado antes de usá-los. Este contrato tem certas funções administrativas perigosas, mas pelo menos estão por trás de um Timelock significativo.&#x20;
* Critérios de Qualificação: Há pelo menos uma função presente que pode limitar parcial ou completamente os fundos do usuário. A função deve estar atrás de um timelock de +6h.

#### ADMIN\_WITHOUT\_TIMELOCK

* Título: Funções perigosas sem timelock&#x20;
* Explicação: Às vezes, o proprietário do contrato ou administrador pode executar determinadas funções que podem colocar os fundos do usuário em risco. A melhor coisa é evitá-los completamente. Se eles devem estar presentes, é importante mantê-los atrás de um timelock para dar o aviso adequado antes de usá-los. Este contrato tem certas funções de administração perigosas e não há bloqueio de tempo presente. Eles podem ser executados a qualquer momento.&#x20;
* Critérios de Qualificação: Há pelo menos uma função presente que pode limitar parcial ou completamente os fundos do usuário. A função não possui proteção de bloqueio de tempo.

# Escore de Segurança da Beefy(Beefy Safety Score)

Este documento descreve o design do Escore de Segurança da Beefy. O objetivo da pontuação de segurança é educar os usuários ao tomar a decisão de entrar em um determinado cofre do Beefy. O Escore de Segurança não é necessariamente perfeito, mas é mais uma ferramenta que auxilia o usuário.

A pontuação de segurança que um cofre pode obter vai de 0 a 10. A melhor pontuação possível é 10 e a pior é 0. É tecnicamente possível que os cofres tenham pontuação inferior a 0, caso em que 0 será exibido.&#x20;

Os riscos são distribuídos em três categorias principais:

* Riscos Beefy: Riscos que adicionamos servindo como plataforma.&#x20;
* Riscos do Ativo: Riscos do ativo sendo manuseado pelo cofre.&#x20;
* Riscos da plataforma: riscos da pool incentivada ou plataforma subjacente usada.

Cada categoria é responsável por uma porcentagem da pontuação total. Cada categoria é dividida em várias subcategorias.&#x20;

Todos os cofres começam com uma pontuação perfeita de 10 e são subtraídos pontos sempre que possuem qualidades que aumentam o risco.

## Categoria: Riscos Beefy

São riscos relacionados à própria plataforma Beefy. Esses podem ser riscos adicionados pela complexidade da estratégia do cofre, se for um lançamento experimental, se tiver sido auditada por outros, etc. Vinte por cento da pontuação de segurança é determinada pelos Riscos Beefy.

### Subcategoria: Complexidade

Acompanha a complexidade da estratégia por trás de um cofre.

#### COMPLEXIDADE BAIXA

* Título: Estratégia de baixa complexidade
* Explicação: As estratégias de baixa complexidade têm poucas partes móveis, se houver, e seu código é fácil de ler e depurar. Existe uma correlação direta entre a complexidade do código e o risco implícito. Uma estratégia simples reduz efetivamente os riscos de implementação.&#x20;
* Critérios de Qualificação: Uma estratégia de baixa complexidade deve interagir com apenas um contrato inteligente auditado e conhecido, por exemplo, _MasterChef_. A estratégia serve de fachada para esse contrato inteligente, encaminhando chamadas de depósito, coleta e saque usando uma única linha de código.

#### COMPLEXIDADE MÉDIA

* Título: A estratégia Beefy é de média complexidade&#x20;
* Explicação: Estratégias de média complexidade interagem com dois ou mais contratos inteligentes auditados e conhecidos. Seu código ainda é fácil de ler, testar e depurar. Ele mitiga a maioria dos riscos de implementação mantendo as coisas simples, no entanto, as interações entre 2 ou mais sistemas adicionam uma camada de complexidade.&#x20;
* Critérios de Qualificação: Uma estratégia de média complexidade interage com 2 ou mais contratos inteligentes conhecidos. Essa estratégia automatiza a execução de uma série de etapas sem caminhos de bifurcação. Toda vez que `deposit()`, `harvest()` e `withdraw()` são chamados, o mesmo caminho de execução é seguido.

#### COMPLEXIDADE ALTA

* Título: Estratégia Beefy é complexa&#x20;
* Explicação: As estratégias de alta complexidade interagem com um ou mais contratos inteligentes conhecidos. Essas estratégias avançadas apresentam caminhos de execução ramificados. Em alguns casos, vários contratos inteligentes são necessários para implementar a estratégia completa.&#x20;
* Critérios de Qualificação: Uma estratégia de alto nível de complexidade pode ser identificada por um ou mais dos seguintes fatores: alta complexidade ciclomática, interações entre duas ou mais plataformas de terceiros, implementação dividida entre vários contratos inteligentes.

### Subcategoria: Tempo no Mercado

Acompanha há quanto tempo essa estratégia está em execução sem grandes problemas.

#### COMPROVADA PELO TEMPO

* Título: A estratégia Beefy é comprovada pelo tempo&#x20;
* Explicação: Quanto mais tempo uma estratégia específica estiver em execução, maior a probabilidade de que quaisquer bugs em potencial tenham sido encontrados e corrigidos. Essa estratégia já foi exposta a ataques e uso há algum tempo, com pouca ou nenhuma alteração. Isso a torna mais resistente.&#x20;
* Critérios de qualificação:&#x20;
  * Foi implantada usando uma BeefyStratFactory&#x20;
  * Mais de 10 estratégias que compartilham o mesmo código implantadas&#x20;
  * 3 meses trabalhando como esperado sem atualizações

#### ESTRATÉGIA NOVA

* Título: A estratégia está em execução há menos de um mês&#x20;
* Explicação: Quanto mais tempo uma estratégia específica estiver em execução, maior a probabilidade de que quaisquer bugs potenciais tenham sido encontrados e corrigidos. Esta estratégia é uma modificação ou iteração de uma estratégia anterior. Não foi testada pelo tempo tanto quanto outras.&#x20;
* Critérios de Qualificação: -

#### ESTRATÉGIA EXPERIMENTAL

* Título: A estratégia tem algumas características que são novas&#x20;
* Explicação: Quanto mais tempo uma estratégia específica estiver em execução, maior a probabilidade de que quaisquer bugs em potencial tenham sido encontrados e corrigidos. Essa estratégia é nova e tem pelo menos um recurso experimental. Use-a com cuidado a seu próprio critério.&#x20;
* Critérios de Qualificação: -

## Categoria: Riscos dos Ativos

Riscos relacionados ao ativo ou ativos manipulados pelo cofre. Entrar em um cofre com BTC tem um conjunto diferente de riscos do que entrar em um cofre com uma moeda mais nova e menor. Vinte por cento da pontuação é determinada por esta categoria.

### Subcategoria: Perda Impermanente (IL -Impermanent Loss)

Acompanha o risco de perda impermanente dentro do cofre

#### NENHUMA IL

* Título: IL projetada muito baixa ou zero&#x20;
* Explicação: O ativo neste cofre tem muito pouca ou nenhuma perda impermanente esperada. Isso pode ser porque você está depositando um único ativo ou porque os ativos na LP estão fortemente correlacionados, como USDC-USDT ou WBTC-renBTC.&#x20;
* Critérios de qualificação: cofres de ativos únicos e cofres que gerenciam moedas estáveis com um lastro que não é experimental: USDT, USDC, DAI, sUSD, etc.

#### BAIXA IL

* Título: IL projetada baixa&#x20;
* Explicação: Quando você está fornecendo liquidez em um par de moedas, por exemplo, ETH-BNB, existe o risco de que esses ativos se desvinculem de preço. A BNB pode cair consideravelmente em relação à ETH. Você perderia alguns fundos como resultado, em comparação a apenas deter ETH e BNB por conta própria. Os ativos neste cofre têm alguns riscos de perda impermanente.&#x20;
* Critérios de qualificação: Cofres que lidam com o que normalmente são chamadas de LPs como “Pool 1” se encaixam aqui: ETH-USDC, MATIC-AAVE, etc. As moedas de governança para projetos menores são normalmente conhecidas como “Pool 2” e, portanto, excluídas.

#### ALTA IL

* Título: IL projetada alta&#x20;
* Explicação:  Quando você está fornecendo liquidez em um par de moedas, por exemplo, ETH-BNB, existe o risco de que esses ativos se desvinculem de preço. A BNB pode cair consideravelmente em relação à ETH. Você perderia alguns fundos como resultado, em comparação a apenas deter ETH e BNB por conta própria. Os ativos neste cofre têm riscos de perda impermanente altos ou muito altos.&#x20;
* Critérios de qualificação: Cofres que lidam com LPs “Pool 2” vão aqui. Essas LPs normalmente incluem a moeda de governança da própria pool incentivada.

#### ESTÁVEL ALGORÍTMICA

* Título: Estável algorítmica, lastro experimental
* Explicação: Quando você está fornecendo liquidez em um par de moedas, por exemplo, ETH-BNB, existe o risco de que esses ativos se desvinculem de preço. A BNB pode cair consideravelmente em relação à ETH. Você perderia alguns fundos como resultado, em comparação a apenas deter ETH e BNB por conta própria. Pelo menos uma das moedas contidas nesse cofre é uma moeda estável algorítmica. Isso significa que o lastro estável é experimental e altamente arriscado. Use-a com cuidado a seu próprio critério.&#x20;
* Critérios de Qualificação: “Moedas estáveis” com lastros experimentais, ou _tokenomics_ que falharam repetidamente em manter seu lastro no passado.

### Subcategoria: Liquidez

Acompanha o quão difícil é comprar/vender a(s) moeda(s) do cofre.

#### LIQUIDEZ ALTA

* Título: Alta liquidez de troca
* Explicação: A liquidez de um ativo afeta o risco de tê-lo. Os ativos líquidos são negociados em muitos lugares e com bom volume. O ativo detido por este cofre tem alta liquidez. Isso significa que você pode trocar seus ganhos facilmente em muitos lugares.&#x20;
* Critérios de Qualificação: -

#### LIQUIDEZ BAIXA

* Título: Baixa liquidez comercial&#x20;
* Explicação: A liquidez de um ativo afeta o risco de tê-lo. Os ativos líquidos são negociados em muitos lugares e com bom volume. O ativo usado neste cofre tem baixa liquidez. Isso significa que não é tão fácil trocar e você pode incorrer em alto 'deslize' ao fazer a troca.&#x20;
* Critérios de Qualificação: -

### Subcategoria: Capitalização de Mercado (Market Cap)

Valor total de todas as moedas em circulação. Indiretamente acompanha o quão volátil é o ativo subjacente do cofre.

#### ALTA CAPITALIZAÇÃO DE MERCADO

* Título: Alta capitalização de mercado, ativo de baixa volatilidade&#x20;
* Explicação: A capitalização de mercado de criptoativos afeta diretamente o risco de tê-lo. Normalmente, uma capitalização de mercado baixa implica alta volatilidade e baixa liquidez. O ativo usado neste cofre tem uma grande capitalização de mercado. Isso significa que é potencialmente um ativo altamente seguro de se ter. O ativo tem um alto potencial de permanecer no mercado e crescer ao longo do tempo.&#x20;
* Critérios de qualificação: Ranking Top 50 Capitalização de Mercado na CoinGecko/CoinMarketCap

#### CAPITALIZAÇÃO DE MERCADO MÉDIA

* Title: Capitalização de mercado média, ativo de volatilidade média&#x20;
* Explicação: A capitalização de mercado de criptoativos afeta diretamente o risco de tê-lo. Normalmente, uma capitalização de mercado baixa implica alta volatilidade e baixa liquidez. O ativo usado neste cofre tem uma capitalização de mercado média. Isso significa que é potencialmente um ativo seguro de se ter. O ativo tem potencial de permanecer no mercado  e crescer ao longo do tempo.&#x20;
* Critérios de Qualificação: Ranking de Capitalização de Mercado entre 50 e 300 na CoinGecko/CoinMarketCap

#### CAPITALIZAÇÃO DE MERCADO PEQUENA

* Título: Pequena capitalização de mercado, ativo de alta volatilidade&#x20;
* Explicação: A capitalização de mercado de criptoativos afeta diretamente o risco de tê-lo. Normalmente, uma capitalização de mercado baixa implica alta volatilidade e baixa liquidez. O ativo usado neste cofre tem uma pequena capitalização de mercado. Isso significa que é potencialmente um ativo arriscado de se ter. O ativo tem baixo potencial de permanecer no mercado e crescer ao longo do tempo.&#x20;
* Critérios de Qualificação: Ranking de Capitalização de Mercado entre 300 e 500 na CoinGecko/CoinMarketCap

#### CAPITALIZAÇÃO DE MERCADO MICRO

* Título: Micro capitalização de mercado, ativo de extrema volatilidade&#x20;
* Explicação: A capitalização de mercado de criptoativos afeta diretamente o risco de tê-lo. Normalmente, uma capitalização de mercado baixa implica alta volatilidade e baixa liquidez. O ativo usado neste cofre tem uma micro capitalização de mercado. Isso significa que é potencialmente um ativo altamente arriscado de se ter. O ativo tem baixo potencial de permanecer no mercado.&#x20;
* Critérios de Qualificação: Ranking de Capitalização de Mercado acima de 500 na CoinGecko/CoinMarketCap

### Subcategoria: Fornecimento

Acompanha riscos relacionados ao fornecimento do ativo. Pode ser alterado por qualquer pessoa? Quão centralizado é?

#### FORNECIMENTO CENTRALIZADO

* Título: Poucas baleias muito poderosas&#x20;
* Explicação: Quando a oferta está concentrada em poucas mãos, elas podem afetar bastante o preço ao vender. As baleias podem manipular o preço da moeda. Quanto mais pessoas tiverem investidas em uma moeda, melhor e mais orgânica será a ação do preço.&#x20;
* Critérios de Qualificação: Menos de 50 contas detêm mais de 50% da oferta.

## Categoria: Riscos da Platforma

Riscos relacionados às plataformas de terceiros usadas pelo cofre. Qual histórico eles têm, quão sólido é o código, se há alguma ação perigosa que um administrador pode tomar, etc. Sessenta por cento da pontuação é determinada por esta categoria.

### Subcategoria: Reputação

Tenta dar pistas sobre o histórico da equipe e da comunidade. Qual a probabilidade de eles puxarem o tapete, por exemplo.

#### PLATAFORMA ESTABELECIDA

* Título: A plataforma tem um histórico conhecido&#x20;
* Explicação: Ao participar de uma pool incentivada, pode ser útil saber há quanto tempo a plataforma existe e o grau de sua reputação. Quanto maior o histórico, mais investimento a equipe e a comunidade têm por trás de um projeto. Este cofre investe na plataforma de um projeto que existe há muitos meses.&#x20;
* Critérios de Qualificação: A plataforma subjacente existe há pelo menos 3 meses.

#### PLATFORMA NOVA

* Título: A plataforma é nova e com pouco histórico&#x20;
* Explicação: Ao participar de uma pool incentivada, pode ser útil saber há quanto tempo a plataforma existe e o grau de sua reputação. Quanto maior o histórico, mais investimento a equipe e a comunidade têm por trás de um projeto. Este cofre investe na plataforma de um projeto novo, com poucos meses em funcionamento.&#x20;
* Critérios de Qualificação: A plataforma subjacente existe há menos de 3 meses.

### Subcategoria: Segurança

Acompanha várias boas práticas de contratos inteligentes.

#### SEM AUDITORIA

* Título: A plataforma nunca foi auditada por auditores terceiros confiáveis&#x20;
* Explicação: As auditorias são revisões de código por um grupo de desenvolvedores terceiros.&#x20;
* Critérios de Qualificação: -

#### AUDITADO

* Título: A plataforma tem uma auditoria de pelo menos um auditor confiável&#x20;
* Explicação: As auditorias são revisões de código por um grupo de desenvolvedores terceiros.&#x20;
* Critérios de Qualificação: Uma ou mais auditorias de um auditor que tenha histórico positivo no espaço.

#### CONTRATOS VERIFICADOS

* Título: Todos os contratos relevantes são verificados publicamente&#x20;
* Explicação: O código em execução em um contrato específico não é público por padrão. Os exploradores de blocos (_block explorers_) permitem que os desenvolvedores verifiquem o código por trás de um contrato específico. Essa é uma boa prática porque permite que outros desenvolvedores auditem se o código faz o que deveria. Todos os contratos de terceiros que este cofre usa são verificados. Isso o torna menos arriscado.&#x20;
* Critérios de Qualificação: -

#### CONTRATOS NÃO VERIFICADOS

* Título: Alguns contratos não são verificados&#x20;
* Explicação: O código em execução em um contrato específico não é público por padrão. Os exploradores de blocos (_block explorers_) permitem que os desenvolvedores verifiquem o código por trás de um contrato específico. Essa é uma boa prática porque permite que outros desenvolvedores auditem se o código faz o que deveria. Alguns dos contratos de terceiros que este cofre usa não são verificados. Isso significa que há certas coisas que os desenvolvedores da Beefy não foram capazes de inspecionar.&#x20;
* Critérios de Qualificação: -

#### FUNÇÕES ADMINISTRATIVAS COM TRANCAS DE TEMPO

* Título: Funções perigosas estão por trás de uma tranca de tempo&#x20;
* Explicação: Às vezes, o proprietário do contrato ou administrador pode executar determinadas funções que podem colocar os fundos dos usuários em risco. A melhor coisa é evitá-las completamente. Se elas devem estar presentes, é importante mantê-las por trás de uma tranca de tempo para dar o aviso adequado antes de usá-las. Este contrato tem certas funções administrativas perigosas, mas pelo menos estão por trás de uma tranca de tempo significativa.&#x20;
* Critérios de Qualificação: Há pelo menos uma função presente que pode tomar parcial ou completamente os fundos dos usuários. A função deve estar atrás de uma tranca de tempo de +6h.

#### FUNÇÕES ADMINISTRATIVAS SEM TRANCAS DE TEMPO

* Título: Funções perigosas sem trancas de tempo
* Explicação: Às vezes, o proprietário do contrato ou administrador pode executar determinadas funções que podem colocar os fundos dos usuários em risco. A melhor coisa é evitá-las completamente. Se elas devem estar presentes, é importante mantê-las por trás de uma tranca de tempo para dar o aviso adequado antes de usá-las. Este contrato tem certas funções administrativas perigosas e não há trancas de tempo presentes. Elas podem ser executadas a qualquer momento.&#x20;
* Critérios de Qualificação: Há pelo menos uma função presente que pode tomar parcial ou completamente os fundos dos usuários. A função não possui proteção de tranca de tempo.

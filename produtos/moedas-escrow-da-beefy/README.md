---
description: Tradução feita a partir da atualização de Outubro de 2022
---

# Moedas Escrow da Beefy

## O que é _Escrow_?

Um mecanismo _Escrow_ é como uma garantia, uma parte detém os direitos ou bens de outra parte em custódia por eles, enquanto aguarda o cumprimento de uma condição específica (por exemplo, o recebimento seguro de bens adquiridos com esses bens). Na DeFi, os mecanismos de _Escrow_ envolvem o fornecimento de suas moedas a terceiros (por exemplo, a Beefy) para que eles possam implementar alguma funcionalidade com essas moedas em seu nome. Como tal, todos os mecanismos de _Escrow_ são normalmente construídos em torno de algum design econômico ("tokenômico") das moedas que você possui.

Por exemplo, a moeda nativa de uma blockchain (por exemplo, a FTM da Fantom) pode ser depositadas em validadores para assegurar uma blockchain, validando suas transações de forma justa e segura. O design tokenômico permite aos usuários depositar suas moedas a fim de ganhar taxas de transação dos usuários da blockchain, dando à moeda nativa a capacidade de ganhar ou gerar valor para o titular. No entanto, o depósito é complicado e tem contrapontos, como trancar suas moedas e limitar sua capacidade de negociar com elas. Portanto, soluções de _escrow_ de terceiros (por exemplo, a beFTM da Beefy) foram criadas para permitir que você tenha acesso aos benefícios da tokenomics (ou seja, depositar a sua FTM) sem ter que gerenciar o depósito você mesmo, e ao mesmo tempo permitindo que você troque suas moedas trancadas e seus rendimentos.

## O que é _Escrow_ de voto?

Um mecanismo de _Escrow_ de voto é uma forma de design tokenômico de _Escrow_ cujo objetivo é recompensar detentores de long prazo de uma moeda de governança de um protocolo com maior poder de voto, para favorecer os seus interesses em termos de governança sobre os detentores de curto prazo. Isso é alcançado com detentores depositando suas moedas e tipicamente trancando-as com o protocolo (tipicamente em troca de uma parte da receita do protocolo), assim limitando sua capacidade de negociar essas moedas. Fazendo isso, o usuário ou destrava seu poder de voto (que não são disponibilizados para meros detentores) ou impulsiona seu poder de voto já existente, normalmente proporcional à quantidade de tempo pelas quais são trancadas/depositadas. Este poder de voto é frequentemente usado para direcionar a economia do referido protocolo, fazendo com que os usuários votem sobre como distribuir moedas recém cunhadas como incentivos adicionais entre as pools de liquidez do protocolo.

O pioneiro do sistema de voto _Escrow_ na DeFi foi a Curve Finance com o design das moedas CRV e veCRV (presente na Ethereum). Outros exemplos notáveis de designs _Escrow_ incluem veCVX da Convex (Ethereum), veBAL da Balancer (Ethereum), veFXS da Frax (Ethereum), eQI da Mai Finance (Polygon), veJOE da Trader Joe (Avalanche), vePTP da Platypus (Avalanche), veVELO da Velodrome (Optimism).

## O que são Moedas _Escrowed_ de Voto (veTokens)?

Na maioria dos sistemas de voto _Escrow,_ o poder de voto do usuário não está linearmente relacionadas à quantidade de moedas de governança em mãos, dependendo no entanto de fatores como o tempo pelos quais essas moedas são trancadas. Sob essa luz, o conceito de moedas _Escrowed_ de voto (_"veTokens"_) foi concebido, para refletir a quantidade de poder de voto que um usuário tem a partir de suas moedas trancadas/depositadas. Na medida em que os fatores que impactam o poder de voto mudam, a quantidade de _veTokens_ também vai mudar, mesmo se a quantidade de moedas trancadas/depositadas continuar a mesma.

Um ponto de confusão é que - apesar do nome - _veTokens_ não são sempre representadas por uma moeda ERC20, então não são necessariamente recebidas e guardadas pelos usuários em suas carteiras. Isso porque a economia das _veTokens_ (_veTokenomics_) são desenhadas para permitir que o poder de voto mude constantemente na medida em que os fatores condicionais (por exemplo, o tempo restante de trancamento) mudam. Se as _veTokens_ fossem emitidas aos seus usuários, isso requereria constantes reajustes do fornecimento total e das respectivas quantidades possuídas por todos os usuários, o que acrescentaria uma complexidade e custo adicional considerável. Ademais, como as _veTokenomics_ foram desenhadas para incentivar a posse a longo prazo de moedas de governança, implementar poder de voto em uma moeda formato ERC20 transferível comprometeria este objetivo, pois isso permitiria que detentores de longo prazo negociassem seus interesses da mesma forma que detentores de curto prazo.

<details>

<summary>Exemplo de veTokenomics</summary>

Imagine que um eleitor possui 1 moeda EXMPL, emitida pela Exemplo DAO e que lhe dá direito a 1 voto inteiro no processo de governança existente da Exemplo DAO.

A Exemplo DAO então implementa um design de _escrow_ de voto, onde o eleitor pode depositar e trancar suas moedas por qualquer período de tempo até 2 anos, e receberá um aumento de poder de voto igual ao número de anos restantes na tranca.

Em circunstâncias normais, a moeda 1 EXMPL do eleitor lhe daria direito ao poder de voto equivalente a 1 veEXMPL estático, ou 1 voto inteiro no processo de governança.

O eleitor poderia então optar por trancar sua 1 EXMPL por 2 anos, e receberia 3 veEXMPL (1 base + 2 bônus), o que equivale a 3 votos inteiros.

Após um ano de votação impulsionada, o período restante da tranca do usuário teria diminuído para 1 ano, consequentemente reduzindo seu bônus e veEXMPL, de modo que eles tenham direito a 2 votos. O usuário pode decidir, a qualquer momento, estender sua tranca de volta para 2 anos para aumentar seu veEXMPL, ou pode decidir que quer sair da tranca esperando mais um ano, e depois vender suas moedas.

</details>

## O que são Moedas _Escrowed_ da Beefy(_beTokens_)?

Moedas _Escrowed_ da Beefy("_beTokens"_) são moedas de invólucro, desenvolvidas e implementadas pela Beefy para destravar os benefícios das _veTokenomics_ ao mesmo tempo que permitindo usuários fazer trocas na moeda de governança do projeto parceiro. Efetivamente, nós lançamos um contrato inteligente interino que pode guardar moedas de governança do projeto parceiro, trancá-las no protocolo do projeto parceiro pelo máximo de tempo possível e ganhar acesso aos benefícios do modelo _Escrow_. Adicionalmente, nós acrescentamos valor extra ao combinar esses aspectos à emissão de uma nova moeda _beToken_ ERC20 a qual você pode então trocar para sair da tranca a qualquer momento.

Cada _beToken_ é desenvolvida unicamente de acordo com o modelo _veTokenomics_ do protocolo de nossos parceiros, então elas vêm com um grande raio de características diferentes. Essas podem incluir: suporte para liquidez em corretoras descentralizadas (DEXes); lastro flutuante de acordo com o mercado; um processo de votação da Beefy para alocação de votos no protocolo subjacente; compra de votos pela Beefy ou por usuários e; impulsos a cofres associados da Beefy.

Nós da Beefy sempre provêmos cofres para nossas _beTokens_ na nossa plataforma, onde você pode depositá-las para ganhar um retorno. Isso pode ser na forma de um Cofre de Auto-reinvestimento _beToken_ (ganhando mais _beTokens_) ou uma Pool de Ganhos (ganhando retorno na respectiva moeda de governança). Em qualquer caso, você está livre para retirar suas moedas do depósito a qualquer momento, trocar a sua _beToken_ e sair da posição.

## Quais _beTokens_ já existem?

Nesta seção, fornecemos uma página cobrindo cada uma das diferentes _beTokens_ que operamos atualmente. No momento em que escrevemos, estes incluem:

{% content-ref url="beftm.md" %}
[beftm.md](beftm.md)
{% endcontent-ref %}

{% content-ref url="binspirit.md" %}
[binspirit.md](binspirit.md)
{% endcontent-ref %}

{% content-ref url="bejoe.md" %}
[bejoe.md](bejoe.md)
{% endcontent-ref %}

{% content-ref url="beqi.md" %}
[beqi.md](beqi.md)
{% endcontent-ref %}

{% content-ref url="bevelo.md" %}
[bevelo.md](bevelo.md)
{% endcontent-ref %}

{% content-ref url="beopx.md" %}
[beopx.md](beopx.md)
{% endcontent-ref %}

## Onde posso saber mais sobre?

Esta seção fornece detalhes completos sobre os projetos de cada uma de nossas _beTokens_ existentes. Você também pode levantar quaisquer questões específicas sobre nossas _beTokens_, entrando em contato conosco no servidor da [Beefy Discord](https://discord.gg/yq8wfHd).

---
description: Tradução feita a partir da atualização de março de 2023
---

# Tesouraria

No coração das operações da Beefy está nossa Tesouraria, que é administrada por nossa equipe de colaboradores principais. Como nossa moeda de $BIFI é totalmente distribuída, sem nenhuma moeda reservada para uso posterior, toda nossa operação é financiada por nossas atividades geradoras de receita em andamento. Para manter as luzes acesas e nossos cofres de auto-reinvestimento, a Beefy conta com a vigilância constante de sua equipe de tesouraria para administrar o uso de nossa Tesouraria de forma responsável e com os melhores interesses da DAO no coração.

Esta página explica a história e a estrutura da Tesouraria Beefy, resume nossa abordagem à gestão da tesouraria e fornece os detalhes necessários para acessar nossas atividades de tesouraria em andamento.

## História

O produto principal da Beefy - nossos Cofres Beefy - são projetados desde o início para gerar taxas para o projeto (ver [beefy-finance-fees-breakdown.md](../ecosystem/beefy-bulletins/beefy-finance-fees-breakdown.md "mention") ) para sustentar nossas atividades. Como tal, sempre fomos um projeto gerador de receita e sempre tivemos algum nível de entrada e saída de tesouraria.

Com o tempo, nossas atividades de tesouraria têm se tornado cada vez mais sofisticadas. Inicialmente, os fundadores do projeto gerenciaram privadamente os fluxos de entrada do contrato inteligente para cobrir seus custos na operação e manutenção do protocolo. O [contrato original da BeefyTreasury](https://bscscan.com/address/0x4a32de8c248533c28904b24b4cfcfe18e9f2ad01#code) foi [lançado](https://bscscan.com/tx/0xccc2a94cde6aa10e3928a837b17cb7705f8ec3104afb66842627cc9cdaf4621c) em 6 de novembro de 2020. O contrato do Tesouro era muito básico em funcionalidade, permitindo que a moeda nativa da rede e as moedas ERC-20/BEP-20 fossem retiradas pelo proprietário, que era o [EOA da BeefyDeployer](https://bscscan.com/address/0x565eb5e5b21f97ae9200d121e77d2760fff106cb).

Em março de 2021, a Beefy tinha se expandido para incluir mais colaboradores, e assim a equipe principal de colaboradores criou o canal #💵-treasury no [Discord da Beefy](https://discord.gg/yq8wfHd) como um local de discussão de todas as questões relacionadas à tesouraria. Nos meses seguintes, a Beefy se tornou cada vez mais multi-rede, e contratos adicionais da BeefyTreasury foram implantados na [Avalanche](https://snowtrace.io/address/0xa3e3af161943cfb3941b631676134bb048739727#code), [Polygon](https://polygonscan.com/address/0x09ef0e7b555599a9f810789fff68db8dbf4c51a0#code), [Fantom](https://ftmscan.com/address/0xe6cce165aa3e52b2cc55f17b1dbc6a8fe5d66610#code) junto com algumas outras cadeias iniciais. Entretanto, a equipe principal reconheceu a limitação do projeto inicial do Tesouro, e foi debatida uma mudança nas carteiras MultiSig, apesar das soluções MultiSig não estarem disponíveis em todas as redes.

Em setembro de 2021, a DAO tinha se decidido em mudar para as carteiras MultiSig na BSC e Polygon (como as duas redes com soluções MultiSig disponíveis na época), e estabelecer o Conselho do Tesouro como os signatários da MultiSig. Em 3 de setembro de 2021, foi concluída uma votação suave sobre a Discord para nomear os novos membros do Conselho do Tesouro. Isto foi seguido por uma [Proposta na Snapshot](https://vote-archive.beefy.finance/#/beefy/proposal/QmafULDojJ4StzJtuwjBZutnUkzb9TUhTLCLZe5R7deWLo), que confirmou os 7 membros iniciais. Em 11 de setembro, a propriedade do contrato original da BeefyTreasury sobre a BSC foi [transferida ](https://bscscan.com/tx/0x34a89b3cd5564fbd22672169b9cce43a538cf764cb73e1a28fe4db89241ae7ad)para a nova MultiSig. Desde então, o sistema MultiSig e o Conselho do Tesouro continuaram e se expandiram para cada uma das novas redes da Beefy.

Também em setembro de 2021, a equipe central da Beefy começou a implementar bots no canal #💵-treasury, exibindo inicialmente o valor do Tesouro em benefício dos membros da DAO. Em outubro de 2022, isto havia evoluído para incluir cada nova transação ao vivo quando afixada a partir de qualquer uma das carteiras multisig do Tesouro. Alguns dos principais comandos do bot são:

* **Mostrar Tesouro Completo:** `@Bitch I'm a Cow#9189 treasury`
* **Mostrar a Tesouraria Total em ums Rede Específica:** `@Bitch I'm a Cow#9189 treasury {blockchain}`
* **Mostrar os saldos atuais do Cowllector:**`@Bitch I'm a Cow#9189 cowllector balances`

## Conselho do Tesouro

Como descrito acima, o Conselho do Tesouro foi formado em setembro de 2021 como a equipe que deveria conduzir e administrar todas as transações do Tesouro e atividades relacionadas para a administração da Tesouraria. O papel do Conselho do Tesouro tem se expandido gradualmente, para incluir agora:

* Orquestrar, assinar e executar todas as transações da Tesouraria (ou seja, pagamentos usando bens da Tesouraria);
* Administração dos ativos da Tesouraria, tais como a criação e saída de liquidez de propriedade do protocolo e a realização de concessões, recompensas pendentes e outros ativos externos;
* Monitorar e fornecer capital operacional (por exemplo, gás) para a infra-estrutura da Beefy, incluindo nosso Cowllector, Fee Batch Harvester e EOAs de contribuintes;
* Providenciar o pagamento das principais despesas, incluindo salários dos contribuintes, patrocínios, taxas recorrentes de hospedagem e serviços e reembolso das despesas dos contribuintes e;
* Manipulação de pagamentos regulares de suborno para corretoras parceiras.

O Conselho do Tesouro sempre tem 7 membros, e requer consenso de qualquer 4 para assinar qualquer transação MultiSig antes de poder ser executada. Os detalhes dos atuais 7 membros e suas carteiras EOA do Tesouro são:

* **AllTrades:** 0xa75209dC118dF7B6541db5b7Be0DE9485Ebaa907
* **DefiDebauchery:** 0x037465bF6a4A8D7F552AE18046478C6A727178F3
* **Mjoaris:** 0xBFEB0756f09f73A19CE62FBa6a8Db4e922E73A14
* **Pablo:** 0xDB583b636f995eF1EF28ac96B9bA235916bd1583
* **Power:** 0x6fCE222540015290FB572C82622dc73a431CdF3F
* **TBC:** 0x428b2F01Bfb0917FE6FF463f37B0c47F1782B9Cd
* **YR2150:** 0xF24f555d6765D559BFF4C5557dD9024CBA10d30e

Qualquer pergunta para o Conselho do Tesouro deve ser direcionada ao canal #💵-treasury no [Discord da Beefy](https://discord.gg/yq8wfHd). Para fins de segurança, por favor, não envie mensagens diretamente aos membros do Conselho, ou suas mensagens serão ignoradas e potencialmente bloqueadas ou comunicadas.

## Infraestrutura da Tesouraria

O Tesouro da Beefy depende de alguns componentes básicos de infra-estrutura para facilitar as entradas e saídas seguras de fundos do Tesouro. Os elementos centrais são:

* **MultiSig do Tesouro** - carteiras com várias assinaturas controladas pelo Conselho do Tesouro, usadas para segurar todos os principais ativos do Tesouro com segurança e de uma maneira que não pode ser explorada por nenhum indivíduo;
* **Carteiras de Contribuintes do Tesouro** - contas externamente controladas (**EOAs**) por diferentes contribuintes da Beefy, tais como nossos membros do Conselho do Tesouro e outros contribuintes-chave da DAO. Ao usar as EOAs para interagir com protocolos e contratos externos, isolamos o risco de hacks ou explorações com impacto sobre a Tesouraria da Beefy, isolando-a dos externos e dando nenhuma ou muito limitada aprovação externa;
* **Cowllector** - o Beefy Cowllector é um bot criado e mantido pela equipe principal da Beefy que procura coletar regularmente cofres Beefy onde quer que uma oportunidade lucrativa se apresente. Como o chamador da coleta exige uma pequena taxa como proporção da coleta, o Cowllector analisa o tamanho da recompensa potencial versus o custo da coleta e faz chamadas automáticas quando apropriado e;
* **Fee Batcher** - o Beefy Fee Batcher é outro bot criado e mantido pela equipe principal da Beefy que agrega as taxas da Beefy das colheitas em um único local, para poder trocar eficientemente lotes agregados de taxas na moeda principal da rede, antes de enviar a saída das taxas em um único lote limpo para a tesouraria da Beefy.

As MultiSigs do Tesouro podem ser encontradas nos seguintes endereços para as seguintes redes:

* Arbitrum: [0x3f5eddad52C665A4AA011cd11A21E1d5107d7862](https://gnosis-safe.io/app/arb1:0x3f5eddad52C665A4AA011cd11A21E1d5107d7862/balances)
* Aurora: [0x088C70Ddff3a3774825dd5e5EaDB356404248d83](https://app.safe.global/home?safe=aurora:0x088C70Ddff3a3774825dd5e5EaDB356404248d83)
* Avalanche: [0x26dE4EBffBE8d3d632A292c972E3594eFc2eCeEd](https://gnosis-safe.io/app/avax:0x26dE4EBffBE8d3d632A292c972E3594eFc2eCeEd/balances)
* BSC: [0x7C780b8A63eE9B7d0F985E8a922Be38a1F7B2141](https://gnosis-safe.io/app/bnb:0x7C780b8A63eE9B7d0F985E8a922Be38a1F7B2141/balances)
* Canto: [0xF09d213EE8a8B159C884b276b86E08E26B3bfF75](https://safe.neobase.one/canto:0xF09d213EE8a8B159C884b276b86E08E26B3bfF75/home)
* Celo: [0xca807d809f9639cefb3d31a7951cec3ab405a2fd](https://www.xdao.app/42220/dao/0xCA807D809f9639CEfb3d31a7951Cec3ab405a2fd)
* Cronos: [0xa9721Ae5042482D7a884A2138f580459B680920f](https://cronos-safe.org/cro:0xa9721Ae5042482D7a884A2138f580459B680920f/home)
* Ethereum: [0xc9C61194682a3A5f56BF9Cd5B59EE63028aB6041](https://gnosis-safe.io/app/eth:0xc9C61194682a3A5f56BF9Cd5B59EE63028aB6041/home)
* Emerald: [0x8fd0869271d26e6653f5d5650685630f75b6aedf](https://www.xdao.app/42262/dao/0x8FD0869271d26E6653f5d5650685630F75b6AEDf)
* Fantom: [0xdFf234670038dEfB2115Cf103F86dA5fB7CfD2D2](https://safe.fantom.network/#/safes/0xdFf234670038dEfB2115Cf103F86dA5fB7CfD2D2/balances)[  ](https://safe.fantom.network/#/safes/0xdFf234670038dEfB2115Cf103F86dA5fB7CfD2D2/balances)
* Fuse: [0x1C124c2CaB83b3C3B5D0f0899CeeA5e06964599F](https://gnosis-safe.fuse.io/fuse:0x1C124c2CaB83b3C3B5D0f0899CeeA5e06964599F/balances)
* Harmony: [0x523154a03180FD1CB26F39087441c9F91BcD0389](https://multisig.harmony.one/#/safes/0x523154a03180FD1CB26F39087441c9F91BcD0389/balances)
* HECO : [0xdbb72c8b7ebdd52a4813b9d262386dfdab69c9ba](https://www.xdao.app/128/dao/0xdbB72c8B7eBdD52A4813B9D262386dfDAB69c9bA)
* Kava: [0x07F29FE11FbC17876D9376E3CD6F2112e81feA6F](https://app.oryy.io/kava:0x07F29FE11FbC17876D9376E3CD6F2112e81feA6F/home)
* Metis: [0x0f9602B7E7146a9BaE16dB948281BebDb7C2D095](https://metissafe.tech/metis-andromeda:0x0f9602B7E7146a9BaE16dB948281BebDb7C2D095/balances)
* Moonbeam: [0x3E7F60B442CEAE0FE5e48e07EB85Cfb1Ed60e81A](https://multisig.moonbeam.network/mbeam:0x3E7F60B442CEAE0FE5e48e07EB85Cfb1Ed60e81A/home)
* Moonriver: [0x617f12E04097F16e73934e84f35175a1B8196551](https://multisig.moonbeam.network/mriver:0x617f12E04097F16e73934e84f35175a1B8196551/balances)
* Optimism: [0x4ABa01FB8E1f6BFE80c56Deb367f19F35Df0f4aE](https://gnosis-safe.io/app/oeth:0x4ABa01FB8E1f6BFE80c56Deb367f19F35Df0f4aE/home)
* Polygon: [0xe37dD9A535c1D3c9fC33e3295B7e08bD1C42218D](https://gnosis-safe.io/app/matic:0xe37dD9A535c1D3c9fC33e3295B7e08bD1C42218D/balances)

## Gestão de Tesouraria

A administração da Tesouraria da Beefy também evoluiu ao longo do tempo, para refletir as mudanças das necessidades do protocolo e da DAO. Operar em tantas redes, cada uma com seus próprios conjuntos de cofres, infra-estrutura e carteiras MultiSig torna um processo complicado para gerenciar ativamente a Tesouraria. Em vez disso, vários princípios abrangentes surgiram para orientar as melhores práticas atuais.

Antes de tudo, a equipe de colaboradores da Beefy optou por operar o Tesouro em cada grande rede principalmente em moedas estáveis, para mitigar o risco negativo de manter ativos voláteis. Isto permite que Beefy tome decisões claras e deliberadas sobre como utilizar seus fundos, livres dos riscos das condições atuais do mercado. Como tal, o Fee Batcher em cada rede principal troca todas as taxas de cofre da Beefy por uma moeda designada para essa rede, conforme detalhado em [#moedas-de-entrada](tesouraria.md#moedas-de-entrada "mention") abaixo.

Em segundo lugar, foi decidido que investir uma parte dos ativos da tesouraria em Cofres Beefy para gerar renda passiva seria uma utilização sensata e inteligente dos fundos. De modo geral, apenas uma pequena parte do Tesouro de nossas redes principais é investida em Cofres Beefy, e eles são sempre alocados em cofres só de moeda estável. Embora os rendimentos dos fundos investidos sejam geralmente relativamente pequenos, este mecanismo ajuda a mitigar a natureza inflacionária dos valores de moedas estáveis.

Finalmente, para facilitar a liquidez de nossas moedas através das diferentes cadeias, Beefy também investe e mantém posições de liquidez em nossas moedas, incluindo tanto nossa [bifi-token](../ecosystem/bifi-token/ "mention"), quanto nossas [moedas-escrow-da-beefy](../produtos/moedas-escrow-da-beefy/ "mention"). Nossa moeda $BIFI é tipicamente pareada com moedas nativas ou de gás na rede relevante, para fornecer a rota mais fácil para a moeda para os recém-chegados à rede. Uma vez que o contrato de moedas $BIFI é implantado em uma nova rede, o contrato é conectado à Beefy _Bridge_ e a nossos parceiros da Multichain, de modo que mais $BIFI possam ser tranferidas à rede e para que uma LP inicial possa ser criada.

Detalhes resumidos ao vivo do estado atual do Tesouro Beefy, incluindo todas as moedas líquidas, depositadas/investidas e bloqueadas e posições de liquidez, estão disponíveis na página do [Painel do Tesouro](https://app.beefy.finance/treasury) do aplicativo da Beefy.

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption><p>O Painel do Tesouro Beefy foi introduzido em janeiro de 2023 para fornecer informações resumidas e imediatas sobre o estado atual do Tesouro da Beefy.</p></figcaption></figure>

## Moedas de Entrada

Como descrito acima em [#gestao-de-tesouraria](tesouraria.md#gestao-de-tesouraria "mention"), a entrada de dinheiro em nossas principais blockchains é convertida em moedas estáveis para fins de gestão de tesouraria, com o Fee Batcher de cada rede adotando uma moeda estável chave para suas operações. As seguintes redes têm as seguintes moedas designadas:

* Arbitrum: USDC
* Avalanche: USDT
* BSC: BUSD
* Canto: USDC
* Cronos: USDC
* Ethereum: USDC
* Ethereum Validator: ETH (retida no validador)
* Fantom: USDC
* Fantom Validator: WBTC (gradualmente tranferida para a Ethereum)
* Fuse: BUSD
* Fuse Validator: Fuse (retida no validador)
* Kava: USDC
* Metis: USDC
* Moonbeam: MAI
* Moonriver: USDC
* Optimism: USDC
* Polygon: USDC

Volumes e liquidez na Aurora, Celo, Emerald, Harmony e HECO são todos atualmente muito pequenos para garantir o gerenciamento estável de moedas, de modo que os influxos de taxas de cofre são tipicamente trocados para a moeda nativa relevante da rede.

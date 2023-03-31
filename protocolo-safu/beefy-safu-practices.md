---
description: '"Não Confie, Verifique"'
---

# Práticas SAFU

Na Beefy, reconhecemos três palavras para seguir vivendo: _SAFU Primeiro. Sempre._ Você pode criar as características mais incríveis em seus contratos inteligentes, mas se você não puder salvaguardar adequadamente os fundos dos usuários, seus contratos não merecem ter usuários. É por isso que a segurança é a primeira, última e principal consideração em cada produto que lançamos.

Esta página descreve as várias práticas que os colaboradores da Beefy tomam para garantir que todos os novos produtos sejam seguros antes do lançamento, que todos os produtos em andamento sejam devidamente mantidos e observados, e que nossa resposta a quaisquer preocupações de segurança sejam rápidas e seguras.

\[IMAGE TRANSLATION: All projects have to pass a stringent set of security rules = Todos os projetos precisam passar por um conjunto rigoroso de regras de segurança\
Verified Contracts = Contratos Verificados\
Token Liquidity = Liquidez da Moeda\
Backdoor Functions = Funções _Backdoor_\
Emission Rate = Velocidade de Emissão\
Whale Holders = Detentores 'Baleias'\
Proxy & Timelocks leave as is\
Pass = Passou\
Security = Segurança]

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption><p>A Beefy adotou uma abordagem de gestão SAFU rigorosa, que monitora uma série de fatores de segurança como pré-requisitos para todos os nossos produtos.</p></figcaption></figure>

## **Novas **_**farms**_** na Beefy**

Antes que uma nova estratégia de farm seja usada na Beefy, o projeto precisa passar por um conjunto rigoroso de regras SAFU:

* Os contratos foram verificados no _block explorer_;
* Moedas não-nativas precisam ser de pontes multi-rede respeitadas;
* Liquidez suficiente para trocar moedas recompensas de pools incentivadas;
* As funções de migração estão completamente removidas ou trancadas por tempo suficiente;
* As taxas de emissão das moedas de incentivo(_farm_) precisam estar trancadas por tempo (se pares dessa moeda estiverem sendo usados em cofres);
* Detentores das moedas de incentivo com >5% do fornecimento em circulação não são endereços de contas externas ou de contas multi-assinatura;
* Todas as mudanças de implementação de proxy devem ser trancadas por tempo (_timelock_).

## Novos cofres na Beefy

Nossos estrategistas seguem um procedimento de teste manual em cada novo cofre antes de ser lançado. Isso é para garantir que o cofre funcione como pretendido e os fundos do usuário estejam sempre SAFU.

1. É depositado uma pequena quantia do ativo;&#x20;
2. Retira-se tudo;&#x20;
3. Deposita-se novamente, espera-se 1 minuto e verifica-se se `callReward()` não é 0;&#x20;
4. Coleta-se a estratégia;&#x20;
5. Coloca-se a estratégia em pânico;&#x20;
6. Retira-se 50% enquanto estiver em pânico para garantir que os usuários possam sair;&#x20;
7. Tenta-se depositar, um erro deve aparecer, mas não se envia o depósito;&#x20;
8. Retoma-se a estratégia;&#x20;
9. Deposita-se os 50% que foram sacados anteriormente e coleta-se novamente.

## Atualizações de estratégia

Ocasionalmente, os estrategistas da Beefy lançam uma nova estratégia inovadora ou as pools incentivadas mudam seus contratos de recompensa. Se for esse o caso, os cofres Beefy têm a flexibilidade de se adaptar a essas mudanças e  capacidade de trocar de estratégias para que os usuários não precisem migrar seus fundos para um novo cofre: isso é feito automaticamente por uma atualização de estratégia.

A nova estratégia é implantada com um cofre fictício e todos os testes manuais descritos acima são feitos. Depois de passar nas verificações, a nova estratégia é atribuída ao cofre. O cofre recebe a proposta da nova estratégia por meio de uma carteira multi-assinatura(_multi-sig_) e precisa esperar até que o período da tranca de tempo tenha passado antes que o cofre use a nova estratégia.

## **Monitor de **_**Timelocks**_

Durante a vida de nossos cofres, os projetos e protocolos sobre os quais construímos, naturalmente, precisarão usar funcionalidades em seus contratos inteligentes que são suscetíveis a abusos (e para as quais foi exigido uma tranca de tempo para implementar um cofre Beefy). Para proteger contra o risco de abuso, implementamos o canal #👀-timelock-monitor no [Discord da Beefy](https://discord.gg/yq8wfHd).

Ao exibir o contrato e protocolo relevantes, o evento acionado, o método programado para ser chamado e o tempo final da tranca de tempo, o Monitor de _Timelocks_ fornece todas as informações necessárias para avaliar o risco e proteger os fundos do usuário. Como um canal público, o monitor fornece acesso livre a estas informações para nossos usuários, bem como uma visão de como a equipe da Beefy está lidando com estes riscos, para informar a tomada de decisões.

## **Pânico**

Às vezes, se algo dá errado com a pool incentivada (_farm)_ subjacente, agir rapidamente é de grande importância. As estratégias Beefy têm um guardião que pode entrar em pânico, que retira os fundos depositados da pool incentivada de volta ao contrato da estratégia e remove todas as permissões. Isso garante que os fundos estejam sempre disponíveis para que os depositadores da Beefy saquem em caso de emergência.

# Pratica SAFU

_"Não confie, verifique"_

## **Novas fazendas no Beefy**

Antes que uma nova estrategia de farming seja usada no Beefy, o projeto precisa passar por um conjunto rigoroso de regras SAFU:

* Os contratos foram verificados no blockexplorer;
* Liquidez suficiente para trocar recompensas de tokens de farm;
* As funções de migrador são completamente removidas ou bloqueadas de forma suficiente;
* As taxas de emissão de tokens de farm precisam ser bloqueadas por tempo (se os pares de tokens de farm estiverem sendo guardados);
* Todas as mudanças de implementação de proxy devem ser blockeadas com um timelock.

## Novos cofres no Beefy

Nossos estrategistas seguem um procedimento de teste manual em cada novo cofre antes de entrar em operação. Isso é para garantir que o cofre funcione como pretendido e os fundos do usuário sejam sempre SAFU.

1. Deposite uma pequena quantia do ativo;&#x20;
2. Retirar tudo;&#x20;
3. Deposite novamente, espere 1 minuto e verifique se callReward() não é 0;&#x20;
4. Colha a estratégia;&#x20;
5. Entre em pânico com a estratégia;&#x20;
6. Retire 50% enquanto estiver em pânico para garantir que os usuários possam sair;&#x20;
7. Tente depositar, um erro deve aparecer, mas não envie o depósito;&#x20;
8. Retome a estratégia;&#x20;
9. Deposite os 50% que foram sacados anteriormente e colha novamente.

## Atualizações de estratégia

Ocasionalmente, os estrategistas da Beefy lançam uma nova estratégia inovadora ou as farms de produção mudam seus contratos de recompensa. Se for esse o caso, os cofres Beefy têm a flexibilidade de se adaptar a essas mudanças e têm a capacidade de trocar estratégias para que os usuários não precisem migrar seus fundos para um novo cofre: isso é feito automaticamente por uma atualização de estratégia.

A nova estratégia é implantada com um cofre fictício e todos os testes manuais descritos acima são concluídos. Depois de passar nas verificações, a nova estratégia é atribuída ao cofre. O cofre recebe a proposta da nova estratégia por meio de uma carteira multi-sig e precisa esperar até que o atraso do timelock tenha passado antes que o cofre use a nova estratégia.

## **Pânico**

Se algo der errado com a farm de rendimento, agir rapidamente é de grande importância. As estratégias Beefy têm um guardião que pode entrar em pânico, que retira os fundos staked da fazenda de volta ao contrato da estratégia e remove todas as permissões. Isso garante que os fundos estejam sempre disponíveis para os stakers do Beefy sacarem em caso de emergência.

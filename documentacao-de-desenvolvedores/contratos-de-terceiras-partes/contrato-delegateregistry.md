---
description: Tradução feita a partir da atualização de fevereiro de 2023
---

# Contrato DelegateRegistry

O [contrato DelegateRegistry](https://github.com/gnosis/delegate-registry/blob/main/contracts/DelegateRegistry.sol) é um contrato inteligente de governança desenvolvido pela Gnosis e usado pelo Snapshot Labs para facilitar a delegação de votos em espaços de governança baseados em Snapshot. Os usuários podem autorizar outro usuário a votar em seu nome usando seu poder de voto, delegando a eles na BNB Chain. Os usuários também podem remover suas delegações a qualquer momento.

Por meio desse mecanismo, vozes confiáveis na comunidade podem alavancar seu apoio com um pequeno esforço por parte de seus apoiadores. Também permite que aqueles com pouco tempo garantam que seu poder de voto esteja participando da governança, sem exigir que eles se envolvam com todas as propostas que surgem.

## Mapeamento do Contrato

O contrato DelegateRegistry é, antes de tudo, um repositório de informações sobre as delegações existentes, que são armazenadas no mapeamento de "delegação" no contrato:

```solidity
// The first key is the delegator and the second key a id. 
// The value is the address of the delegate 

mapping (address => mapping (bytes32 => address)) public delegation;
```

Efetivamente, cada delegação é armazenada por referência ao endereço do delegante (ou seja, o usuário que delegou seu poder de voto), que é então mapeado para o ID do espaço Snapshot relevante (armazenado como um valor bytes32) e o endereço do delegado (ou seja, o usuário a quem o poder de voto é delegado).

Para obter detalhes completos de todas as delegações gerenciadas pelo contrato DelegateRegistry do Snapshot Labs, você pode explorar o Snapshot Subgraph [aqui](https://thegraph.com/hosted-service/subgraph/snapshot-labs/snapshot).

## Eventos do Contrato

O contrato DelegateRegistry emite dois eventos possíveis em suas operações ordinárias.

### SetDelegate

Significa que a função [#setdelegate-1](contrato-delegateregistry.md#setdelegate-1 "mention") do contrato foi chamada com sucesso e, consequentemente, o chamador selecionou um novo delegado.

```solidity
// Using these events it is possible to process the events to build up reverse lookups.
// The indeces allow it to be very partial about how to build this lookup (e.g. only for a specific delegate).

event SetDelegate(address indexed delegator, bytes32 indexed id, address indexed delegate);
```

### ClearDelegate

Significa que uma das [#funcoes-do-contrato](contrato-delegateregistry.md#funcoes-do-contrato "mention") abaixo foi chamada com sucesso e, conseqüentemente, o antigo delegado foi liberado do chamador.

```solidity
// Using these events it is possible to process the events to build up reverse lookups.
// The indeces allow it to be very partial about how to build this lookup (e.g. only for a specific delegate).

event ClearDelegate(address indexed delegator, bytes32 indexed id, address indexed delegate);
```

## Funções do Contrato

A funcionalidade por trás do contrato DelegateRegistry é muito direta e consiste em apenas duas funções para definir e remover delegados.

### setDelegate()

Para definir um delegado, o contrato requer duas entradas: o ID do espaço Snapshot relevante (armazenado como um valor bytes32); e o endereço do delegado (ou seja, o usuário ao qual o poder de voto é delegado). Em seguida, ele testa as entradas em relação a alguns requisitos (por exemplo, o usuário não está delegando para si mesmo, para um endereço nulo ou para seu representante atual) antes de executar a chamada.

```solidity
/// @dev Sets a delegate for the msg.sender and a specific id.
///      The combination of msg.sender and the id can be seen as a unique key.
/// @param id Id for which the delegate should be set
/// @param delegate Address of the delegate

function setDelegate(bytes32 id, address delegate) public {
        require (delegate != msg.sender, "Can't delegate to self");
        require (delegate != address(0), "Can't delegate to 0x0");
        address currentDelegate = delegation[msg.sender][id];
        require (delegate != currentDelegate, "Already delegated to this address");
        
        // Update delegation mapping
        delegation[msg.sender][id] = delegate;
        
        if (currentDelegate != address(0)) {
            emit ClearDelegate(msg.sender, id, currentDelegate);
        }

        emit SetDelegate(msg.sender, id, delegate);
}
```

Quando a chamada for bem-sucedida, a função atualizará o mapeamento de delegação para o novo endereço de delegado. Em seguida, ele testa se o usuário delegou anteriormente a outro usuário e, em caso afirmativo, emitirá o evento [#cleardelegate](contrato-delegateregistry.md#cleardelegate "mention") para indicar que o delegado antigo foi removido. Por fim emitirá o evento [#setdelegate](contrato-delegateregistry.md#setdelegate "mention") para indicar que um novo delegado foi adicionado.

Observe que a função também não exige que o contrato use a função [#cleardelegate-1](contrato-delegateregistry.md#cleardelegate-1 "mention"), que é usada apenas para remover um delegado existente.

### clearDelegate()

Para remover o delegado atual, o contrato requer uma entrada, que é o ID do espaço Snapshot relevante (armazenado como um valor bytes32). Em seguida, ele testa para garantir que um delegado foi de fato definido antes de executar a chamada.

```solidity
/// @dev Clears a delegate for the msg.sender and a specific id.
///      The combination of msg.sender and the id can be seen as a unique key.
/// @param id Id for which the delegate should be set

function clearDelegate(bytes32 id) public {
        address currentDelegate = delegation[msg.sender][id];
        require (currentDelegate != address(0), "No delegate set");
        
        // update delegation mapping
        delegation[msg.sender][id] = address(0);
        
        emit ClearDelegate(msg.sender, id, currentDelegate);
}
```

Quando a chamada for bem-sucedida, a função atualizará o mapeamento de delegação para o endereço nulo (ou seja, informando que o usuário não delegou seu poder de voto) e, em seguida, emitirá o evento [#cleardelegate](contrato-delegateregistry.md#cleardelegate "mention")para indicar que o antigo delegado foi removido.

## Guia passo-a-passo de delegação

Existem dois métodos principais que os usuários podem adotar para interagir com o contrato DelegateRegistry: interagindo por meio da interface Snapshot ou interagindo diretamente com o contrato (por exemplo, por meio de um block explorer relevante). Abaixo estão breves orientações para cada método.

### Através da interface da Snapshot

1. Acesse a [página de delegação da interface Snapshot](https://vote.beefy.finance/#/delegate/beefydao.eth).
2. Conecte sua carteira ao site, para que ele detecte seu endereço e assim você possa chamar a função [#setdelegate-1](contrato-delegateregistry.md#setdelegate-1 "mention").
3. Certifique-se de estar conectado à BNB Chain na rede BSC com sua carteira. **Nenhuma outra rede funcionará.**
4. Insira o endereço ou nome ENS do usuário ao qual você deseja delegar seu poder de voto.
5. Se desejar, você pode selecionar "limitar a delegação a um espaço específico" para limitar sua delegação apenas ao espaço Beefy Snapshot. Para isso, insira o seguinte espaço: beefydao.eth.
6. Clique em "Confirmar" para iniciar a transação em sua carteira. Como se trata de uma transação de escrita (ou seja, envio de informações para armazenamento na blockchain), você terá que pagar uma pequena quantia de gás para facilitar a transação.

<figure><img src="../../.gitbook/assets/image (34).png" alt=""><figcaption><p>A página de delegação da interface Snapshot fornece uma maneira clara e simples de delegar seu poder de votação.</p></figcaption></figure>

7. Depois que a transação for concluída, você terá delegado com sucesso ao endereço de usuário que forneceu em todas as redes nas quais nossa token BIFI está operante.

### Pelo Block Explorer

1. Acesse o endereço do contrato DelegateRegistry na [BscScan](https://bscscan.com/address/0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446).
2. Navegue até a subguia "Write contract" na guia "Contract" na página do contrato (conforme abaixo).
3. Selecione o botão "Connect to Web3" para conectar sua carteira e interagir com o contrato.
4. Certifique-se de que sua carteira esteja configurada para a BNB Chain na rede BSC. **Nenhuma outra rede funcionará.**

<figure><img src="../../.gitbook/assets/image (59).png" alt=""><figcaption><p>A interface do BscScan fornecerá acesso total a todos os métodos de delegação, eventos e transações, embora sejam claramente menos amigáveis para a maioria dos usuários.</p></figcaption></figure>

5. Role para baixo até a função [#setdelegate-1](contrato-delegateregistry.md#setdelegate-1 "mention") e insira os dados necessários, sendo eles:
   1. id (bytes32) - o endereço do espaço Snapshot para o qual você está delegando (ou seja, o Beefy Space ID: 0x626565667964616f2e657468).
   2. delegate (address) - o endereço do usuário para o qual você deseja delegar seu poder de voto.
6. Clique em "Write" para iniciar a transação em sua carteira. Como se trata de uma transação de escrita (ou seja, envio de informações para armazenamento na blockchain), você terá que pagar uma pequena quantia de gás para facilitar a transação.

<figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption><p>As funções em cada block explorer refletem aquelas detalhadas na seção <a data-mention href="contrato-delegateregistry.md#funcoes-do-contrato">#funcoes-do-contrato</a>acima.</p></figcaption></figure>

7. Depois que a transação for concluída, você terá delegado com sucesso ao endereço de usuário que forneceu em todas as redes nas quais nossa token BIFI está operante.

## Contratos

O contrato DelegateRegistry e o espaço Snapshot Beefy estão lançados nos seguintes endereços:

* DelegateRegistry - [0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446](https://bscscan.com/address/0x469788fE6E9E9681C6ebF3bF78e7Fd26Fc015446).
* Beefy Space ID - 0x626565667964616f2e657468 or beefydao.eth.

## Mais Informações

Para obter mais detalhes sobre como funciona a delegação de votos para a governança da Beefy, consulte a página [governanca.md](../../community/governanca.md "mention")(especificalmente as seções [#como-posso-delegar-meu-voto](../../community/governanca.md#como-posso-delegar-meu-voto "mention") e [#como-posso-me-tornar-um-delegado](../../community/governanca.md#como-posso-me-tornar-um-delegado "mention")). Você também pode encontrar a lista mantida atual de delegados de voto nesta [planilha](https://docs.google.com/spreadsheets/d/1sJH4jg3eEEJDpbws55qUmzPeLDiDuL\_5OAQobSn7m2Y/edit?usp=sharing).

Para obter detalhes completos de todas as delegações gerenciadas pelo contrato DelegateRegistry do Snapshot Labs, você pode explorar o Snapshot Subgraph [aqui](https://thegraph.com/hosted-service/subgraph/snapshot-labs/snapshot). Mais informações estão disponíveis na [documentação](https://docs.snapshot.org/guides/delegation) da Snapshot.

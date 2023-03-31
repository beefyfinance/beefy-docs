---
description: >-
  Esse guia visual vai te mostrar cada passo para depositar seus fundos em um
  cofre
---

# Como participar de um cofre

### Pré-requisitos

* Você deve ter a moeda referente ao cofre na sua carteira. Veja aqui como adicionar fundos na sua carteira: [depositando-fundos-na-carteira.md](../../comece-agora/depositando-fundos-na-carteira.md "mention").
* Você deve usar uma carteira compatível, como a Metamask ou a Trustwallet: [conectando-a-carteira-a-beefy.md](../../comece-agora/conectando-a-carteira-a-beefy.md "mention")

### Guia passo-a-passo

#### 1. Acesse o [aplicativo da Beefy](https://app.beefy.com/):

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption><p>Data do print: 10 de outubro de 2022</p></figcaption></figure>

Novamente, certifique-se que a sua carteira esteja conectada e que ela tenha suas moedas.

#### 2. Use os filtros para achar um cofre no qual queira fazer seu depósito:

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

As logos das blockchains, os botões de classificações e o campo de pesquisa agem como filtros.

#### 3. Exemplo de uso dos filtros

Neste guia, nós vamos usar o cofre BIFI Maxi na Arbitrum como exemplo:

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

Note que a Pool de Ganhos BIFI, na qual você sua BIFI depositada rende WETH, também aparece. Abra o cofre BIFI Maxi clicando em qualquer lugar no campo acima.

#### 4. Dentro do cofre BIFI Maxi:

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Existem muitas informações dentro do cofre, como o TVL (Valor Total Depositado), Preço e histórico do APY (Rendimento Anual Percentual), o [beefy-safety-score.md](../../protocolo-safu/beefy-safety-score.md "mention"), detalhes das moedas subjacentes e a estratégia de composição do cofre ( [#o-que-e-uma-estrategia-de-cofre](../../produtos/strategies.md#o-que-e-uma-estrategia-de-cofre "mention")).

#### 5. O módulo de Depósitos e Saques:

<figure><img src="../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

O cofre já vê que temos 1 BIFI disponível na nossa carteira para depósito. Há um link "_Buy Token_" (Compre moedas) provido caso você não tenha BIFI ou queira comprar mais BIFI para depositar, assim como um botão "_Bridge_ BIFI" para transferir BIFI de uma outra blockchain para a Arbitrum ( [how-to-bridge-bifi-cross-chain.md](how-to-bridge-bifi-cross-chain.md "mention")). O campo de depósito e um botão MAX são usado para colocar a exata quantidade de BIFI que você quer depositar. Além do mais, as taxas do cofre são mostradas ( [#qual-e-a-estrutura-de-taxas-do-cofre](../../produtos/vaults.md#qual-e-a-estrutura-de-taxas-do-cofre "mention")).

#### 6. Um exemplo de depósito:

Neste exemplo, nós primeiro clicamos no botão "MAX" para depositar todas as BIFI da nossa carteira, em seguida clicamos no botão "_DEPOSIT ALL_" (depositar tudo).

<figure><img src="../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

Quando é a primeira vez que você deposita em um cofre, você precisa dar permissão ao contrato do cofre para acessar os seus fundos:

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

Na próxima transação você estará de fato depositando no cofre:

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Resumindo, depositar em um novo cofre sempre requer duas transações: uma para aprovar a permissão de uso da moeda na sua carteira e uma para o depósito em si.

#### 7. Confirmação do depósito:

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

Uma vez que a transação for sucedida, uma mensagem vai aparecer confirmando o depósito e ela contém um link para a transação no _block explorer._ É muito importante entender que a sua carteira agora tem um comprovante de depósito em forma de moeda chamado de "moeda moo" ( [#o-que-sao-moedas-moo](../../produtos/vaults.md#o-que-sao-moedas-moo "mention")). Essa moeda moo é necessária para fazer o saque do cofre, não a perca!

Na página da transação de depósito do _block explorer_ você pode ver que as moedas moo foram de fato passadas para a sua carteira depois de depositar em um cofre. A transferência da moeda vai parecer com algo assim:

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

Como as moedas moo ganham juros, elas são mais valiosas que as moedas "normais" subjacentes. Esse também é o motivo pelo qual a quantidade de moedas moo não bate 1 por 1 com a quantidade de moedas inicialmente depositadas ( [#como-as-moedas-moo-ganham-juros](../../produtos/vaults.md#como-as-moedas-moo-ganham-juros "mention")).

É isso, uma vez que a função de coleta for chamada no cofre, você já está ganhando retornos!

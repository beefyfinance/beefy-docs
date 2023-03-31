---
description: Invista em um cofre da Beefy com um um clique!
---

# Como usar o Beefy Zap

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

\[IMAGE TRANSLATION:        Available On: = Disponível em:             New = Novo

ONE CLICK ZAP IN = USE O ZAP COM UM CLIQUE

Use supported tokens to build LPs on deposit = Use as moedas suportadas para criar LPs ao depositar

In Partnership With: = Em Parceria com:]

O Beefy ZAP permite criar moedas de pool de liquidez e fazer depósitos nos cofres da Beefy com apenas uma transação. Você não precisa mais [adicionar e remover manualmente a liquidez!](how-to-add-remove-liquidity.md) O Beefy ZAP é uma solução simples, rápida, barata e segura que elimina a necessidade de lidar com endereços de contrato de token ou até mesmo de deixar o ambiente confortável do aplicativo Beefy.

Essa página mostra um tutorial curto de como depositar e sacar nos cofres da Beefy com as nossas ferramentas ZAP. Para uma explicação de maior nível conceitual das nossas ferramentas ZAP, veja a sessão de infográficos da [#beefy-zap](../infographics.md#beefy-zap "mention").

{% hint style="info" %}
Ao utilizar o Zap, cheque sempre o seu pedido! Embora o Zap o proteja contra o 'deslize' do mercado (alterações de preço entre o momento do pedido da transação de troca e o momento da execução), ele **não** o protege contra o impacto no preço (o quanto sua transação alterará o preço das moedas na pool de liquidez).
{% endhint %}

## Cofre de exemplo

{% hint style="info" %}
Última atualização: janeiro de 2023. Como o site está em constante desenvolvimento, a interface que você vê pode variar ligeiramente das capturas de tela abaixo ao longo do tempo.
{% endhint %}

Para os propósitos desses tutoriais usaremos o cofre stMATIC-MATIC sLP da Beefy para a DEX Dystopia na blockchain da Polygon. Esse cofre suporta tanto o ZAP V1 quanto o ZAP V2.

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption><p>O primeiro passo é navegar até a página referente ao cofre que você deseja entrar. Para esse tutorial, usaremos o cofre stMATIC-MATIC sLP da Beefy para a DEX Dystopia na blockchain da Polygon.</p></figcaption></figure>

Para aqueles que estão seguindo este tutorial, basta navegar até a página relevante para o cofre que você gostaria de entrar. Entretanto, esteja ciente de que nossas ferramentas ZAP não estão disponíveis para todos os cofres em todas as blockchains, portanto, você deve verificar nesta fase se o menu suspenso da moeda de depósito em "_Select token_" permite depósitos com ativos diferentes. Certifique-se também de conectar sua carteira antes de tentar depositar.

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption><p>A segunda etapa é ver quais moedas você pode usar para fazer o depósito. Sem o ZAP, você só pode depositar a moeda do cofre (no caso, a moeda LP no topo da lista). Com o V1, você pode fazer o depósito com as moedas subjacentes da LP (ex: WMATIC, stMATIC ou MATIC). Com o V2, você pode fazer o depósito com uma maior abrangência de ativos (ex: USDC, USDT, DAI etc).</p></figcaption></figure>

Quando o ZAP V2 está disponível e você seleciona uma moeda que pode ser utilizada tanto pelo V1 quanto pelo V2, você também poderá decidir qual ferramenta usar. Para trocar entre os dois, procure a seta lateral no cabeçalho "Beefy" no topo da caixa _"Zap Route"._

<figure><img src="../../.gitbook/assets/image (41).png" alt=""><figcaption><p>Quando o ZAP V2 está disponível e você seleciona uma moeda que pode ser utilizada tanto pelo V1 quanto pelo V2, você também poderá decidir qual ferramenta usar. Para trocar entre os dois, procure a seta lateral no cabeçalho "Beefy".</p></figcaption></figure>

A interface vai te oferecer que você escolha um provedor mostrar os provedores de ZAP disponíveis e ferramentas que você pode usar. Nesse caso, você pode escolher entre o ZAP V1 (ou "Beefy" como mostrado abaixo) ou o ZAP V2 ( ou "Beefy x 1inch" como mostrado abaixo).

<figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption><p>A interface permite selecionar entre usar a própria ferramenta do Beefy (usando ZAP V1) ou alternativamente um agregador de DEXes como 1inch (usando ZAP v2).</p></figcaption></figure>

## ZAP V1: Entrando em Cofres

Para usar o ZAP V1 para depósitos, certifique-se de ter selecionado a aba "_Deposit_" na parte superior da caixa mostrada no lado direito da imagem abaixo. Use a opção "_Select token_" para selecionar um dos ativos subjacentes para o cofre (por exemplo, WMATIC, stMATIC ou MATIC), mas não a moeda principal do depósito (por exemplo, stMATIC-MATIC sLP). Você pode então digitar a quantidade da moeda que deseja depositar de sua carteira, ou clicar em "MAX" para depositar todas as moedas de uma só vez.

A IU mostrará então uma estimativa de quanto da moeda principal do depósito (por exemplo, stMATIC-MATIC sLP) você receberá e então depositará através do processo do ZAP V1. Abaixo, a caixa "_Zap Route_" mostra as diferentes etapas dos processos e estimativas de quanto de cada moeda será recebida e usada em cada parte da transação. Observe que é impossível saber com antecedência exatamente quanto você receberá pelas trocas em um processo ZAP, portanto os valores finais podem variar ligeiramente em relação às estimativas.

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption><p>Para fazer o depósito com o ZAP V1, selecione uma das moedas subjacentes no cofre e insira a quantidade que você deseja depositar no cofre.</p></figcaption></figure>

Para executar a transação proposta, clique em "_Deposit_" ou "_Deposit All_", sua carteira escolhida acionará uma transação (possivelmente incluindo uma transação de aprovação primeiro). Uma vez executada a transação, você receberá a confirmação de que a transação foi submetida na blockchain e que a confirmação está pendente. Uma vez validada a transação na blockchain, você receberá então a confirmação de que a transação foi concluída, o que significa que as moedas da sua carteira estarão agora no cofre.

E é isso! Depósito completo. O Beefy ZAP V1 criou liquidez com a Dystopia automaticamente e depositou essa liquidez no cofre da Beefy. Você pode verificar quando nossos cofres vão coletar recompensas e compor mais moedas LP.

## ZAP V1: Saindo de Cofres

Ao contrário, você pode retirar selecionando a aba "_Withdraw_" ao invés de "_Deposit_". Use a opção "_Select token_" para selecionar um dos ativos subjacentes do cofre (WMATIC, stMATIC, MATIC). Você pode então selecionar a quantidade de moedas LP que deseja retirar, ou usar o botão "MAX" para selecionar todas. Observe que o número de moedas LP é normalmente diferente do número de moedas moo ou do número de moedas de ativos subjacentes que você receberá, de modo que a quantidade exibida pode causar confusão.

A IU exibirá então uma estimativa de quanto da moeda escolhida para a retirada (por exemplo, MATIC) você receberá através dos processos do ZAP V1. Abaixo, a caixa "_Zap Route_" mostra as diferentes etapas e estimativas de quanto de cada moeda será recebida e usada em cada subtransação. Assim como nos depósitos, é impossível saber com antecedência exatamente quanto você receberá pelas trocas nos processos ZAP, portanto, os valores finais podem variar ligeiramente das estimativas.

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption><p>Para reitrar com o ZAP V1, selecione uma das moedas subjacentes no cofre e insira o número de moedas que você deseja retirar do cofre.</p></figcaption></figure>

Para executar a transação proposta, clique em "_Withdraw_" ou "_Withdraw All_", e sua carteira acionará outra transação (incluindo aprovações, se necessário). Uma vez executada a transação, você receberá a confirmação de que a transação foi submetida na blockchain e a confirmação está pendente. Assim que a transação for validada na blockchain, você receberá a confirmação de que a transação foi concluída, o que significa que as moedas retiradas do cofre estarão agora em sua carteira.

Aí está! Retirada completa. O Beefy ZAP V1 tomou todas as medidas para sair do cofre, quebrar a posição de liquidez e trocar de volta para a moeda escolhida.

## ZAP V2: Entrando em Cofres

O fluxo de trabalho do ZAP V2 é quase idêntico ao do V1 do ponto de vista do usuário. Você pode selecionar qualquer uma das moedas disponíveis no menu suspenso "_Select token_" e inserir a quantia a ser depositada na caixa à direita. Novamente a IU mostrará as estimativas do número de moedas LP que você receberá para depositar no cofre, e cada uma das etapas até o depósito (incluindo as trocas iniciais para os ativos subjacentes do cofre).

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption><p>Para o fluxo de trabalho do depósito ZAP V2, selecione qualquer uma das moedas disponíveis no menu suspenso e insira a quantidade que você deseja depositar no cofre.</p></figcaption></figure>

Assim como no processo V1 detalhado acima, basta pressionar "_Deposit_" ou "_Deposit All_", percorrer a transação em sua carteira e ver a transação concluída na cadeia de bloqueio. Depósito completo! O Beefy ZAP V2 levou você de suas moedas escolhidas para as moedas subjacentes do cofre, e depois executou o mesmo fluxo de trabalho que o ZAP V1.

## ZAP V2: Saindo do Cofre

Da mesma forma, o fluxo de trabalho de retirada do ZAP V2 também é quase idêntico ao V1 para os usuários. Como nos depósitos, agora você pode selecionar qualquer uma das moedas disponíveis no menu suspenso "_Select token_" e inserir a quantidade a ser depositada na caixa à direita. Novamente a IU mostrará a estimativa de quanto da moeda escolhida para a retirada (por exemplo, ETH) você receberá, e quanto de cada moeda será recebida para cada etapa do processo.

<figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption><p>Para a retirada pelo ZAP V2, selecione qualquer uma das moedas disponíveis no menu suspenso e insira a quantidade de moedas LP que você deseja retirar do cofre.</p></figcaption></figure>

Assim como no processo V1 detalhado acima, basta clicar em "_Withdraw_" ou "_Withdraw All_", aceitar a transação em sua carteira e ver a transação concluída na blockchain. Retirada completa! O Beefy ZAP V2 o levou por todas as etapas do V1 para sair do cofre e quebrar a posição de liquidez, antes de trocar as moedas do cofre para a moeda escolhida no V2.

{% hint style="info" %}
A quota do ZAP que é mostrada durante o processo de depósito ou de saque já inclui a taxa do ZAP calculada. Adicionalmente, a taxa do ZAP é deduzida apenas das trocas de moedas. As taxas primeiro são acumuladas em um lote de tesouro, depois são trocadas para moedas estáveis e enviadas para o [tesouro da Beefy](https://app.beefy.com/treasury). O ZAP V1 original continua de uso gratuito.
{% endhint %}

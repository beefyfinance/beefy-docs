# APY dos Cofres

## **O que é o APY?**

Vamos dar uma olhada em uma típica pool incentivada, onde eles declaram um APY (juros compostos) como +100%, por exemplo. A definição tradicional de APY **é a taxa real de retorno obtida em um investimento, levando em consideração o efeito do reinvestimento dos lucros.** O uso dessa terminologia indicaria que a pool incentivada estivesse reinvestindo os ganhos para você. Isso simplesmente não é o caso. Uma terminologia mais aplicável a ser usada seria APR (juros simples), ou seja, a taxa anual obtida em um investimento. Por definição, isso significaria que sua pool incentivada com 100% de rendimento dobraria seu investimento original no final do ano 1 sem reinvestir nenhum lucro. Mas e se você reinvestisse todo esse valor no ano seguinte e no ano seguinte?

## **Entendendo o Crescimento Exponencial (Reinvestimento)**

Crescimento cuja taxa se torna cada vez mais rápida em proporção ao número ou tamanho total crescente. A fórmula simples para isso é **crescimento = (1 + r)^x** , onde 'r' = retorno e 'x' = número de 'vezes'. Por exemplo, seu dinheiro dobra a cada ano se você receber 100% de retorno anual. Após 3 anos você teria 8x seu investimento original.

![crescimento = (1 + 100%)^3](<../.gitbook/assets/capture (2).png>)

\[CORRECTIONS TO THE IMAGE ABOVE: Amount = quantidade\
Time = Tempo]

## **Ok, então o que REALMENTE é o APY?**

Um investimento típico não paga apenas anualmente, mas em termos menores (diariamente, mensalmente, etc). Em pools incentivadas, os retornos podem até ser pagos por bloco. Com uma média de 28.800 blocos por dia e taxas de transação baratas, isso pode permitir uma quantidade significativa de crescimento exponencial ou reinvestimento de seu retorno. Vamos ver como dissecar isso...

* Valor final = **P \* (1+r/n)^nt**                Exemplo: 100 \* (1+1/12)^(12\*1)
* P = saldo inicial
* r = APR = 100%
* n = períodos de reinvestimento = 12 meses
* t = time = 1 ano
* O cálculo simples do APY no Excel também pode ser declarado como =EFFECT(r, n)

![No final do ano 1 teria 261 moedas ou 161% APY ao invés de 100% APR sem reinvestimento](<../.gitbook/assets/capture (3).png>)

\[CORRECTIONS TO THE IMAGE ABOVE: Amount = quantidade\
Months = Meses]

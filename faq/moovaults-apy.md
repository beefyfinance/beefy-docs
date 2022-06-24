# mooVaults APY

## **O que é o API?**

Vamos dar uma olhada em uma fazenda de rendimento típica, onde eles declaram um APY (juros compostos) como +100%, por exemplo. A definição tradicional de APY é a taxa real de retorno obtida em um investimento, levando em consideração o efeito dos lucros compostos**. O uso dessa terminologia indicaria que a fazenda de rendimento estava compondo os ganhos para você. Isso simplesmente não é o caso.** Uma terminologia mais aplicável a ser usada seria APR (juros simples), ou seja, a taxa anual obtida por meio de um investimento. Por definição, isso significaria que sua fazenda com 100% de rendimento dobraria seu investimento original no final do ano 1 sem reinvestir nenhum lucro. Mas e se você reinvestisse todo esse valor no ano seguinte e no ano seguinte?

## **Entendendo o crescimento exponencial (composição)**

Crescimento cuja taxa se torna cada vez mais rápida em proporção ao número ou tamanho total crescente. A fórmula simples para isso é **growth = (1 + r)^x** , onde 'r' = return e 'x' = número de 'vezes'. Por exemplo, seu dinheiro dobra a cada ano se você receber 100% de retorno anual. Após 3 anos você teria 8x seu investimento original.

![growth = (1 + 100%)^3](<../.gitbook/assets/capture (2).png>)

## **Ok, então o que REALMENTE é o APY?**

Um investimento típico não paga apenas anualmente, mas em termos menores (ou seja: diariamente, mensalmente, etc). Para o farming de rendimento, os retornos são pagos por bloco. Com uma média de 28.800 blocos por dia e taxas de transação baratas, isso pode permitir uma quantidade significativa de crescimento exponencial ou composição de seu retorno. Vamos ver como quebrar isso...

* Compound = **P \* (1+r/n)^nt**                Example : 100 \* (1+1/12)^(12\*1)
* P = saldo inicial
* r = APR = 100%
* n = períodos compostos = 12 meses
* t = time = 1 ano
* O cálculo simples de APY no Excel também pode ser declarado como =EFFECT(r, n)

![Year 1 end would be 261 tokens or 161% APY versus 100% APR w/o compounding](<../.gitbook/assets/capture (3).png>)














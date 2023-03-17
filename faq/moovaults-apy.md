# mooVaults APY

## Che cos'è l'APY?

Consideriamo una tipica yield farm, dove dichiarano un APY (rendimento percentuale annuo) del 100%. La definizione tradizionale di APY **è il tasso di rendimento reale guadagnato su un investimento tenendo conto dell'effetto della capitalizzazione degli utili**. L'utilizzo di questa terminologia indicherebbe che la yield farm stava componendo gli interessi per te. Semplicemente, non è questo il caso. Una terminologia più azzeccata sarebbe l'APR (tasso percentuale annuale),  intendendo il tasso annuale guadagnato da un investimento. Per definizione ciò vorrebbe dire che la farm del 100% duplicherà il tuo investimento iniziale alla fine del primo anno, senza reinvestire i guadagni. Ma cosa accadrebbe se reinvestissi l'intera somma il prossimo anno e anche l'anno dopo?

## Comprendere la crescita esponenziale (Compounding)

La crescita il cui ritmo diventa sempre più rapido in proporzione alla crescita del numero o delle dimensioni. La semplice formula per questo è **crescita **_**= (1 + r)^x** _ , dove 'r' = ritorno e 'x' = numero di 'volte'. Per esempio, se ottieni un ritorno del 100% annuo, i tuoi soldi raddoppiano ogni anno. Dopo 3 anni avrai 8 volte il tuo investimento iniziale.&#x20;

![growth = (1 + 100%)^3](<../.gitbook/assets/capture (2).png>)

## &#x20;Ok, quindi cos'è REALMENTE l' APY?

Un investimento tipico non paga su base annuale, ma paga a piccoli termini (cioè giornalmente, mensilmente, etc.). Per lo yield farming, i rendimenti vengono addirittura pagati in base ai blocchi. Con una stima di 28000 blocchi per giorno e commissioni di transazione basse, ciò permette un quantitativo di crescita esponenziale o compounding significativo. Diamo un'occhiata per capirlo meglio...

* Composto = **P \* (1+r/n)^nt**                Esempio : 100 \* (1+1/12)^(12\*1)
* P = principale o bilancio iniziale
* r = APR = 100%
* n = periodi di composizione = 12 mesi
* t = tempo = 1 anno
* Il semplice calcolo APY in Excel può anche essere indicato come =EFFECT(r, n)

![Alla fine del primo anno avremo 261 token o il 161% APY verso il 100% APR senza compounding](<../.gitbook/assets/capture (3).png>)














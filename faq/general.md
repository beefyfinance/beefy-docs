# Generale

## Beefy ha un audit?

Il nostro primo revisore è stato DefiYield, Che ha fatto l'audit del token $BIFI, della RewardPool e di tutti i timelocks.

Adesso Beefy ha anche l'audit di Certik, che garantisce la robustezza dei nostri smart contract e la sicurezza dei fondi investiti tramite Beefy. Certik ha anche provveduto audit per progetti come Ocean Protocol, NEO, Ontology e Waves.

Certik ha fatto l'audit di alcune delle strategie d'investimento più complesse e riutilizzabili, usate nella piattaforma. Ciò assicura la robustezza e la sicurezza di aspetti importanti della piattaforma con cui la maggior parte degli utenti interagiscono.

[Tutti gli audit di Beefy possono essere trovati qui.](https://github.com/beefyfinance/beefy-audits)

## Cos'è un ottimizzatore di rendimenti?

Un ottimizzatore di rendimenti è un servizio automatizzato che cerca di guadagnare il ritorno più elevato possibile da crypto-investimenti, in modo molto più efficace rispetto al tentativo di massimizzarli manualmente.

Ogni cassaforte ha la sua strategia per farmare, che normalmente include il reinvestimento degli asset crypto messi a rendita nelle pool di liquidità. In parole povere, farma le ricompense date dagli asset messi a rendita e le reinveste nelle pool di liquidità. Ciò incrementa ila quantità di interessi ricevuti e incrementa la quantità di asset su cui si basa la rendita. un ottimizzatore di rendimenti può ripetere qusto processo migliaia di volte al giorno.

Questo semplice metodo è il motivo dietro agli elevati APY che si trovano su Beefy. Le commissioni per il compounding sono ammortizzate tra tutti i partecipanti alla cassaforte, rendendole più economiche per l'utente.

## Qual è la differenza tra APR e APY?

L'APR (Tasso Percentuale Annuale) è l'interesse annuale, meno le commissioni. Ciò non include l'effetto compounding che si verifica dal reinvestimento dei profitti. Se tu dovessi investire $100 con un APR del 100%, faresti $100 di profitto nell'arco di un anno.

Tuttavia, se tu reinvesti i tuoi profitti regolarmente, componi il tuoi interesse. Ciò calcolato nell'arco di un anno ti da l'APY (Rendimento Percentuale Annuo). Più spesso componi il tuo interesse, maggiore sarà la differenza tra APR e APY.

## Come funziona l'APY?

L'APY è il rendimento percentuale annuo offerto da investimenti particolari. tiene conto dell'interesse composto, dandoti un'idea accurata del tuo ritorno comparato con l'interesse semplice.

APY elevati, con percentuale di migliaia, sono possibili con investimenti che forniscono rendimenti giornalieri dell'1% o più. Dato che le tue ricompense nella pool di liquidità vengono costantemente raccolte e reinvestite, l'interesse si compone in quantità sempre maggiori.

## Cosa significano Vault Daily e Trading Daily?

Trading Daily (Trading Giornaliero) rappresenta quanto i tuoi token della liquidità aumenteranno in valore. Le pool di liquidità condividono le commissioni tra tutti i fornitori di liquidità, come introdotto dal [modello di liquidità di Uniswap](https://docs.uniswap.org/). Il Trading Daily è influenzato dal volume di scambi e dalla percentuale di commissioni di trading allocate ai fornitori di liquidità.

Vault Daily rappresenta quanto i tuoi token aumenteranno in numero. Dato che la cassaforte raccoglie e reinveste continuamente le ricompense, la quantità dei tuoi token depositati incrementa. Vault Daily è influenzato dalle ricompense della farm (cioè incentivi aggiuntivi aggiuntivi alle commissioni del trading), come ad esempio CAKE su Pancakeswap.

Trading Daily eVault Daily possono essere moltiplicati per 365 per formare il Trading APR e il Vault APR. Il Vault APR è poi convertito nel Vault APY per includere anche l'interesse composto. La percentuale di APY totale mostrata viene calcolata così:

$$
APY = (1 + vaultAPY) * (1 + tradingAPR) - 1
$$

&#x20;Un comodo tool per convertire APR in APY è: [APRtoAPY.com](https://www.aprtoapy.com/)

## Come posso sapere quanti guadagni ho accumulato?

Puoi usare una dashboard per la DeFi che sarà in grado di calcolare esattamente quanto profito hai fatto dai tuoi investimenti. Tool esterni come [Yieldwatch](https://yieldwatch.net/) per la rete BSC oppure [PolygonDex](https://polygondex.com/track/yield/yieldMeBroDawg.aspx) per la rete Polygon si connetteranno al tuo wallet e ti daranno un'accurata immagine del tuo investimento iniziale e dei tuoi guadagni correnti.

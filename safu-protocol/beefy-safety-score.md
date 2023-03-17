---
description: Punteggio di sicurezza di Beefy
---

# Beefy Safety Score

Questo documento delinea il design per il punteggio di sicurezza di Beefy. Lo scopo del punteggio di sicurezza è di educare gli utenti quando devono fare la decisione di entrare in una cassaforte di Beefy in particolare. Il punteggio di sicurezza non deve necessariamente essere perfetto, ma è un altro utile strumento che aiuta l'utente.

Il punteggio di sicurezza che una cassafote può ottenere va da 1 a 10. Il miglior punteggio possibile è 10, il peggiore è 0. Tecnicamente è possibile per una cassaforte ricevere meno di 0 ma in quel caso si vedrà solo lo 0.

I rischi sono distribuiti in tre categorie principali:

* Rischi di Beefy: Rischi aggiunti da noi in quanto fungiamo da piattaforma.&#x20;
* Rischi dell'Asset: Rischii legati all'asset gestito dalla cassaforte.
* Rischi della Piattaforma: Rischi legati alla sottostante farm o alla piattaforma usata.

Ogni categoria è responsabile di una percentuale del punteggio totale. Ogni categoria si divide a sua volta in più sottocategorie.

Tutte le casefforti iniziano con un perfetto punteggio di 10 da cui vengono sottratti punti ogni qualvotla che si trovano qualità che aumentano i rischi.

## Categoria: Rischi di Beefy

Sono rischi relativi alla piattaforma stessa di Beefy Finance. Potrebbero essere rischi aggiunti dalla complessità della strategia della cassaforte, se è una distribuzione sperimentale, se è stata controllata da altri etc. I rischi di Beefy determinano il 20 per cento del punteggio di sicurezza.

### Sottocategoria: Complessità

Tiene traccia della complessità della strategia che sta dietro ad una cassaforte.

#### COMPLEXITY\_LOW

* Titolo: Strategia a bassa complessità (Low complexity strategy)
* Spiegazione: Le strategie a bassa complessità hanno poche, se ne hanno, parti in movimento, e il loro codice è semplice da leggere e da mettere a punto. C'è una correlazione diretta tra la complessità del codice e i rischi impliciti. Una strategia semplice mitiga l'implementazione di rischi.
* Criteri di Qualificazione: Una strategia a bassa complessità deve interagire con solo un controllato e ben conosciuto smart contract cioè MasterChef. La strategia serve solo come facciata per questo smart contract, inoltrando deposito, raccolta e ritiro usando una sola linea di codice.&#x20;

#### COMPLEXITY\_MID

* Titolo: La strategia di Beefy è di complessità media (Beefy strategy is of medium complexity)
* Spiegazione: Strategie di media complessità interagiscono con due o più controllati e ben conosciuti smart contract. Il loro codice è ancora facile da leggere, da testare e da mettere a punto. Questo mitiga la maggior parte dei rischi di implementazione mantenendo il tutto semplice, ma comunque l'interazione di due o più sistemi aggiunge un livello di complessità.
* Criteri di Qualificazione: Una strategia di media complessità interagisce con due o più smart contract ben conosciuti. Questa strategia automatizza l'esecuzione di una serie di step senza percorsi alternativi. Ogni volta che vengono chiamate le funzioni di deposit(), harvest() e withdraw(), si segue lo stesso percorso di esecuzione.

#### COMPLEXITY\_HIGH

* Titolo: La strategia di Beefy è complessa&#x20;
* Speigazione: Sttategie ad alta complessità interagiscono con uno o più smart contract ben conosciuto. Questa strategie avanzate presentano ramificati percorsi di esecuzione. In alcuni casi sono necessari molteplici smart contract per implementare la strategia completa.
* Criteri di Qualificazione: Una strategia ad alto livello di complessità può essere identificata da uno o più dei seguenti fattori: alta complessità ciclomatica, interazione tra due o più piattaforme di terze parti, implementazione divisa tra più smart contract.

### Sottocategoria: Tempo nel Mercato

Tiene traccia di quanto a lungo la strategia è stata eseguita senza grossi problemi.

#### BATTLE\_TESTED

* Titolo: La strategia di Beefy è testata in battaglia
* Spiegazione: Più tempo è in esecuzione una particolare strategia, più è probabile che eventuali bug potenziali siano stati trovati e corretti. Questa strategia è stata già esposta ad attacchi e utilizzo per un po' di tempo, con cambiamenti piccoli o nulli. Ciò la rende più robusta.&#x20;
* Criteri di Qualificazione:
  * È stato distribuita utilizzando un BeefyStratFactory
  * Sono state distribuite 10+ strategie condividendo lo stesso codice
  * Ha lavorato come previsto per 3 mesi senza nessun aggiornamento

#### NEW\_STRAT

* Titolo: La strategia è in esecuzione da meno di un mese&#x20;
* Spiegazione: Più tempo è in esecuzione una particolare strategia, più è probabile che eventuali bug potenziali siano stati trovati e corretti. Questa strategia è una modificazione o un'iterazione di una precedente strategia. Non è stata testata in battaglia tanto quanto le altre.
* Criteri di Qualificazione: -

#### EXPERIMENTAL\_STRAT

* Titolo: La strategia ha delle caratteristiche nuove
* Spiegazione: Più tempo è in esecuzione una particolare strategia, più è probabile che eventuali bug potenziali siano stati trovati e corretti. Questa strategia è nuova di zecca ed ha almeno una caratteristica sperimentale. Usala a tua discrezione.
* Criteri di Qualificazione: -

## Categoria: Rischi degli Asset

Rischi legati agli asset oppure asset gestiti dalla cassaforte. Entrare in una cassaforte con BTC ha rischi diversi rispetto ad entrare in una cassaforte con una coin nuova e più piccola. Questa categoria determina il venti per cento del punteggio.

### Sottocategoria: Impermanent Loss (Perdita Impermanente)

Tiene traccia del rischio di impermanent loss della cassaforte

#### IL\_NONE

* Titolo: IL previsto molto basso o nullo&#x20;
* Spiegazione: L'asset in questa cassaforte ha un impermanent loss minimo o addirittura inesistente. Ciò potrebbe essere dato dal fatto che stai mettendo in staking un asset singolo oppure perché gli asset che compongono l'LP sono strettaemnte correlati come USDC-USDT o WBTC-renBTC.
* Criteri di Qualificazione: Casseforti con asset singoli e casseforti che gestiscono stablecoin con un peg non sperimentale: USDT, USDC, DAI, sUSD, etc. &#x20;

#### IL\_LOW

* Titolo: IL previsto basso&#x20;
* Spiegazione: Quando fornisci liquidità ad una coppia di token, per esempio ETH-BNB, c'è il rischio che tali asset si disaccoppino nel prezzo. BNB potrebbe perdere valore considerevolmente rispetto ad ETH. Come risultato perderai dei fondi, rispetto a detenere ETH e BNB separati. Gli asset in questa cassaforte sono esposti al rischio di impermanent loss.&#x20;
* Criteri di Qualificazione: Vi rientrano le casseforti che gestiscono ciò che normalmente viene definito come LP "Pool 1": ETH-USDC, MATIC-AAVE, etc. Token di governance di progetti minori sono solitamente conosciuti come LP "Pool 2" e sono quindi esclusi.

#### IL\_HIGH

* Titolo: IL previsto alto&#x20;
* Spiegazione: Quando fornisci liquidità ad una coppia di token, per esempio ETH-BNB, c'è il rischio che tali asset si disaccoppino nel prezzo. BNB potrebbe perdere valore considerevolmente rispetto ad ETH. Come risultato perderai dei fondi, rispetto a detenere ETH e BNB separati. Gli asset in questa cassaforte sono esposti al rischio di impermanent loss. &#x20;
* Criteri di Qualificazione: Vi rientrano le casseforti che gestiscono LP "Pool 2". Questi LP normalmente includono i token di governance della farm stessa.

#### ALGO\_STABLE

* Titolo: Stabile algoritmicamente, peg sperimentale
* Spiegazione: Quando fornisci liquidità ad una coppia di token, per esempio ETH-BNB, c'è il rischio che tali asset si disaccoppino nel prezzo. BNB potrebbe perdere valore considerevolmente rispetto ad ETH. Come risultato perderai dei fondi, rispetto a detenere ETH e BNB separati. Almeno una delle stablecoin detenute in questa cassaforte è stabile algoritmicamente. Ciò significa che il peg stabile è sperimentale ed altamente rischioso. Usala con attenzione e a tua discrezione.
* Criteri di Qualificazione: Vi rientrano “stablecoins” con peg sperimentali, o tokenomic che in passato hanno ripetutamente fallito nel mantenere il peg.

### Sottocategoria: Liquidità

Tiene traccia di quanto difficile sia comprare/vendere il token della cassaforte.

#### LIQ\_HIGH

* Titolo: Liquidità di trading elevata
* Spiegazione: Quanto liquido è un asset influenza quanto rischioso sia detenerlo. Asset molto liquidi sono scambiabili in molti posti e con un buon volume di scambi. L'asset detenuto in questa cassaforte ha un'alta liquidità. Ciò significa che puoi scambiare i tuoi guadagni facilmente e in molti posti.
* Criteri di Qualificazione: -

#### LIQ\_LOW

* Titolo: Liquidità di trading bassa
* Spiegazione: Quanto liquido è un asset influenza quanto rischioso sia detenerlo. Asset molto liquidi sono scambiabili in molti posti e con un buon volume di scambi. L'asset detenuto in questa cassaforte ha una bassa liquidità. Ciò significa che non è molto facile da scambiare e potresti andare incontro ad elevato slippage quando provi a scambiarlo.
* Criteri di Qualificazione: -

### Sottocategoria: Market Cap (Capitalizzazione di mercato)

Il valore totale di tutte le coin in circolazione. Traccia indirettamente quanto volatile possa essere l'asset sottostante di una cassaforte.

#### MCAP\_LARGE

* Titolo: Alta capitalizzazione di mercato, asset con bassa volatilità
* Spiegazione: La capitalizzazione di mercato dell'asset crypto influenza direttamente quanto rischioso sia detenerlo. Solitamente una bassa capitalizzazione di mercato implica alta volatilità e bassa liquidità. L'asset detenuto in questa cassaforte ha un'alta capitalizzazione di mercato. Ciò significa che potenzialmente è un asset molto sicuro da detenere. L'asset ha un elevato potenziale di restare al valore attuale e crescere col tempo.
* Criteri di Qualificazione: Top 50 MC di Gecko/CMC

#### MCAP\_MEDIUM

* Titolo: Capitalizzazione di mercato media, asset con volatilità media
* Spiegazione: La capitalizzazione di mercato dell'asset crypto influenza direttamente quanto rischioso sia detenerlo. Solitamente una bassa capitalizzazione di mercato implica alta volatilità e bassa liquidità. L'asset detenuto in questa cassaforte ha una capitalizzazione di mercato media. Ciò significa che è potenzialmente sicuro da detenere. L'asset ha il potenziale per restare al valore attuale e crescere col tempo.
* Criteri di Qualificazione: Tra il posto n. 50 e n. 300 MC di Gecko/CMC

#### MCAP\_SMALL

* Titolo: Bassa capitalizzazione di mercato, asset con volatilità elevata
* Spiegazione: La capitalizzazione di mercato dell'asset crypto influenza direttamente quanto rischioso sia detenerlo. Solitamente una bassa capitalizzazione di mercato implica alta volatilità e bassa liquidità. L'asset detenuto in questa cassaforte ha una capitalizzazione di mercato bassa. Ciò significa che è potenzialmente un asset rischioso da detenere. L'asset ha un basso potenziale di rimanere al valore attuale e di crescere col tempo.
* Criteri di Qualificazione: Tra il posto n. 300 e n. 500 MC di Gecko/CMC

#### MCAP\_MICRO

* Titolo: Capitalizzazione di mercato micro, asseto con estrema volatilità
* Spiegazione: La capitalizzazione di mercato dell'asset crypto influenza direttamente quanto rischioso sia detenerlo. Solitamente una bassa capitalizzazione di mercato implica alta volatilità e bassa liquidità. L'asset detenuto in questa cassaforte ha una capitalizzazione di mercato micro. Ciò significa che è potenzialmente un asset molto rischioso da detenere. L'asset ha un basso potenziale di rimanere al valore attuale.
* Criteri di Qualificazione: +500 MC di Gecko/CMC

### Sottocategoria: Supply (Fornitura)

Tiene traccia dei rischi relativi alla supply dell'asset. Potrebbe essere alterata da qualcuno? Quanto è centralizzato?

#### SUPPLY\_CENTRALIZED

* Titolo: Poche e molto potenti whale
* Spiegazione: Quando la supply è concentrata in poche mani, queste possono influenzare notevolmente il prezzo vendendo. Le whale possono manipolare il prezzo di una coin. Più persone hanno interesse acquisito in una coin, più organica e migliore sarà la pirce action.
* Criteri di Qualificazione: Meno di 50 account detengono più del 50% della supply.&#x20;

## Categoria: Rischi della Piattaforma

Rischi legati alla piattaforma terzi usata dalla cassaforte. Quanto track record hanno, quanto è solido il codice, ci sono pericolose azioni che un admin può effettuare etc. Il sessanta per cento del punteggio è determinato da questa categoria.

### Sottocategoria: Reputazione

Cerca di fornire indizi sul track record del team e della community. Quanto è probabile che facciano un rug, per esempio.

#### PLATFORM\_ESTABLISHED

* Titolo: La piattaforma ha un conosciuto track record
* Spiegazione: Quando si prende parte ad una farm, potrebbe essere utile conoscere da quanto tempo la piattaforma esista e il suo grado di reputazione. Più lungo è il track record, più investimenti il team è la community hanno in un progetto. Questa cassaforte farma in un progetto che esiste da molti mesi.
* Criteri di Qualificazione: La sottostante farm esiste da almeno 3 mesi.

#### PLATFORM\_NEW

* Titolo: La piattaforma è nuova e con un piccolo track record
* Spiegazione: Quando si prende parte ad una farm, potrebbe essere utile conoscere da quanto tempo la piattaforma esista e il suo grado di reputazione. Più lungo è il track record, più investimenti il team è la community hanno in un progetto. Questa cassaforte farma in un nuovo progetto, che esiste da pochi mesi.
* Criteri di Qualificazione: La sottostante farm esiste da meno di 3 mesi.

### Sottocategoria: Sicurezza

Tiene traccia delle buone pratiche degli smart contract.

#### NO\_AUDIT

* Titolo: La piattaforma non ha mai ricevuto audit da un revisore di terze parti
* Spiegazione: Gli audit sono revisioni del codice fatte da un gruppo di sviluppatori di terze parti.
* Criteri di Qualificazione: -

#### AUDIT

* Titolo: La piattaforma ha ricevuto un audit da almeno un revisore di fiducia
* Spiegazione: Gli audit sono revisioni del codice fatte da un gruppo di sviluppatori di terze parti.
* Criteri di Qualificazione: Uno o più audit da un revisore che ha un track record positivo nell'ambiente crypto.

#### CONTRACTS\_VERIFIED

* Titolo: Tutti i relativi contratti sono pubblicamente verificati
* Spiegazione: Il codice che gira in un particolare contratto non è pubblico di defualt. I block explorer lasciano che siano gli sviluppatori a verificare il codice dietro un particolare contratto. Questa è una buona pratica perché permette ad altri sviluppatori di verificare che il codice faccia ciò che deve. Questo lo rende meno rischioso.
* Criteri di Qualificazione: -

#### CONTRACTS\_UNVERIFIED

* Titolo: Alcuni contratti non sono verificati
* Spiegazione: Il codice che gira in un particolare contratto non è pubblico di defualt. I block explorer lasciano che siano gli sviluppatori a verificare il codice dietro un particolare contratto. Questa è una buona pratica perché permette ad altri sviluppatori di verificare che il codice faccia ciò che deve. Alcuni dei contratti di terze parti che questa cassaforte usa non sono verificati. Ciò significa che ci sono certe cose che Beefy non è riuscita a controllare.
* Criteri di Qualificazione: -

#### ADMIN\_WITH\_TIMELOCK

* Titolo: Ci sono pericolose funzioni dietro ad un timelock
* Spiegazione: Certe volte il possessore del contratto o l'admin possono eseguire certe funzioni che possono mettere a rischio i fondi degli utenti. La cosa migliore è evitarli del tutto. Se queste funzioni dovessero essere presenti, è importante tenerle dietro ad un timelock per dare una avviso adeguato prima di usarli. Questo contratto ha certe funzione di admin pericolose, ma almeno sono dietro ad un significativo timelock.
* Criteri di Qualificazione: C'è almeno una funzione che può rubare parzialmente o completamente i fondi degli utenti. La funzione dev'essere dietro ad un timelock di almeno 6 ore.

#### ADMIN\_WITHOUT\_TIMELOCK

* Titolo: Ci sono pericolose funzioni senza timelock
* Spiegazione: Certe volte il possessore del contratto o l'admin possono eseguire certe funzioni che possono mettere a rischio i fondi degli utenti. La cosa migliore è evitarli del tutto. Se queste funzioni dovessero essere presenti, è importante tenerle dietro ad un timelock per dare una avviso adeguato prima di usarli. Questo contratto ha certe funzioni di admin pericolose, e non c'è nessun timelock. Potrebbero essere eseguite in qualsiasi momento.
* Criteri di Qualificazione: C'è almeno una funzione che può rubare parzialmente o completamente i fondi degli utenti. La funzione non ha nessun timelock a protezione.

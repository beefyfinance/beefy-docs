# Beefy SAFU Practices

_"Don't Trust, Verify" (Non credere, Verifica)_

## Nuova farm su Beefy

Prima che una nuova farm arrivi su Beefy, il progetto deve rispettare delle regole di sicurezza molto stringenti:

* Contratti verificati su blockexplorer;
* Abbastanza liquidità per scambiare i token di ricompensa;
* Funzioni di rug/migrazione sono completamente rimosse o hanno un blocco temporale sufficiente;
* Le emissioni del token farmato devono essere bloccate temporalmente (se le coppie di token farmato vengono messe in cassaforte);
* Tutte le modifiche di implementazione del proxy devono essere bloccate  nel tempo.

## Nuova cassaforte su Beefy

I nostri strateghi seguono una procedura di test manuale su ogni nuova cassaforte prima che venga resa disponibile. Tutto ciò per assicurarci che la cassaforte funzioni come dovrebbe e che i fondi degli utenti siano sempre SAFU. (Al sicuro)

1\. Depositare una piccola quantità dell'asset; \
2\. Ritirare tutto; \
3\. Depositare nuovamente, aspettare 1 minuto e controllare che `callReward()` non sia 0; \
4\. Raccogliere la strategia; \
5\. Impanicare la strategia; \
6\. Ritirare il 50% mentre impanicata per essere sicuri che gli utenti possano lasciarla; \
7\. Provare a depositare, un errore dovrebbe comparire, senza far proseguire il deposito; \
8\. Riavviare la strategia; \
9\. Depositare il 50% che era stato prima ritirato e raccogliere nuovamente.

## Aggiornamenti delle Strategie

Occasionalmente, gli strateghi di Beefy potranno avere nuove ed innovative strategie, oppure qualche yield farm potrebbe cambiare il suo contratto di ricompensa. Se è questo il caso, le casseforti di Beefy hanno la flessibilità di adattarsi a questi cambiamenti e hanno l'abilità di cambiare la strategia cosicché gli utenti non debbano migrare i loro fondi in una nuova cassaforte: è fatto automaticamente da un aggiornamento della strategia.

La nuova strategia è rilasciata in una cassaforte in una cassaforte fantoccio e tutti i test manuali menzionati sopra sono stati completati. Dopo aver passato i test la nuova strategia viene assegnata alla cassaforte. alla cassaforte viene proposta la nuova strategia tramite un wallet multi-sig e si deve aspettare fino a che passi il timelock pima che la cassaforte possa usare la nuova strategia.

## Panico

Alcune volte qualcosa può non andare per il verso giusto con la farm sottostante, e reagire velocemente è di elevata importanza. Le strategie di Beefy hanno un custode che è abilitato ad impanicarsi, che ritira tutti i fondi dalla farm e rimuove tutte i permessi. Ciò assicura che i fondi siano sempre disponibili per coloro che mettono in staking per essere ritirati in caso di emergenza.

# Interfaccia a riga di comando convergente

La CLI Converged è un motore di comandi rivolto agli operatori. Fornisce una
superficie di comandi coerente per la diagnostica della piattaforma,
l'automazione, lo storage e le operazioni sui domini, consentendo al contempo a
ogni funzionalità di rimanere nel proprio modulo di comandi.

## Superficie di comandi modulare

Il core della CLI non contiene un registro fisso dei comandi di business. All'avvio
legge una o più directory passate tramite `--commands` e carica il modulo
TypeScript selezionato per ogni sezione di comandi. Un modulo esporta una factory
che restituisce un processore; il processore dichiara i propri comandi e instrada
ogni nome di comando verso un gestore.

```text
bun cli <section> <command> [param]
          |          |
          |          +-> command handler
          v
  command module -> processor -> generated NRPC client
```

Questo rende la CLI estensibile senza modificare il suo runtime. Una soluzione o
un prodotto può aggiungere una directory di comandi, e un nuovo modulo
`<section>.ts` diventa una nuova sezione della CLI. Il core carica solo la sezione
richiesta per l'esecuzione, quindi un modulo opzionale o non funzionante non può
impedire l'esecuzione di comandi non correlati.

`BaseCommandProcessor` fornisce la mappa comune dei comandi, l'output della guida,
la propagazione degli errori e un comportamento coerente per l'elenco. I moduli
si concentrano sui propri argomenti e sulle azioni del dominio; il runner gestisce
la configurazione della connessione, il ciclo di vita, la reportistica, la
misurazione dei tempi, lo stato di uscita e la chiusura del canale.

## Un unico modello di autorizzazione

Tutti i moduli di comandi abilitati per NRPC utilizzano la stessa sessione CLI e lo
stesso percorso di autorizzazione. La CLI legge innanzitutto il JWT dell'utente
dal file di sessione locale, quindi ricorre a `SERVICE_TOKEN` quando non è
disponibile alcuna sessione. La sessione utente ha la precedenza perché le azioni
dell'operatore possono richiedere l'identità del chiamante.

Il token viene inviato durante l'handshake WebSocket condiviso di Fujin e viene
anche fornito alla configurazione del client NRPC. Se una sessione memorizzata
viene rifiutata, il runner la rimuove dalla connessione attiva e riprova una volta
con il token di servizio, quando configurato. Gli errori di autenticazione vengono
segnalati in modo uniforme, con l'indicazione di effettuare nuovamente l'accesso,
invece di lasciare ai singoli moduli di comandi la gestione autonoma dello stato
del token.

L'autorizzazione continua a essere applicata dal servizio ricevente. La CLI
trasporta le credenziali del chiamante e l'ambito del workspace; non interpreta i
permessi né concede l'accesso localmente. Un comando può rinunciare al canale
WebSocket solo quando comunica deliberatamente con un endpoint non NRPC, come
un'operazione diagnostica diretta.

## Integrazione NRPC

I moduli di comandi creano client dai pacchetti generati `g-<service>` e passano
loro la configurazione condivisa `createCliNrpcClientConfig`. NRPC serializza la
chiamata al metodo tipizzato in una richiesta WebSocket, indirizzata a una
specifica destinazione logica e a un servizio Fujin. Fujin la inoltra al peer del
runtime attivo e il servizio applica la propria normale policy di accesso prima di
eseguire il metodo.

Lo stesso canale supporta sia i normali metodi richiesta-risposta sia i metodi di
streaming. Gli identificatori delle richieste, le scadenze, l'ordinamento delle
risposte e la gestione dei guasti di connessione sono centralizzati nel canale
CLI, così ogni modulo ottiene lo stesso comportamento senza reimplementare il
codice del protocollo.

## Confine delle responsabilità

La CLI gestisce l'individuazione dei comandi, il ciclo di vita dell'esecuzione dei
comandi, la selezione della sessione locale e il canale client NRPC/WebSocket
comune. Non gestisce la logica di business del dominio, le decisioni sui permessi,
l'implementazione dei servizi né il routing di Fujin. Tali responsabilità
rimangono ai moduli di comandi, ai servizi backend e all'infrastruttura di runtime
che riceve la chiamata.

# SQLite

SQLite è il motore di archiviazione relazionale alla base dei wrapper nativi per i database.
Memorizza un database in un file locale ed esegue SQL nel processo chiamante, consentendo
al servizio Converged di mantenere i propri record, indici e transazioni vicino al codice
che li utilizza.

La stessa connessione SQLite ospita anche tabelle specializzate. Stanchion aggiunge tabelle
virtuali colonnari per le letture analitiche; `sqlite-vec` aggiunge tabelle vettoriali e query
di distanza. Le tabelle ordinarie e queste estensioni possono condividere un database e
partecipare allo stesso flusso di lavoro a livello applicativo.

Questo wrapper costituisce il confine nativo di SQLite: fornisce la libreria e il percorso
per il caricamento delle estensioni utilizzati dall'implementazione dello store di livello
superiore.

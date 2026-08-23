## Processi

Il problema principale di un’officina in crescita raramente è la mancanza di un pulsante in più. Più spesso, i processi vivono nella testa delle persone: chi deve rispondere al cliente, quando calcolare il prezzo, chi controlla il file, quando avviare la produzione, chi avvisare in caso di ritardo e cosa fare dopo la spedizione.

In Converged queste catene sono descritte come workflow. Un processo tipico può andare dalla richiesta alla stima, approvazione, messa in coda, produzione, controllo qualità, pagamento, consegna e notifiche. L’utente di solito non costruisce un grafo da zero: gli scenari pronti vengono forniti con le soluzioni, e la configurazione si riduce a regole, ruoli, scadenze, integrazioni e notifiche.

Tecnicamente, l’esecuzione è spostata nello strato Runtime. Esso esegue workflow, attività cron, passi di integrazione e logica aziendale rimanendo stateless: i dati persistenti restano nei microservizi, e Runtime risponde dell’esecuzione delle catene. Così la logica di business non viene dispersa in decine di servizi e resta un punto chiaro dove vivono le regole di processo.

Per implementazioni complesse, i workflow possono essere estesi. Uno sviluppatore descrive gli scenari come classi TypeScript tipizzate, e gli agenti IA possono lanciare azioni consentite dentro questi scenari. Ma per l’utente comune l’obiettivo è diverso: non costruire un editor, ma attivare un processo pronto e ottenere un risultato gestito.

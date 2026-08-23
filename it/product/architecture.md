## Architettura

Converged è progettato come piattaforma modulare, ma non come una raccolta caotica di microservizi. La separazione è semplice: l’interfaccia mostra dati e avvia azioni, Runtime esegue processi, i microservizi possiedono dati, e gli adattatori collegano attrezzature e sistemi esterni.

```text
Utente / cliente
        ↓
UI e micro-frontends
        ↓
Runtime: workflow, cron, integrazioni, azioni IA
        ↓
Microservizi: API tipizzate e dati propri
        ↓
Storage / Behemoth / file / SQL / KV / metriche
        ↓
Attrezzature, messaggistica, pagamenti e servizi esterni
```

I microservizi restano intenzionalmente sottili. Ogni servizio risponde della propria area dati, della validazione e di un’API tipizzata. Non deve conoscere la logica interna dei servizi vicini e non deve diventare un centro nascosto dei processi aziendali. Questo riduce l’accoppiamento e rende il sistema più semplice da mantenere.

Tutta la logica trasversale viene spostata in Runtime. Se il sistema deve accettare un ordine, interrogare diversi servizi, creare un’attività, inviare una notifica, attendere un evento e aggiornare lo stato, questo viene eseguito in un workflow. Runtime non memorizza stato persistente di per sé: scrive storico, variabili e risultati tramite i servizi che possiedono i propri storage.

Lo storage è costruito intorno all’isolamento. Invece di un database comune, ogni dominio riceve i propri confini dati: SQL, key-value, file, dati colonnari, indici vettoriali o relazioni grafo dove necessario. Questo approccio aiuta a spostare workspace, limitare l’accesso ed evitare un database condiviso in cui si mescolano dati di clienti diversi.

Anche il frontend è modulare. La shell comune carica micro-frontends indipendenti tramite import map, quindi singole aree dell’interfaccia possono evolvere senza ricompilare tutto il prodotto. Per l’utente resta un unico sistema; per lo sviluppo, un insieme di zone di responsabilità chiare.

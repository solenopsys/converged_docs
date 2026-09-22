# Runtime dei workflow di Centimanus

Centimanus esegue i processi in più fasi che collegano moduli Converged altrimenti indipendenti. L'instradamento degli ordini, le notifiche, le approvazioni, le attività assistite dall'IA e le sequenze di produzione possono evolversi come workflow senza spostare l'orchestrazione nei servizi di dominio.

## Esecuzione riproducibile

Un workflow è un programma le cui operazioni significative sono suddivise in nodi denominati. Centimanus esegue un nodo non completato, ne registra il risultato e poi valuta nuovamente il workflow. I nodi completati restituiscono i risultati memorizzati invece di ripetere i loro effetti collaterali.

```text
primo passaggio:   trova ordine -> memorizza risultato
secondo passaggio: riproduci ordine -> prenota macchina -> memorizza risultato
terzo passaggio:   riproduci entrambi -> notifica operatore -> completa
```

I rami e i cicli possono dipendere dai risultati precedenti, quindi il grafo emerge dal processo stesso anziché da un diagramma statico separato. I risultati registrati dei nodi rendono espliciti i progressi e consentono di continuare l'esecuzione dal primo passaggio non completato.

## Perché i workflow sono separati

I microservizi di dominio in Converged possiedono i dati e piccole funzionalità aziendali. Non si chiamano a vicenda per implementare un processo end-to-end. Questo evita catene nascoste in cui una modifica o un errore in un servizio influisce inaspettatamente su molti altri.

Centimanus è il luogo in cui il coordinamento tra domini è visibile. Un workflow può chiamare servizi, richiedere attività all'IA e scegliere il passaggio successivo, mentre ogni servizio rimane concentrato sul proprio ambito.

## Distribuzione dei workflow

Le soluzioni determinano quali workflow sono attivi. Ptah pubblica questa selezione, il servizio DAG espone i descrittori selezionati e Centimanus carica il contenuto corrispondente tramite il proxy content-addressed di Ptah. Un workflow che non fa parte della soluzione attiva non è disponibile per l'esecuzione.

Questo separa quattro aspetti: selezione del prodotto, distribuzione dei contenuti, esecuzione e osservabilità. Ognuno può cambiare senza trasformare il runtime dei workflow in un registro di moduli o in un controller di distribuzione.

## Confine di affidabilità

Centimanus registra i risultati dei nodi completati, ma le operazioni esterne devono comunque rispettare le proprie regole di idempotenza. La telemetria dei workflow viene utilizzata per la visibilità; non determina lo stato di esecuzione. I dati aziendali rimangono nei servizi che ne sono proprietari invece di diventare stato del motore di workflow.

## Ruolo nel sistema

Centimanus riceve il lavoro e chiama i servizi tramite Fujin. Utilizza lo storage della piattaforma per l'avanzamento dei workflow e segnala gli eventi del ciclo di vita per il monitoraggio. Non possiede record di dominio, non seleziona le soluzioni attive e non instrada messaggi tra altri peer.

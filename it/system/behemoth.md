# Archiviazione Behemoth

Behemoth è la base nativa per l'archiviazione di Converged. Fornisce diversi
modelli di dati attraverso un unico runtime compatto, mantenendo al contempo un
confine di archiviazione fisico separato per ogni microservizio.

## Archiviazione per servizi modulari

Ogni servizio di dominio possiede i propri dati. Non condivide tabelle o indici
con servizi non correlati e non deve gestire uno stack di database separato.
Behemoth serve le radici isolate da un processo nativo comune e instrada ogni
richiesta verso l'archivio corretto.

```text
orders service  -> orders volume  -> SQL and files
calls service   -> calls volume   -> key-value and audio fragments
search service  -> search volume  -> vector index
```

La separazione è fisica, non una semplice convenzione di denominazione. Se la
radice di un servizio non è montata e dichiarata, Behemoth rifiuta di creare il
suo archivio. Un errore di distribuzione diventa quindi immediatamente visibile
invece di scrivere dati nel file system temporaneo del container.

## Più modelli di dati

Carichi di lavoro diversi richiedono strutture diverse. Behemoth combina
l'archiviazione relazionale, chiave-valore, a colonne, vettoriale, a grafo e su
file dietro lo stesso confine di runtime. Un servizio sceglie l'archivio più
adatto ai propri dati senza aggiungere alla piattaforma un nuovo prodotto di
database esterno.

I motori rimangono internamente specializzati. Il livello unificato è
responsabile del ciclo di vita, dell'isolamento, del trasporto e dei metadati,
non di fingere che tutti i modelli di dati si comportino allo stesso modo.

## Posizionamento e scalabilità

Il posizionamento dell'archiviazione è indipendente dal codice applicativo. Un'
installazione edge può utilizzare un singolo processo Behemoth. Le distribuzioni
più grandi possono dividere gli ambiti tra diverse istanze, mentre un profilo
cloud può assegnare a ogni tenant la propria istanza di archiviazione.

Ogni microservizio conserva il proprio volume in ogni profilo. Spostare un
ambito o un servizio su un'altra istanza Behemoth modifica la configurazione di
distribuzione, mentre i chiamanti continuano a utilizzare la stessa identità
logica di archiviazione.

## Confini di errore e ripristino

Gli archivi di proprietà dei singoli servizi riducono l'impatto di corruzione,
migrazioni e operazioni di backup. Un problema in un archivio non richiede il
ripristino di un database condiviso per l'intera piattaforma. I dump e il
ripristino possono essere gestiti per il confine del servizio interessato, e i
servizi non correlati continuano a operare.

## Ruolo nel sistema

Le richieste di archiviazione raggiungono Behemoth tramite Fujin, come le
richieste verso qualsiasi altro peer di runtime. Ptah fornisce il layout dei
volumi e la configurazione dei mount. Behemoth esegue le operazioni di
archiviazione, ma non coordina i flussi di lavoro aziendali, non seleziona i
tenant e non definisce quali servizi compongano una soluzione.

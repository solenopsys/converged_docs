## Architettura

Converged è costruito come un ambiente di esecuzione modulare in cui l'interfaccia, la logica di business e l'infrastruttura sono separate pur operando come un unico sistema.

A livello utente, il sistema è costituito da **Superfici**, che organizzano il contesto di lavoro, e **Proiezioni** — singole schermate progettate per risolvere attività specifiche degli utenti.

La logica di business è implementata in **TypeScript** attraverso diversi tipi di **Servizi**: Repository, Lambda e Runtime. I processi più complessi vengono assemblati in **Workflow**, eseguiti tramite il motore di elaborazione DAG Centimanus.

Alla base del sistema ci sono le **App**. Sono ambienti di esecuzione dell'infrastruttura con un compatto core in Zig, nel quale vengono eseguiti script TypeScript. Le App forniscono le funzionalità fondamentali su cui operano Servizi, Workflow e interfaccia utente.

```text
Utente
  ↓
Superfici
  └── Proiezioni
        ↓
Servizi — TypeScript
  ├── Repository
  ├── Lambda
  └── Runtime
        ↓
Workflow
        ↓
App — Zig + TypeScript
  ├── Fujin
  ├── Centimanus
  ├── Resonus
  ├── Behemoth
  ├── Ptah
  └── Cruller
        ↓
Kubernetes
  ↓
Edge / Server / Cluster
```

### Superfici e Proiezioni

Una **Superficie** è uno spazio di lavoro dell'utente organizzato attorno a uno specifico contesto operativo. Riunisce i dati, le azioni e le viste necessari per lavorare in una determinata area.

Una Superficie non deve necessariamente corrispondere a un singolo Servizio. Può combinare dati e azioni provenienti da più Repository, Lambda, Runtime e Workflow.

Una **Proiezione** è una singola schermata all'interno di una Superficie, progettata per svolgere una funzione specifica. Presenta i dati in una forma comoda per l'utente e fornisce le azioni necessarie.

L'interfaccia è quindi organizzata attorno a **ciò con cui l'utente sta lavorando**, anziché attorno alla struttura interna dei Servizi.

### Servizi

La logica di business di Converged è scritta in TypeScript e suddivisa in diversi tipi di Servizi.

I **Repository** incapsulano l'accesso ai dati. Forniscono un'interfaccia per leggere, modificare e interrogare i dati, nascondendo il meccanismo di archiviazione sottostante.

Le **Lambda** sono funzioni senza stato progettate per singole operazioni, come elaborazione e trasformazione dei dati, calcolo, convalida o utilizzo come gateway verso API esterne.

I **Runtime** forniscono ambienti di esecuzione specializzati per la logica che richiede un proprio contesto di esecuzione.

I Servizi sono i blocchi costitutivi del sistema. Non devono conoscere i processi di business nei quali verranno utilizzati e possono essere riutilizzati da Superfici e Workflow diversi.

### Workflow

Un **Workflow** combina i Servizi in un processo di business completo.

Invece di collegare i Servizi tramite chiamate dirette, un Workflow definisce quali operazioni devono essere eseguite, in quale ordine, quali passaggi possono essere eseguiti in parallelo, dove il sistema deve attendere un evento e cosa deve accadere quando un'operazione fallisce.

Ad esempio:

```text
Ordine
  ↓
Pagamento
  ↓
Slicing
  ↓
Produzione
  ↓
Consegna
```

Un Workflow può utilizzare Repository per le operazioni sui dati, Lambda per singole operazioni e Runtime o App per attività specializzate.

### Centimanus

**Centimanus è il motore DAG che esegue i Workflow.**

Un Workflow è rappresentato come un grafo di operazioni, mentre Centimanus ne gestisce l'esecuzione: dipendenze tra i passaggi, nuovi tentativi, attesa di eventi, operazioni parallele e compensazione in caso di errore.

Ogni esecuzione produce una traccia di audit che mostra cosa è stato avviato, cosa è stato completato, quali operazioni sono state ripetute e perché si è verificato un errore.

Questo permette di creare processi resilienti e di lunga durata che preservano lo stato di esecuzione e possono proseguire dopo un riavvio.

I Servizi rimangono indipendenti perché non devono essere collegati tramite catene di chiamate dirette per implementare un determinato processo di business.

### App

**Le App sono la base dell'infrastruttura di Converged.**

Un'App è un ambiente di esecuzione virtuale leggero. Il suo core di sistema è scritto in **Zig**, mentre la logica mutabile viene eseguita come **script TypeScript**.

Questa separazione mantiene l'infrastruttura critica in un core compatto e ad alte prestazioni, conservando al contempo la flessibilità di TypeScript per la logica applicativa e la configurazione.

Le App forniscono le funzionalità infrastrutturali utilizzate dal resto del sistema:

* **Fujin** — fabric di comunicazione per comandi, eventi, WebSocket e telemetria delle macchine.
* **Centimanus** — elaborazione DAG ed esecuzione dei Workflow.
* **Resonus** — gateway realtime per voce, media, trascrizione e provider AI.
* **Behemoth** — sistema multi-storage isolato per diversi tipi di dati.
* **Ptah** — gestione del deployment e della topologia Kubernetes.
* **Cruller** — runtime in cui vengono eseguiti i moduli UI e TypeScript.

Le App non costituiscono un ulteriore livello di logica di business. Forniscono le **infrastrutture e gli ambienti di esecuzione** in cui opera il livello TypeScript.

### Fujin

**Fujin è il fabric unificato per comandi, eventi e telemetria.**

Tutti i componenti del sistema comunicano tramite Fujin invece di effettuare chiamate dirette tra loro. Un comando proveniente dall'interfaccia utente, un evento di un Workflow, una lettura di un sensore della macchina o un aggiornamento sullo stato di avanzamento della produzione passano tutti attraverso lo stesso livello di comunicazione.

I WebSocket trasmettono le modifiche all'interfaccia in tempo reale senza polling.

Poiché la comunicazione passa attraverso un unico livello, può essere tracciata centralmente, riprodotta e soggetta a limitazione della frequenza.

**Risultato:** i Servizi rimangono indipendenti, il realtime diventa parte dell'infrastruttura comune e gli eventi di sistema diventano osservabili.

### Resonus

**Resonus è un'interfaccia realtime unificata per voce, media e AI.**

Combina telefonate, flussi audio, trascrizione e adattatori per provider AI all'interno di un unico livello.

Una conversazione può passare da una telefonata alla trascrizione e poi all'analisi AI senza transitare tra sistemi separati. I media possono essere associati direttamente a ordini, apparecchiature ed eventi.

Gli adattatori dei provider isolano il sistema dai singoli fornitori di servizi vocali e AI.

**Risultato:** voce, media e AI diventano parte dell'ambiente comune dei Workflow, mentre i provider possono essere sostituiti senza ristrutturare la logica applicativa.

### Behemoth

**Behemoth è il sistema multi-storage unificato per i dati di Converged.**

Ai diversi tipi di dati viene fornito uno storage appropriato: SQL per ordini e clienti, file per modelli e documenti, vettori per la ricerca AI, cache per lo stato caldo e altri tipi di storage specializzati quando necessario.

L'isolamento è strutturale: i dati provenienti da workspace diversi non vengono mescolati e possono essere scalati, sottoposti a backup e spostati indipendentemente.

Lo stesso modello funziona nei deployment Edge, Server e Cluster. Su un piccolo dispositivo Edge, tutti i domini di storage possono risiedere su un singolo nodo; in un Cluster, possono essere distribuiti su hardware di storage specializzato.

**Risultato:** i dati sono isolati per costruzione, mentre l'infrastruttura di storage può crescere insieme all'installazione senza modificare il livello applicativo.

### Ptah

**Ptah è l'orchestratore di deployment di Converged basato su Kubernetes.**

Gestisce il posizionamento di App, container e dati in base alla topologia di deployment: Edge, Server o Cluster.

Il core di Ptah è scritto in Zig, mentre le regole di gestione sono implementate come script TypeScript. Questo permette di modificare la logica di posizionamento, ordine di rilascio, failover e distribuzione dei dati senza ricostruire il core.

Lo stesso meccanismo viene utilizzato per diversi tipi di installazione — da un singolo nodo Edge a un cluster distribuito.

**Risultato:** l'intero sistema viene gestito tramite un livello di deployment unificato, mentre la logica di deployment rimane dinamica e modificabile.

### Cruller

**Cruller è il runtime per l'interfaccia utente e i moduli TypeScript.**

Fornisce l'ambiente in cui viene eseguita la logica TypeScript di Converged, inclusi l'interfaccia utente e i moduli applicativi.

Cruller collega il livello dinamico TypeScript alle funzionalità infrastrutturali fornite dalle App, permettendo al livello applicativo di evolversi senza modificare il core di basso livello.

### Kubernetes e topologia

Tutte le App e i componenti correlati vengono distribuiti tramite **Kubernetes**.

Converged utilizza lo stesso modello architetturale indipendentemente dalla dimensione dell'installazione:

```text
Edge
  → nodo singolo

Server
  → singolo server con maggiori risorse

Cluster
  → più nodi e storage distribuito
```

La topologia fisica cambia, ma il modello applicativo no. Servizi, Workflow, Superfici e Proiezioni operano allo stesso modo sia quando il sistema è in esecuzione su un dispositivo Edge sia quando opera su un cluster completo.

### Modello unificato

Le diverse parti di Converged sono organizzate attorno a responsabilità differenti:

**Superficie** — contesto di lavoro dell'utente.
**Proiezione** — una funzione specifica e la sua rappresentazione visiva.
**Repository** — accesso ai dati.
**Lambda** — un'operazione individuale senza stato.
**Runtime** — un ambiente di esecuzione specializzato.
**Workflow** — un processo di business che combina i Servizi.
**App** — ambienti di esecuzione dell'infrastruttura con un core Zig e TypeScript al loro interno.
**Fujin** — comunicazione ed eventi.
**Centimanus** — esecuzione dei Workflow.
**Resonus** — voce, media e AI realtime.
**Behemoth** — storage.
**Ptah** — deployment e gestione di Kubernetes.
**Cruller** — ambiente di esecuzione per UI e TypeScript.

Il principio centrale di Converged è **separare il contesto dell'utente, la logica applicativa e l'infrastruttura senza costringerli nella stessa struttura**.

Una Superficie può combinare più Servizi. Un Workflow può combinare più operazioni. E più Workflow e Servizi possono utilizzare le stesse App sottostanti.

Il risultato è un sistema che rimane modulare a livello di logica di business, compatto a livello infrastrutturale e unificato dal punto di vista dell'utente.
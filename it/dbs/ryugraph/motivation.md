## Perché l'archiviazione a grafo è adatta agli agenti IA

Il valore di un database a grafo in un sistema basato innanzitutto sull'IA non si limita a una traversata più rapida delle relazioni. Il suo vantaggio più importante è che un grafo rappresenta le informazioni in una forma che è naturalmente comoda da comprendere ed esplorare per un agente LLM.

Un database relazionale è costruito attorno a tabelle, colonne, chiavi esterne e join predefiniti. Questo funziona molto bene quando la struttura della query è nota in anticipo. Un agente, tuttavia, spesso lavora in modo diverso. Può iniziare con una richiesta incompleta, trovare un oggetto rilevante, esaminarne l'ambiente, seguire una relazione utile e continuare finché non ha raccolto abbastanza contesto.

Un grafo supporta direttamente questo stile.

Ad esempio, un'azienda di produzione può avere oggetti come un'azienda, un dipendente, un thread di email, un allegato, un componente, un materiale, una RFQ, un'offerta, un ordine e una macchina. Questi oggetti possono essere collegati tramite relazioni significative:

```text
John Smith → WORKS_AT → Acme CNC
Message → SENT_BY → John Smith
Message → HAS_FILE → housing_revC.step
housing_revC.step → REVISION_OF → Housing
RFQ → REQUESTS → Housing
Quote → ANSWERS → RFQ
Order → BASED_ON → Quote
```

Per un LLM, questa struttura è già informativa. `Acme CNC`, `Housing`, `REVISION_OF`, `SENT_BY` e `BASED_ON` non sono chiavi di database opache. I loro nomi hanno un significato semantico. Il grafo agisce quindi non solo come archivio, ma anche come descrizione compatta del dominio aziendale.

Questo cambia il modo in cui l'agente può lavorare.

Supponiamo che un utente chieda:

> Trova ciò che voleva il cliente in quell'ordine di alloggiamenti di Acme.

L'agente non deve costruire immediatamente una query molto grande. Può prima trovare `Acme CNC`, esaminare gli ordini collegati, identificare l'ordine pertinente relativo agli alloggiamenti, esaminarne i thread e solo dopo recuperare i pochi messaggi che contano.

Un'esplorazione tipica può essere simile a questa:

```text
Acme CNC
  ↓
Orders
  ↓
Housing Order
  ↓
Threads
  ↓
Messages
  ↓
Attachments
```

A ogni passaggio l'agente riceve solo una piccola vista locale del grafo. Ad esempio:

```json
{
  "id": "order_551",
  "type": "Order",
  "name": "Housing batch",
  "relations": {
    "CUSTOMER": 1,
    "THREAD": 3,
    "FILE": 11,
    "PART": 2,
    "QUOTE": 2
  }
}
```

Questo è sufficiente perché il modello comprenda il tipo di oggetto che sta esaminando e quale direzione sia utile esplorare successivamente.

La conseguenza importante è che l'agente non ha bisogno dell'intero schema del database nel proprio contesto. Non deve ricordare decine di tabelle, chiavi esterne, tabelle di collegamento o espressioni SQL ricorsive. Gli servono solo un oggetto corrente e una piccola descrizione delle sue relazioni locali.

Questo rende l'esplorazione ricorsiva economica e robusta.

Non è nemmeno necessario memorizzare i contenuti di grandi dimensioni all'interno del grafo. I corpi delle email, i file PDF, i modelli CAD, le immagini e altri oggetti pesanti possono rimanere in KVS o nell'object storage. Il grafo conserva solo metadati compatti, identificatori degli oggetti, chiavi di archiviazione e relazioni.

L'architettura separa quindi la struttura dal contenuto:

```text
Graph
    → objects, relationships, metadata, storage keys

KVS / Object Storage
    → email bodies, PDF, STEP, STL, DXF, images

LLM Agent
    → explores the graph first
    → retrieves heavy content only when necessary
```

Questo è particolarmente importante quando si lavora con molti anni di storia aziendale. Centinaia di gigabyte di email e allegati possono essere rappresentati da un grafo molto più piccolo contenente aziende, persone, thread, file, ordini, componenti e le relative relazioni.

L'agente può eseguire dieci o venti piccole operazioni sul grafo consumando solo pochi kilobyte di contesto strutturato. Al termine di questa esplorazione potrebbe già sapere quale azienda è coinvolta, quali ordini sono pertinenti, quali persone hanno partecipato, quali file appartengono al caso e dove si trovano le conversazioni importanti. Solo a quel punto carica i corpi effettivi dei messaggi o i file necessari per rispondere alla domanda.

Il grafo è inoltre naturalmente estensibile. Un sistema può inizialmente contenere solo `Company`, `Person`, `Message`, `File` e `Order`. In seguito può includere `Part`, `Revision`, `Material`, `Machine`, `Job`, `Supplier` o `Contract`, insieme a nuove relazioni come `REVISION_OF`, `USES_MATERIAL`, `MANUFACTURED_ON` o `SUPPLIED_BY`.

L'interfaccia dell'agente non deve cambiare fondamentalmente. Può continuare a utilizzare lo stesso piccolo insieme di operazioni:

```text
find
inspect
follow
expand
search
fetch
```

Questa è una differenza importante rispetto a un sistema in cui ogni nuova relazione aziendale finisce per creare un ulteriore insieme di join SQL, metodi API e logica specifica per le query.

Un esempio pratico illustra bene il vantaggio.

L'utente chiede:

> Trova il contratto dell'azienda per cui abbiamo stampato componenti in nylon l'anno scorso.

L'utente non ricorda il nome dell'azienda, il numero dell'ordine, l'oggetto dell'email o il nome del file.

L'agente può partire dal concetto che conosce:

```text
Nylon
  ↓
Jobs
  ↓
Orders
  ↓
Companies
  ↓
Documents
  ↓
Contract
```

Un'altra richiesta potrebbe essere:

> Trova il file CAD che il cliente ha inviato prima che ricalcolassimo l'offerta.

Anche in questo caso, l'agente può navigare attraverso le relazioni e la cronologia finché non trova l'allegato pertinente, senza richiedere all'utente di sapere come sono organizzati i dati sottostanti.

Questa è la ragione architetturale principale per utilizzare un grafo con un agente LLM.

Il grafo non è semplicemente un sostituto più veloce dei join SQL. È una rappresentazione semantica compatta del dominio che il modello può leggere, comprendere ed esplorare in modo incrementale.

In questa architettura, il grafo diventa memoria strutturale, l'object storage contiene i contenuti pesanti e l'LLM diventa l'esploratore semantico che si muove attraverso la struttura.

Il principio fondamentale è semplice:

> **Il grafo è un modello di dati nativo per gli agenti.**

Fornisce all'agente una forma di dati compatta, significativa, espandibile e naturalmente adatta all'esplorazione ricorsiva.

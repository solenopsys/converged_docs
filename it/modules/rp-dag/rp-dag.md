# rp-dag

## Scopo

Gestisce i trigger dei workflow e il log di esecuzione. Non esegue nulla.

## Confine di responsabilità

Qui appartengono due cose e nient'altro:

- **Trigger** — "quando appare questo topic del bus, esegui quel workflow". Configurazione di sistema: decine di righe gestite da un operatore, mantenute per intero nella memoria del runtime invece di essere interrogate.
- **Il log di esecuzione** — un albero di ciò che ha fatto un'esecuzione. Il runtime lo scrive mentre lo script è in esecuzione: un nodo viene aperto prima dell'esecuzione del suo corpo e chiuso quando termina, così un'esecuzione in corso mostra il nodo su cui si trova.

Il catalogo dei workflow non è gestito qui. Ptah inserisce i descrittori della Solution attiva nell'ambiente di questo servizio (`WORKFLOWS`, `WORKFLOW_DIGESTS`,
`MODULE_PROXY`) e `listAvailableWorkflows` li ripubblica per il runtime e l'interfaccia utente. I byte sorgente restano dietro Ptah-proxy.

## Il log viene scritto dal runtime, non da questo servizio

Qui non viene scritta alcuna voce di log. Il runtime la formatta, la inserisce in Valkey sotto una chiave che compone autonomamente e in seguito trasferisce le chiavi — mai le voci.
`commitLog` trasforma ogni chiave in una posizione dello store e indica allo storage di prelevare la voce; lo storage legge direttamente dalla cache, quindi una voce attraversa il trasporto una sola volta, come byte che nessuno ricodifica.

```text
thread del workflow ─► coda ─► scrittore del log ─► valkey
                                             │
                                             └─ commitLog([keys]) ─► rp-dag ─► lo storage legge valkey
                                                                                  │
                                             ◄──── committed ─────────────────────┘
                                             └─ elimina le chiavi sottoposte a commit
```

È questo che mantiene la registrazione fuori dal percorso critico del workflow: un nodo costa al runtime un'aggiunta alla coda e nient'altro. Significa anche che il log è intrinsecamente best effort — una voce può essere eliminata sotto pressione e un batch può essere sottoposto a commit due volte dopo un arresto anomalo. Le chiavi derivano dall'esecuzione e dalla sequenza del nodo, quindi il secondo commit è una riscrittura anziché un duplicato.

Le chiavi provengono dal runtime proprio per questo motivo: un numero assegnato da questo servizio costerebbe un round trip per nodo e non sarebbe riproducibile dopo un riavvio.

- `dag:log:<executionId>:exec` — l'esecuzione
- `dag:log:<executionId>:n:<seq>` — uno dei suoi nodi, con il numero completato con zeri fino a sei cifre

`commitLog` ricava la posizione dello store dalla chiave e rifiuta qualsiasi elemento al di fuori del prefisso `dag:log:`, quindi una chiave costituisce l'intera autorità trasportata dalla chiamata.

## Il log è un albero

```text
exec:<id>              l'esecuzione
node:<id>:<seq>        i suoi nodi, nell'ordine in cui sono stati aperti
```

Un nodo che ha delegato tramite `rt.sub` contiene l'id dell'esecuzione figlia, e la figlia è un'esecuzione ordinaria con nodi propri. `executionTree` segue quel collegamento in profondità e restituisce il risultato in forma piatta, con ogni riga contrassegnata dal proprio `depth` — così un client visualizza l'albero applicando un'indentazione e nient'altro. Non è necessario alcun indice del genitore: il collegamento è il nodo che lo ha creato.

Le sequenze sono completate con zeri nella chiave, perché il KV store restituisce un intervallo di prefisso in ordine lessicografico e tale ordine deve corrispondere all'ordine in cui sono stati eseguiti i nodi. Il runtime usa la stessa larghezza quando compone la chiave della cache; le due larghezze costituiscono un unico contratto.

La conservazione è un limite sul numero di esecuzioni (`5000` per impostazione predefinita), applicato ogni cento aperture. Il log è diagnostico, non un archivio.

## Le modifiche ai trigger raggiungono il runtime tramite il bus

La creazione, la modifica o l'eliminazione di un trigger pubblica `dag.triggers.changed`. Il runtime si iscrive a quel topic oltre che a quello specifico dei trigger, quindi una modifica è attiva per l'evento successivo invece di attendere la fine di un intervallo di polling. La pubblicazione è best effort — un bus non disponibile non deve far fallire la modifica di un operatore — e l'aggiornamento periodico del runtime rimane il meccanismo di sicurezza.

## Dipendenze dirette dal modulo

- g-bus — per annunciare una modifica ai trigger

## Appartenenza alla Solution

- Non incluso in una Solution predefinita

## Sorgente

`modules/repositories/automation/rp-dag`

# Automazione

## Scopo

Gestisce l'area di lavoro dell'automazione: i workflow e le relative esecuzioni, i trigger del bus che li avviano, le pianificazioni ricorrenti e gli endpoint webhook in ingresso.

## Confine delle responsabilità

Controlla l'esperienza dell'area di lavoro. Non esegue i workflow, non conserva le pianificazioni né consegna i webhook: avvia un'esecuzione tramite il runtime e legge il log da rp-dag.

## La sezione DAG

- **Workflow** — il catalogo pubblicato dalla Solution attiva, in sola lettura.
  Aprirne uno significa chiedere di eseguirlo: i parametri sono tipizzati come JSON e passati a
  `centimanus.runWorkflow`.
- **Esecuzioni** — ogni esecuzione, con il relativo stato.
- **Dettagli dell'esecuzione** — l'albero di ciò che l'esecuzione ha fatto. Una riga per nodo: a quale profondità si trova, se è terminato, quanto tempo ha impiegato. Espandendo un nodo vengono mostrate le
  chiamate ai servizi effettuate e ciò che è stato restituito. Un nodo che ha delegato tramite
  `rt.sub` è seguito dai nodi dell'esecuzione a cui ha delegato, un livello più in profondità.
  Un'esecuzione ancora in corso si aggiorna automaticamente.
- **Trigger** — "quando compare questo argomento del bus, esegui quel workflow". Argomento,
  workflow, parametri JSON, attivato/disattivato.
- **Variabili** — lo stato del workflow scritto da `rt.set`.

I parametri sono tipizzati come JSON ovunque anziché essere generati in un modulo: i parametri di un workflow sono propri e cambiano insieme a esso, quindi un campo di testo rimane corretto quando cambiano e ciò che viene digitato è ciò che il workflow riceve.

## Dipendenze dirette del modulo

- Nessuna

## Appartenenza alla Solution

- Non incluso in una Solution predefinita

## Sorgente

`modules/surfaces/automation/sf-automation`

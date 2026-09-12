# Piano di controllo di Ptah

Ptah trasforma una descrizione della piattaforma Converged in risorse Kubernetes in esecuzione.
È il piano di controllo del sistema: decide cosa dovrebbe esistere per una piattaforma,
quali soluzioni sono attive e come vengono collocati i carichi di lavoro dei tenant e lo storage.

## Modello desiderato della piattaforma

Il modello di distribuzione ha tre livelli:

| Risorsa | Significato |
| --- | --- |
| Piattaforma | Runtime condiviso, instradamento, profilo di storage, applicazioni e mappa dei moduli. |
| Soluzione | Un insieme di moduli aziendali, workflow e processori aggiunti a una piattaforma. |
| Tenant | Un sito isolato con il proprio ambito, le proprie route e, quando necessario, il proprio shard di storage. |

Ptah osserva queste risorse e produce l'insieme completo desiderato di
deployment, servizi, volumi, configurazione e route. Kubernetes quindi
porta il cluster a convergere su tale descrizione.

```text
Piattaforma + Soluzione + Tenant
              |
              v
             Ptah
              |
              v
Carichi di lavoro, storage e route Kubernetes
```

## Policy e meccanismo

Ptah separa i meccanismi del cluster dalla policy del prodotto. Il controller nativo
osserva Kubernetes, applica le risorse, registra lo stato e rimuove gli oggetti obsoleti. Un livello di policy puro converte i dati osservati della piattaforma in un risultato desiderato senza effettuare chiamate di rete o modificare direttamente il cluster.

La stessa policy può quindi essere valutata prima della distribuzione. Questo rende
ispezionabili le decisioni di posizionamento e del ciclo di vita senza riprodurle in un
secondo generatore di configurazione.

## Profili di distribuzione

I profili modificano il posizionamento dello storage senza cambiare le immagini delle applicazioni:

- `mono` esegue una singola istanza di storage per una piattaforma compatta;
- `multi` divide gli ambiti tra gli shard di storage;
- `cloud` assegna a ogni tenant un'istanza di storage isolata e un confine di route.

La regola di assegnazione dei volumi rimane la stessa in ogni profilo: ogni microservizio
ha il proprio volume di storage. Ptah decide quale istanza Behemoth monta quei
volumi e pubblica la mappatura ambito-storage utilizzata dai carichi di lavoro stateless.

## Moduli e rollout

Le soluzioni identificano i moduli invece di incorporarne i byte. Ptah distribuisce una
mappa dei moduli indirizzata al contenuto e fornisce contenuti immutabili dei moduli tramite una
cache condivisa. I consumer ricevono l'esatto digest che devono caricare.

Quando il digest selezionato cambia, cambia con esso la descrizione del carico di lavoro e
Kubernetes esegue il rollout. Un pod in esecuzione registra quindi il contenuto preciso del modulo con cui è stato avviato, e il rollback consiste nel selezionare nuovamente il
digest precedente.

## Riconciliazione sicura

Ptah applica un insieme completo desiderato ed elimina le risorse che non ne fanno più parte.
Le risorse che contengono dati vengono mantenute a meno che la loro eliminazione non sia
richiesta esplicitamente. Un input incompleto o un errore di policy sopprime l'eliminazione,
impedendo che un problema temporaneo di dipendenze venga interpretato come una richiesta di rimuovere
la piattaforma.

## Posto nel sistema

Ptah non è un peer sul bus di messaggistica Fujin e non elabora il traffico aziendale. Crea e configura i peer, lo storage e le route che costituiscono il runtime. Una volta in esecuzione, Fujin, Behemoth, Centimanus e Resonus svolgono il proprio lavoro indipendentemente dal piano di controllo.

# Architettura del sistema

Converged è un livello operativo modulare per le aziende manifatturiere. Le sue
interfacce utente, i servizi di dominio, il motore dei workflow, lo storage, il
gateway multimediale e i processori industriali formano un unico sistema senza
diventare un'unica applicazione.

L'architettura separa tre tipi di lavoro:

- i moduli di dominio possiedono i dati aziendali e le funzionalità rivolte agli utenti;
- i servizi runtime nativi spostano messaggi, eseguono workflow, archiviano dati e gestiscono i media in tempo reale;
- il control plane decide quali parti vengono eseguite per ogni piattaforma e tenant.

## Un unico bus di messaggi

I componenti runtime comunicano tramite Fujin. Ogni processo apre una
connessione, registra una destinazione e invia messaggi a destinazioni logiche.
Il mittente non ha bisogno dell'indirizzo o della posizione di distribuzione del
ricevente.

```text
browser and mobile clients
          |
          v
          Fujin message bus
       /     |      |      \
      ui     ms  Centimanus Resonus
              \      |      /
               \  Behemoth /
```

Questo rimuove il grafo delle chiamate HTTP e la service mesh dal livello applicativo.
Il routing, la correlazione delle richieste e il contesto tenant attendibile viaggiano
nell'inviluppo comune dei messaggi. Un processo ricevente seleziona quindi il
servizio o l'handler richiesto all'interno del proprio confine.

## Runtime principale

| Componente | Responsabilità |
| --- | --- |
| Fujin | Connette i peer runtime e instrada i messaggi verso il proprietario attivo di una destinazione. |
| Behemoth | Fornisce storage SQL, key-value, a colonne, vettoriale, a grafo e su file isolati. |
| Centimanus | Esegue workflow aziendali a più passaggi come grafi riproducibili. |
| Resonus | Gestisce media in tempo reale, chiamate, trascrizione e sessioni AI. |
| Ptah | Riconcilia la piattaforma, le soluzioni e i tenant desiderati con le risorse Kubernetes. |

I componenti sono volutamente ristretti. Fujin non comprende i servizi aziendali.
Behemoth non orchestra le operazioni aziendali. Centimanus non possiede i dati
di dominio. Resonus non decide l'identità del tenant. Ptah crea e configura i
workload, ma non partecipa alla messaggistica runtime.

## Moduli e soluzioni

Le funzionalità aziendali vengono fornite come microservizi, superfici e
workflow. Una soluzione è una selezione dichiarativa di questi moduli per uno
specifico scenario operativo, come la gestione degli ordini, la pianificazione
della produzione o il monitoraggio delle apparecchiature.

I microservizi possiedono i propri dati ed espongono contratti tipizzati. Non si
chiamano tra loro per coordinare un processo. Le sequenze tra domini appartengono
ai workflow, che Centimanus esegue un passaggio durevole alla volta. In questo
modo i moduli di dominio rimangono piccoli e una soluzione può combinarli senza
creare accoppiamenti nascosti.

## Isolamento dei dati

Ogni microservizio ha la propria radice fisica di storage. Behemoth può servire
molte radici da un unico processo, ma ne preserva i confini di proprietà e rifiuta
di creare dati al di fuori dei mount configurati.

Lo stesso modello si estende ai diversi profili di distribuzione:

- un'installazione edge può eseguire un'unica istanza di Behemoth per la piattaforma;
- un'installazione più grande può dividere gli ambiti tra shard di storage;
- un'installazione cloud può eseguire un'istanza di storage isolata per tenant.

Cambiare la topologia non modifica il codice applicativo, perché i peer continuano
a indirizzare destinazioni logiche e confini di storage.

## Control plane

Ptah è il control plane e non è connesso a Fujin. Osserva le risorse Platform,
Solution e Tenant dichiarate, calcola i workload desiderati e li riconcilia con
Kubernetes.

```text
Platform + Solutions + Tenants
              |
              v
             Ptah
              |
              v
Deployments, Services, volumes, configuration and routes
```

Questa separazione permette al runtime di concentrarsi sul traffico aziendale,
mentre il modello di distribuzione gestisce posizionamento, topologia dello
storage, route dei tenant e ciclo di vita. Le stesse immagini applicative possono
quindi essere eseguite su un cluster edge compatto o in un ambiente cloud
multi-tenant.

## Contesto attendibile

L'ambito del tenant viene stabilito al bordo della piattaforma e trasportato
nell'inviluppo del messaggio. I servizi runtime consumano questo contesto
attendibile invece di derivare un tenant dai payload applicativi. Il posizionamento
dello storage, le chiamate ai servizi e le sessioni multimediali preservano tutti
lo stesso confine di ambito.

Nel loro insieme, messaggistica logica, storage isolato, workflow riproducibili e
un control plane separato permettono a Converged di rimanere modulare senza
trasferire la complessità dei sistemi distribuiti a ogni modulo aziendale.

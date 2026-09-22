# Runtime del contratto NRPC

NRPC è il livello di chiamate remote tipizzate di Converged. Trasforma un contratto
 di servizio TypeScript in client corrispondenti e metadati del servizio, così che
un browser, un microservizio, un workflow o un runtime nativo possano chiamare
la stessa funzionalità senza mantenere definizioni API separate basate su stringhe.

## Perché esiste

La piattaforma è composta da moduli distribuiti indipendentemente. Chiamare
 direttamente un modulo tramite un indirizzo farebbe dipendere i chiamanti da dove
viene eseguito e dal trasporto utilizzato. NRPC separa queste responsabilità: un
contratto identifica il servizio e i suoi metodi, mentre il runtime recapita una
chiamata al processo che attualmente gestisce la destinazione richiesta.

Questo mantiene l'accordo tra chiamanti e implementazioni in un unico luogo. I
parametri di un metodo, il tipo restituito, il comportamento di streaming e il
livello di accesso sono noti alla generazione del codice e disponibili per ogni
client supportato.

## Dal contratto alla chiamata

I contratti sono interfacce TypeScript nella directory `modules/types/<domain>`. Eseguendo
`bun run gen` in `core/tools/nrpc`, queste interfacce vengono analizzate e viene
creato un pacchetto `modules/generated/g-<service>`. Il pacchetto contiene i metadati
del contratto, un'interfaccia server e factory di client sicure rispetto ai tipi per
ogni runtime.

```text
TypeScript interface
        |
        v
NRPC generator -> g-<service> package
        |                    |
        |                    +-> browser client
        |                    +-> cluster client
        |                    +-> workflow RT client
        v
service implementation -> messaging backend
```

Un servizio registra la propria implementazione con `createMessagingBackend`. NRPC
usa i metadati generati per trovare il metodo richiesto, convalida la struttura
della chiamata al confine del client, ripristina i valori tipizzati e invoca il
metodo corrispondente dell'implementazione. Un metodo che restituisce `AsyncIterable`
viene consegnato come stream; i metodi ordinari producono una sola risposta.

## Percorsi di consegna

NRPC conserva lo stesso contratto in diversi ambienti di esecuzione:

- I client browser usano un canale WebSocket condiviso per inviare richieste a Fujin.
- I client di servizio e nativi usano il trasporto del cluster tramite Fujin, indirizzati
  a una destinazione di processo logica anziché a un indirizzo host.
- I client dei workflow usano l'entry point RT, che effettua la chiamata tramite il
  trasporto host QuickJS/Zig e rimane sincrono per una singola valutazione del workflow.

Fujin instrada una richiesta verso la connessione di destinazione. Il processo
ricevente sceglie il servizio e il metodo NRPC dai metadati della richiesta; Fujin
non deve comprendere i servizi di dominio della piattaforma. `createHttpBackend` è
disponibile quando è richiesto un edge HTTP e può registrare la stessa implementazione
del servizio sul runtime di messaggistica, mantenendo allineate le chiamate HTTP e
quelle interne.

## Contesto e accesso

Le chiamate trasportano nell'inviluppo dati di correlazione, scadenze e un contesto
attendibile di workspace o ambito. Il servizio ricevente viene eseguito con quel
contesto, consentendo al codice di storage e autorizzazione di usare lo stesso
confine del tenant stabilito all'edge. I servizi non devono ricavare l'identità del
workspace da un payload di business.

Il decoratore `@Access` dichiara una classe o un metodo come `public`, `user` o
`internal`. NRPC risolve il livello dichiarato più specifico e applica le regole di
permesso configurate prima di invocare l'implementazione. In questo modo la policy
di accesso diventa parte del confine del servizio anziché una convenzione incoerente
del client.

## Confine delle responsabilità

NRPC gestisce i metadati dei contratti, i client tipizzati generati, la serializzazione
dei valori, l'instradamento delle chiamate e gli adattatori di trasporto utilizzati
da tali chiamate. Non gestisce le regole di business, l'individuazione dei servizi,
il posizionamento delle distribuzioni, la persistenza del dominio o l'instradamento
del message bus. Queste responsabilità rimangono rispettivamente al servizio, al
piano di controllo della distribuzione, al livello di storage e a Fujin.

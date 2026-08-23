## Tecnologie

La parte server di Converged è costruita su **Bun** ed **Elysia**. Bun avvia rapidamente JavaScript e TypeScript, usa la memoria in modo efficiente ed è adatto a deployment edge compatti. Elysia viene usato come strato HTTP per plugin backend e microservizi.

I contratti tra servizi sono descritti con tipi. NRPC collega interfacce TypeScript alle implementazioni e genera pacchetti client, così frontend, Runtime e backend lavorano con gli stessi contratti invece che con API testuali scollegate.

Lo storage dei dati usa un insieme di store leggeri per compiti diversi: SQL, key-value, file, dati colonnari, indici vettoriali e relazioni grafo. Lo strato nativo Behemoth e gli adattatori Zig coprono i casi in cui contano basso overhead, accesso alle attrezzature, Unix socket o FFI.

Il frontend è una piattaforma React con micro-frontends. La shell comune carica moduli UI separati, e gli scenari di prodotto possono evolvere indipendentemente. Questo è importante per una piattaforma con molte soluzioni: l’interfaccia non deve trasformarsi in un monolite pesante.

Orchestrazione e consegna sono costruite intorno a k3s, Helm e profili di configurazione. Lo stesso insieme di componenti può essere assemblato in un profilo mono compatto o separato in gruppi per la produzione.

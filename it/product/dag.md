## Processi

### Architettura senza una rete di dipendenze

Converged è una piattaforma aperta in cui la community può creare, collegare e aggiornare continuamente migliaia di Servizi, moduli e Workflow. Questi componenti evolvono indipendentemente, pur dovendo funzionare insieme con precisione.

Nelle architetture di servizi tradizionali, questo crea un problema serio con la crescita del sistema: ogni nuovo componente può introdurre nuovi collegamenti verso componenti esistenti. Chiamate dirette, catene di dipendenze, service mesh, routing e gestione degli errori creano gradualmente un livello separato di complessità crescente. Quando migliaia di componenti vengono sviluppati e aggiornati indipendentemente, mantenere una simile rete di connessioni diventa sempre più difficile.

**Converged risolve questo problema a livello architetturale: i Servizi non sanno nulla gli uni degli altri e non si chiamano mai direttamente.** Invece di una rete di dipendenze dirette, il sistema utilizza due livelli di composizione: l'interfaccia utente combina i dati, mentre i Workflow combinano le operazioni in processi di business.

### Composizione di dati e processi di business

A livello di interfaccia utente, i dati provenienti da più Servizi possono essere richiesti in parallelo e combinati all'interno di un singolo contesto utente. Funzioni leggere senza stato possono recuperare dati da fonti diverse, trasformarli e produrre i dati richiesti da una Superficie o da una Proiezione. I Servizi stessi non devono sapere dove o insieme a quali altri dati verranno utilizzati i loro risultati.

Le operazioni e i processi automatizzati vengono gestiti tramite i **Workflow**. Un Workflow è uno scenario individuale composto da una sequenza di script e operazioni. Definisce quali azioni devono essere eseguite, in quale ordine, quali passaggi possono essere eseguiti in parallelo, dove il processo deve attendere un evento e cosa accade quando un'operazione fallisce.

La piattaforma può contenere **migliaia di Workflow indipendenti**. Ciascuno può utilizzare Servizi e script esistenti senza creare dipendenze dirette tra i Servizi stessi.

Ad esempio, un Workflow può combinare una richiesta, il calcolo del prezzo, l'approvazione, l'accodamento, la produzione, il controllo qualità, il pagamento e la consegna. Un altro Workflow può utilizzare gli stessi Servizi per un processo completamente diverso.

### Esecuzione tramite Centimanus

**Centimanus** è il motore DAG che esegue i Workflow. Gestisce le dipendenze tra i passaggi, l'esecuzione parallela, l'attesa di eventi, i nuovi tentativi, il recupero dagli errori e lo stato dei processi di lunga durata.

Ogni Workflow è uno scenario indipendente, mentre Centimanus fornisce un meccanismo di esecuzione unificato per tutti. L'aggiunta di un nuovo processo non richiede quindi la modifica dei Servizi esistenti né la creazione di nuovi collegamenti diretti tra loro.

Questo è particolarmente importante per una piattaforma aperta. La community può aggiungere nuovi Servizi, script e Workflow senza creare una cascata di dipendenze in tutto il sistema.

**Di conseguenza, il numero di componenti e processi può crescere fino alle migliaia senza che la complessità delle loro relazioni cresca proporzionalmente.** I Servizi rimangono indipendenti, i dati vengono composti a livello di interfaccia utente e le operazioni vengono combinate tramite Workflow individuali.

Questo conferisce a Converged un vantaggio architetturale nella scalabilità: il sistema può espandersi attraverso nuovi componenti e scenari senza trasformare le loro interazioni in una rete sempre più grande di dipendenze dirette.

### Ecosistema aperto

Per gli sviluppatori, le nuove funzionalità vengono aggiunte tramite Servizi, script senza stato e Workflow. Gli agenti AI possono inoltre avviare azioni autorizzate all'interno di scenari esistenti, rispettando le regole e i vincoli definiti.

Per gli utenti comuni, questa complessità rimane nascosta. Non devono gestire Servizi, costruire grafi o comprenderne le dipendenze. I Workflow pronti all'uso vengono forniti con le soluzioni, mentre gli utenti possono configurarli tramite regole, ruoli, scadenze, integrazioni e notifiche.

**L'utente abilita semplicemente il processo richiesto e ottiene un risultato gestito.**

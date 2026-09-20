## Deployment

Converged supporta diversi scenari di deployment — da dispositivi edge compatti e server locali fino a infrastrutture cloud al servizio di molte aziende indipendenti. La piattaforma di base funziona su **k3s**, una distribuzione Kubernetes leggera adatta a microcomputer, infrastrutture locali e cluster cloud.

Esistono tre profili principali di deployment:

* **Mono** — interfaccia utente, Servizi, storage e cache funzionano in una configurazione compatta su un'unica macchina. È adatto a **microcomputer come Raspberry Pi e Orange Pi**, dispositivi edge, piccoli server locali, sviluppo, prototipi e demo.
* **Multi** — il sistema è distribuito su più macchine all'interno di un cluster Kubernetes. L'interfaccia utente, i gruppi di Servizi, lo storage e la cache possono essere distribuiti e scalati indipendentemente. Questo profilo è adatto agli ambienti di produzione in cui sono necessarie maggiore capacità, tolleranza ai guasti e un controllo più preciso delle risorse.
* **Cloud** — più aziende operano all'interno dello **stesso cluster Kubernetes** utilizzando un'architettura multi-tenant. Ogni **tenant** dispone di un ambiente isolato con dati, configurazione e risorse propri, mentre l'infrastruttura del cluster sottostante è condivisa. Ciò consente di servire efficacemente molte aziende senza richiedere un cluster separato per ogni cliente.

Tutti e tre i profili utilizzano la stessa codebase. Cambiano solo la topologia e la configurazione del deployment. Un sistema può quindi iniziare come installazione Mono compatta su un microcomputer, passare a un cluster Multi con la crescita dei requisiti o funzionare come servizio Cloud condiviso da molte aziende indipendenti.

In un deployment **self-hosted**, l'azienda controlla l'installazione, la rete, i backup, gli aggiornamenti e la posizione fisica dei propri dati. È adatto alle organizzazioni che necessitano di pieno controllo sulla propria infrastruttura.

Nel **Cloud**, l'infrastruttura viene gestita centralmente. Più aziende condividono lo stesso cluster, mantenendo l'isolamento a livello di tenant, inclusi dati, configurazione e risorse assegnate.

È possibile anche un deployment **ibrido**: i dati sensibili e le apparecchiature possono rimanere locali, mentre il cloud viene utilizzato per aggiornamenti, accesso esterno, team distribuiti o funzionalità AI selezionate.

Il principio fondamentale è che **Converged non vincola la piattaforma a un unico modello di deployment**. Lo stesso sistema può funzionare su un piccolo microcomputer, su un cluster composto da più macchine o come servizio Cloud multi-tenant.

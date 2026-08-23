## Sicurezza

Converged parte dal presupposto che i dati di produzione non debbano finire in un unico spazio condiviso. Ordini, file dei clienti, parametri tecnologici, pagamenti, messaggi e telemetria delle attrezzature devono essere separati per workspace e zone di responsabilità.

Architetturalmente, questo è supportato dall’isolamento dei dati. I microservizi possiedono i propri store, e i workspace possono avere directory, chiavi, file e confini di accesso separati. Questo semplifica export, migrazione self-hosted, backup e audit.

I diritti di accesso si applicano non solo alle persone, ma anche agli agenti IA. Se un modello lancia un’azione, legge dati o chiama un workflow, deve farlo dentro il proprio profilo di permessi. Le azioni sono registrate, quindi è possibile ricostruire chi o quale agente ha avviato un passo, quali dati sono stati toccati e come si è concluso lo scenario.

I deployment self-hosted e private danno al cliente pieno controllo sull’infrastruttura: rete, segreti, API key, backup e posizione fisica dei dati. Il cloud è più semplice operativamente, ma non deve diventare vendor lock-in: i dati devono restare portabili e gli scenari riproducibili in un’altra installazione.

# Valkey

Valkey fornisce a Converged un servizio chiave-valore in memoria. Viene utilizzato per
i dati che traggono vantaggio dai comandi di Valkey e dalla semantica di scadenza:
valori memorizzati nella cache, contatori, stato di coordinamento di breve durata e
altri valori condivisi che devono essere letti o modificati rapidamente.

Il wrapper compila il server incluso come libreria nativa e lo avvia nel
proprio thread. Il server è in ascolto sull'indirizzo locale e sulla porta
configurati; il wrapper comunica quindi con esso tramite libvalkey. La sua API C
avvia e arresta il server, verifica la disponibilità, segnala l'utilizzo della
memoria ed esegue le operazioni chiave-valore supportate.

Questa configurazione incorporata disabilita gli snapshot e AOF, utilizza un
unico database logico e applica la politica di espulsione `allkeys-lru` entro il
limite di memoria configurato. Queste impostazioni rendono esplicito il ciclo di
vita invece di ereditare un'installazione esterna di Valkey.

# Stanchion

Stanchion aggiunge tabelle colonnari a SQLite. Viene utilizzato quando un
archivio Converged deve leggere un piccolo insieme di campi tra molti record:
misurazioni, cronologia degli eventi, log e altri dati a cui vengono aggiunti
dati in coda. Una normale tabella SQLite mantiene insieme una riga; una tabella
Stanchion mantiene ogni colonna nei propri segmenti, così una query legge solo
le colonne che menziona.

Stanchion viene esposto tramite l'interfaccia delle tabelle virtuali di SQLite.
Una tabella viene dichiarata con `USING stanchion` e una `SORT KEY`; la chiave
di ordinamento definisce l'ordine fisico dei record e consente all'estensione di
ignorare i gruppi di righe che non possono soddisfare un predicato. I valori
vengono memorizzati come inserimenti in sospeso, quindi scritti nei segmenti di
colonna utilizzando le codifiche selezionate dall'estensione.

Il wrapper compila l'estensione per il runtime SQLite nativo. Stanchion è ancora
un software alpha: il suo formato su disco e le operazioni sulle tabelle
supportate non sono ancora definiti.
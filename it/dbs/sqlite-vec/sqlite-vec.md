# sqlite-vec

`sqlite-vec` porta colonne vettoriali e query dei vicini più prossimi agli archivi SQLite utilizzati da Converged. Una tabella vettoriale può conservare gli embedding accanto ai campi che identificano e descrivono l'oggetto di origine, così una richiesta di ricerca non deve lasciare l'archivio solo per classificare i record simili.

L'estensione fornisce tabelle virtuali `vec0` per vettori float, int8 e binari. Le query restituiscono righe ordinate per distanza; i metadati, le colonne ausiliarie e le chiavi di partizione rimangono disponibili nella stessa query SQLite. Questo è utile per i percorsi di ricerca semantica e recupero della piattaforma, dove filtraggio e classificazione fanno parte della stessa operazione.

Il wrapper compila l'estensione C upstream come artefatto nativo. SQLite la carica nel processo che possiede il database; in questa integrazione non esiste un servizio separato per la ricerca vettoriale.

# RyuGraph

RyuGraph fornisce l'archivio a grafo per i dati il cui significato è veicolato dalle connessioni tra i record: dipendenze, proprietà, topologia, genealogia e modelli simili fortemente incentrati sulle relazioni. È un motore a grafo delle proprietà integrato con query Cypher, perciò un attraversamento e le join necessarie vengono eseguiti nel processo nativo invece di essere ricostruiti nel codice dell'applicazione.

Il motore memorizza i dati del grafo su disco ed esegue query analitiche sul grafo con archiviazione colonnare, strutture di adiacenza compresse ed elaborazione vettorializzata delle query. Converged utilizza il wrapper per rendere questo motore disponibile come libreria condivisa nativa insieme agli altri componenti di archiviazione.

La compilazione omette intenzionalmente i binding del linguaggio upstream, gli esempi, la shell e gli obiettivi di benchmark. L'artefatto risultante contiene il motore a grafo e l'ABI richiesta dalla piattaforma.

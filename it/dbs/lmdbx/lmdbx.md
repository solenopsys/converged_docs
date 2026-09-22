# LMDBX

LMDBX è l'archivio di coppie chiave-valore ordinato utilizzato quando Converged ha bisogno di accedere direttamente ai byte invece che a SQL. Il wrapper apre un ambiente su disco ed espone le operazioni put, get, delete, le transazioni e i cursori tramite API Zig e C. I cursori rendono le scansioni per intervallo e l'iterazione ordinata parte della stessa primitiva di archiviazione delle ricerche puntuali.

libmdbx memorizza i suoi alberi B+ in file mappati in memoria e utilizza MVCC per i lettori. Le transazioni di lettura vedono uno snapshot stabile mentre un writer esegue il commit delle modifiche. Questo modello è adatto agli indici e allo stato dei servizi che vengono letti frequentemente e aggiornati in transazioni brevi.

Il wrapper collega staticamente libmdbx e produce librerie condivise native per i target supportati. È il livello FFI attorno al motore, non un processo di database separato.

# CuraEngine

CuraEngine prepara i lavori FDM e FFF per Converged. Dato un modello e un profilo
di stampante, suddivide la geometria in strati, genera pareti, riempimento e
percorsi di supporto, quindi scrive il G-code che una stampante a estrusione di
materiale esegue. È lo slicer dell'ecosistema Cura, utilizzato qui senza
l'interfaccia utente desktop.

Il wrapper nativo esegue `CuraEngine slice` in una directory temporanea isolata
e restituisce il G-code generato tramite la sua ABI C. L'esecuzione dello slicer
in un processo separato contiene il suo stato globale e i percorsi di errore,
così un modello o un profilo non valido non arresta il processore che ha
richiesto lo slicing.

Il wrapper prepara un lavoro; non invia il G-code a una stampante. L'invio e
l'esecuzione vengono gestiti successivamente dall'adattatore dell'apparecchiatura
appropriato.

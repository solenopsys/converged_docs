# Adattatore seriale Marlin

L'adattatore Marlin è il percorso seriale diretto da Converged a una stampante
FDM che esegue il firmware Marlin. Apre la porta seriale della stampante, invia
il G-code e tiene traccia dei dettagli del protocollo che rendono affidabile un
flusso di stampa: numeri di riga, checksum, risposte `ok` e richieste di
reinoltro.

L'API include il controllo dei lavori, il movimento e il ritorno all'origine, i
riscaldatori, l'estrusione, le operazioni sulla scheda SD, l'arresto di
emergenza e il G-code grezzo. Le risposte del firmware vengono analizzate nello
stato della stampante: temperature, coordinate, identità, avanzamento della SD
e stato della stampa. Ciò consente al livello delle apparecchiature di
utilizzare un unico modello di stato mentre l'adattatore continua a comunicare
con il protocollo seriale del firmware.

Il nome rimane per compatibilità con l'API circostante. Il wrapper non esegue
OctoPrint né chiama la sua API HTTP; comunica direttamente con Marlin.

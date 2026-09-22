# Adattatore diretto UVtools

L'adattatore UVtools prepara i file per le stampanti a resina. Esegue `UVtoolsCmd`
sui file sottoposti a slicing, consentendo di ispezionare i livelli, convalidare un file, ripararlo,
convertire tra i formati supportati, estrarre le miniature e segnalare le proprietà
del file o i problemi rilevati. Questo lavoro avviene prima che un file venga consegnato a un
adattatore per stampanti.

Il wrapper mantiene UVtools come eseguibile esterno. La sua API espone sia il percorso grezzo degli
argomenti sia operazioni denominate per la conversione, l'ispezione,
il confronto, l'estrazione delle miniature e la segnalazione dei problemi. Restituisce al chiamante
l'output standard, l'errore standard, lo stato di uscita e lo stato dell'adattatore
del processo figlio.

UVtools deve essere installato sull'host. Il wrapper fornisce il confine del processo:
timeout del comando, directory di lavoro, limiti di output e acquisizione
del risultato.

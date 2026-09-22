# SPEACH

SPEACH è il percorso locale di input vocale per Converged. Trasforma l'audio del
microfono e delle chiamate nello stesso testo che CASE e PARAMS ricevono dalla
tastiera. Un'istruzione pronunciata può quindi entrare nel normale flusso dei
comandi e dei parametri senza inviare l'audio a un servizio di trascrizione
remoto.

Per una richiesta registrata, SPEACH accetta audio WAV o Opus, lo converte in
una forma d'onda mono a 16 kHz ed esegue il modello CTC locale. Per una sessione
live, decodifica i pacchetti Opus, utilizza il rilevamento dell'attività vocale
per raccogliere una frase ed emette eventi di trascrizione parziali e completati.
Le brevi pause restano all'interno di una frase; il silenzio la chiude. Un
segmento è limitato a quaranta secondi.

Il riconoscimento termina con il testo. SPEACH non cerca di indovinare a quale
comando della schermata si riferiscano le parole. La trascrizione passa quindi
allo stesso instradamento sensibile al contesto e alla stessa estrazione dei
parametri utilizzati dall'input digitato.

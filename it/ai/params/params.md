# PARAMS

PARAMS estrae i valori di cui un comando ha bisogno dalla richiesta dell'utente. Viene eseguito
dopo che CASE ha riconosciuto il comando. Per «mostra ordine 4815», CASE seleziona il
comando dell'ordine e PARAMS restituisce il numero dell'ordine. L'applicazione può quindi
aprire la schermata dell'ordine con quel numero già applicato.

Il comando fornisce i parametri che accetta e, dove pertinente, i valori disponibili che possono
essere nominati nel testo. PARAMS utilizza il modello ONNX GLiNER2
per trovare i valori nella richiesta e associarli a quei parametri. Lo stesso
meccanismo gestisce sia un valore diretto, come un numero d'ordine, sia una scelta
nominata, come un cliente, uno stato o un elemento dell'attrezzatura.

Insieme, CASE e PARAMS trasformano una richiesta in un comando e nei relativi argomenti.
L'applicazione riceve entrambe le parti ed esegue la consueta navigazione o
azione.

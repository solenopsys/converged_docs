# OpenCAMLib

OpenCAMLib fornisce la componente geometrica del flusso del percorso utensile CNC in Converged.
Utilizza la geometria delle superfici STL e i parametri dell'utensile per calcolare i percorsi
fresa e le stime. Mentre CuraEngine costruisce percorsi additivi strato per strato,
OpenCAMLib modella il contatto dell'utensile con il pezzo in lavorazione per le
operazioni sottrattive.

La libreria implementa le operazioni drop-cutter, push-cutter e waterline e
supporta utensili cilindrici, sferici, bull, conici e compositi. Il wrapper locale espone la
piccola ABI C necessaria al flusso esistente per la stima della fresatura STL e
compila la libreria C++ upstream come artefatto nativo.

OpenCAMLib produce la geometria del percorso utensile. La post-elaborazione nella sintassi
comandi di uno specifico controller, seguita dall'esecuzione su una macchina, appartiene ai
percorsi CAM e delle apparecchiature descritti di seguito.

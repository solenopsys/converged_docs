# MTConnect CppAgent

Questo wrapper esegue l'Agent C++ di MTConnect per Converged. L'agent riceve
segnali dagli adattatori delle macchine configurati e li pubblica come flusso
di dati MTConnect. Fornisce ad apparecchiature CNC, robot, sensori e altri
dispositivi di produzione un modello comune che il resto della piattaforma può
utilizzare.

Il wrapper avvia `cppagent` con un `agent.cfg`, attende che il suo endpoint HTTP
sia pronto e arresta il processo quando il servizio viene rilasciato. L'XML del
dispositivo descrive il modello dell'apparecchiatura; la configurazione
 dell'agent seleziona adattatori, porte e opzioni di runtime. I client leggono
gli endpoint `/probe`, `/current` e `/sample` risultanti dall'agent in esecuzione.

L'integrazione è deliberatamente basata sui processi. Utilizza la configurazione
e l'interfaccia HTTP native dell'agent invece di incorporare la sua libreria C++
el runtime Zig.

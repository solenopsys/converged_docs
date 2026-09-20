## Tecnologie

Converged è costruito su una base di sistemi compatta, progettata per garantire prestazioni elevate e un utilizzo efficiente delle risorse in ambienti Kubernetes di qualsiasi dimensione, da un singolo microcomputer a un cluster distribuito.

Al centro dell'infrastruttura c'è **Zig**, un linguaggio moderno, estremamente veloce e semplice per la programmazione di sistemi. Zig viene utilizzato per gli elementi infrastrutturali in cui sono importanti prestazioni, efficienza delle risorse, accesso all'hardware e controllo a basso livello.

**Cruller** fornisce l'ambiente di esecuzione per TypeScript e JavaScript. È un runtime specializzato derivato da Bun e adattato all'architettura e ai requisiti di Converged.

**Behemoth** fornisce un livello dati unificato che supporta diversi modelli di archiviazione, inclusi SQL, dati chiave-valore, file, vettori e altre strutture dati specializzate. Lo storage può essere distribuito e scalato in base ai requisiti di ogni distribuzione.

**Fujin** fornisce il livello di comunicazione, collegando Services, interfacce, eventi e apparecchiature tramite un'infrastruttura unificata di comunicazione in tempo reale. **Centimanus** esegue i Workflows e ne gestisce le dipendenze, l'esecuzione parallela, gli eventi, i tentativi e le operazioni di lunga durata.

Converged viene sempre eseguito in **Kubernetes**. L'ambiente di base è **k3s**, una distribuzione leggera di Kubernetes che rende pratico lo stesso modello di distribuzione anche su piccoli dispositivi edge come Raspberry Pi. Su una singola macchina, Converged viene eseguito come un cluster compatto a singolo nodo; quando necessario, lo stesso cluster può essere distribuito su più macchine.

Questo fornisce una base tecnologica coerente in tutta l'infrastruttura, da un piccolo dispositivo edge a un cluster cloud distribuito.

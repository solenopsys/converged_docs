# Agent CppAgent MTConnect

Cette enveloppe exécute l’agent C++ MTConnect pour Converged. L’agent reçoit
les signaux des adaptateurs de machines configurés et les publie sous forme de
flux de données MTConnect. Il fournit aux équipements CNC, aux robots, aux
capteurs et aux autres appareils de l’atelier un modèle commun que le reste de
la plateforme peut exploiter.

L’enveloppe démarre `cppagent` avec un fichier `agent.cfg`, attend que son point
de terminaison HTTP soit prêt, puis arrête le processus lorsque le service est
libéré. Le XML des appareils décrit le modèle des équipements ; la configuration
de l’agent sélectionne les adaptateurs, les ports et les options d’exécution. Les
clients lisent les points de terminaison `/probe`, `/current` et `/sample`
produits par l’agent en cours d’exécution.

L’intégration est délibérément basée sur un processus. Elle utilise la
configuration native de l’agent et son interface HTTP plutôt que d’intégrer sa
bibliothèque C++ dans l’environnement d’exécution Zig.

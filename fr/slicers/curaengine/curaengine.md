# CuraEngine

CuraEngine prépare les tâches FDM et FFF pour Converged. À partir d'un modèle et d'un profil d'imprimante, il divise la géométrie en couches, génère les parois, le remplissage et les trajectoires de support, puis écrit le G-code qu'exécute une imprimante à extrusion de matériau.
Il s'agit du trancheur de l'écosystème Cura, utilisé ici sans l'interface utilisateur de bureau.

L'enveloppe native exécute `CuraEngine slice` dans un répertoire temporaire isolé et renvoie le G-code généré via son ABI C. L'exécution du trancheur hors processus isole son état global et ses chemins d'échec, de sorte qu'un modèle ou un profil invalide ne puisse pas arrêter le processeur ayant demandé le tranchage.

L'enveloppe prépare une tâche ; elle n'envoie pas le G-code à une imprimante. La transmission et l'exécution sont prises en charge ultérieurement par l'adaptateur d'équipement approprié.

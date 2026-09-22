# Adaptateur série Marlin

L’adaptateur Marlin est le chemin série direct entre Converged et une imprimante FDM
fonctionnant avec le firmware Marlin. Il ouvre le port série de l’imprimante, envoie du
G-code et suit les détails du protocole qui rendent un flux d’impression fiable : numéros
de ligne, sommes de contrôle, réponses `ok` et demandes de renvoi.

L’API couvre le contrôle des tâches, les mouvements et le référencement, les chauffages,
l’extrusion, les opérations sur carte SD, l’arrêt d’urgence et le G-code brut. Les
réponses du firmware sont analysées pour produire l’état de l’imprimante : températures,
coordonnées, identité, progression sur la carte SD et état de l’impression. Cela permet à
la couche d’équipement d’utiliser un modèle d’état unique tandis que l’adaptateur
continue de communiquer avec le protocole série du firmware.

Le nom est conservé pour assurer la compatibilité avec l’API environnante. Le wrapper
n’exécute pas OctoPrint et n’appelle pas son API HTTP ; il communique directement avec
Marlin.

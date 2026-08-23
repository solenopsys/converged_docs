## Processus

Le principal problème d’un atelier qui grandit est rarement l’absence d’un bouton supplémentaire. Le plus souvent, les processus vivent dans la tête des personnes : qui doit répondre au client, quand calculer le prix, qui vérifie le fichier, quand lancer la production, qui prévenir en cas de retard et que faire après l’expédition.

Dans Converged, ces chaînes sont décrites comme des workflows. Un processus typique peut aller de la demande à l’estimation, l’approbation, la mise en file, la production, le contrôle qualité, le paiement, la livraison et les notifications. L’utilisateur ne construit généralement pas un graphe à partir de zéro : les scénarios prêts à l’emploi sont livrés avec les solutions, et la configuration se limite aux règles, rôles, délais, intégrations et notifications.

Techniquement, l’exécution est déplacée dans la couche Runtime. Elle lance les workflows, tâches cron, étapes d’intégration et logique métier tout en restant stateless : les données persistantes restent dans les microservices, et Runtime exécute les chaînes. Ainsi, la logique métier n’est pas dispersée dans des dizaines de services et il existe un endroit clair où vivent les règles de processus.

Pour les déploiements complexes, les workflows peuvent être étendus. Un développeur décrit les scénarios comme des classes TypeScript typées, et les agents IA peuvent lancer des actions autorisées dans ces scénarios. Mais pour un utilisateur ordinaire, l’objectif est différent : ne pas construire un éditeur, mais activer un processus prêt et obtenir un résultat maîtrisé.

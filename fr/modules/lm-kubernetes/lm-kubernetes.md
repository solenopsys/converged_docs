# lm-kubernetes

## Objet

Pont d'opérateur Kubernetes sans état : applique les intentions d'automatisation de la plateforme aux ressources du cluster (déploiements, jobs) via un client dédié. Aucun état persistant ; les secrets sont résolus via lm-secrets.

## Limite de responsabilité

Responsable de la traduction de l'API du cluster et des lectures d'application/statut ; ne gère pas l'orchestration des workflows, la planification ni le stockage des secrets.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- Non inclus dans une solution prédéfinie

## Source

`modules/lambdas/automation/lm-kubernetes`
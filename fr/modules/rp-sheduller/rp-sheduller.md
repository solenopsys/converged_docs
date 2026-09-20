# rp-sheduller

## Objectif

Le déclencheur temporel partagé : planifications cron et leur historique d'exécution pour
tout l'écosystème. Toute tâche récurrente s'enregistre ici au lieu d'exécuter sa propre
boucle de minuterie.

## Modèle mental

L'opérateur définit une entrée cron (quel workflow, quand, avec quels args) → le
runtime se déclenche selon la planification → l'historique enregistre ce qui a été exécuté et comment cela s'est terminé.
Ce module stocke et liste les entrées ; il n'exécute jamais rien lui-même.

## Valeur pour l'écosystème

Une seule horloge pour les travaux récurrents :

- Lignes cron, historique d'exécutions et statistiques derrière une API.
- Toute tâche récurrente n'a besoin que d'une ligne cron — aucune nouvelle infrastructure de minuterie.

## Non-objectifs

- Ni définition ni exécution de workflows.
- Pas de déclencheurs uniques — uniquement des planifications récurrentes.
## Périmètre de responsabilité

Possède CRUD/liste/stats pour les entrées cron et les enregistrements d'historique ; n'exécute
ni workflows, ni minuteurs, ni réessais, ni distribution en arrière-plan.

## Dépendances directes de modules

- Aucune

## Appartenance aux solutions

- Non inclus dans une solution prédéfinie

## Source

`modules/repositories/automation/rp-sheduller`
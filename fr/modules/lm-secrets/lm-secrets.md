# lm-secrets

## Objectif

L'adaptateur partagé de coffre-fort de secrets : des valeurs de secrets nommées pour l'ensemble de la
plateforme derrière un seul contrat. Les services lisent ici les secrets de configuration au lieu de
la dispersion env ou des clients de coffre-fort par module.

## Modèle mental

Le service demande par nom de secret → obtient la valeur. La rotation a lieu en un
endroit et se propage à chaque consommateur. Les détails du backend de stockage restent derrière
le contrat.

## Valeur pour l'écosystème

Une seule porte de coffre-fort pour tous :

- Identifiants de fournisseurs, jetons d'intégration, secrets OAuth — même forme get/set/delete.
- Tout consommateur garde les secrets hors du code et de la config ; la rotation a lieu en un seul endroit.
- Les nouvelles intégrations ne nécessitent aucune nouvelle plomberie de secrets.

## Non-objectifs

- Pas d'authentification ni de vérifications d'autorisations.
- Pas de registres d'identité utilisateur.
## Limite de responsabilité

Responsable du stockage, de la récupération et de la suppression des valeurs de secrets nommées ; n'est pas responsable de
l'identité, des autorisations ni de la logique de session.

## Dépendances directes de modules

- Aucune

## Appartenance aux solutions

- Non inclus dans une solution prédéfinie

## Source

`modules/lambdas/sequrity/lm-secrets`
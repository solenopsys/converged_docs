# rp-webhooks

## Objectif

La porte d'entrée unique pour le monde extérieur : les systèmes externes appellent un
endpoint de webhook, et ce module valide, normalise et diffuse les événements
vers l'intérieur. Aucun domaine n'expose son propre schéma d'URL de rappel.

## Modèle mental

POST du système externe → le webhook valide la signature et la structure → normalisé
l'événement est enregistré comme une livraison et routé vers le topic configuré.
Les tentatives de livraison et la validation se trouvent ici ; la réaction métier a lieu
en aval.

## Valeur pour l'écosystème

Une entrée unique pour les callbacks externes :

- Configurations d'endpoints et enregistrements de livraison derrière une seule API.
- Tout système externe obtient la même forme d'endpoint au lieu d'une plomberie spécifique à chaque intégration.

## Non-objectifs

- Pas d'exécution de workflows.
- Pas de publication d'événements ni d'envoi de notifications.
## Limite de responsabilité

Responsable du transport webhook, de la validation et des tentatives de livraison ; n'est pas responsable
du traitement métier du système cible.

## Dépendances directes de modules

- Aucune

## Appartenance aux solutions

- Non inclus dans une solution prédéfinie

## Source

`modules/repositories/automation/rp-webhooks`
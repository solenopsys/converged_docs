# rp-events

## Objectif

Le journal partagé du bus d'événements métier : tout domaine y publie « ce qui s'est passé » sans connaître ses consommateurs. Commandes, demandes, équipements, paiements — tous parlent un même langage d'événements.

## Modèle mental

Le producteur émet un événement typé (kind, entity, time, payload) → il arrive sur le flux partagé. Les consommateurs (déclencheurs de workflow, notificateurs, analytique) s'abonnent par type et réagissent. L'éditeur n'appelle jamais directement le consommateur.

## Valeur dans l'écosystème

Point de découplage pour les changements d'état :

- Événements métier typés publiés une fois et relistés derrière une seule API.
- Tout domaine enregistre « ce qui s'est passé » sans connaître ses lecteurs.

## Non-objectifs

- Pas la bande brute des journaux.
- Pas de compteurs ni d'agrégats.
- Pas l'exécution du workflow elle-même.
## Périmètre de responsabilité

Possède la création, le stockage et la récupération des événements ; ne possède pas le traitement métier côté consommateur ni l'exécution des workflows.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- Non inclus dans une solution prédéfinie

## Source

`modules/repositories/business/rp-events`
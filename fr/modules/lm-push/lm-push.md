# lm-push

## Objectif

Branche push du fan-out de notification partagé : transport push web/mobile derrière le contrat rp-notify.

## Valeur pour l'écosystème

Notifications en temps réel pour les chats, commandes, demandes — livrées avec les e-mails/SMS à partir d'une seule intention de notification.

## Non-objectifs

Pas de ciblage ni de logique métier — cela relève de rp-notify et du domaine appelant.

## Périmètre de responsabilité

Prend en charge les détails d'intégration du fournisseur push ; ne prend pas en charge la logique métier de ciblage des notifications.

## Dépendances directes de modules

- Aucune

## Appartenance aux solutions

- Non inclus dans une solution prédéfinie

## Source

`modules/lambdas/providers/lm-push`
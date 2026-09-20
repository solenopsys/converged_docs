# rp-orders

## Objet

Cycle de vie des commandes : création, mises à jour, listage et suivi. Les fichiers sont joints via fileId (rp-files), la discussion repose sur un threadId (rp-threads), l’achèvement peut déclencher des invitations à laisser un avis.

## Limite de responsabilité

Possède les enregistrements de commandes et les transitions de statut ; ne possède ni le stockage de fichiers, ni la messagerie, ni les mécanismes d’avis.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- Non inclus dans une solution prédéfinie

## Source

`modules/repositories/business/rp-orders`
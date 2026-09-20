# lm-sms

## Objectif

Branche SMS de la diffusion partagée des notifications : transport fournisseur derrière le contrat rp-notify.

## Valeur écosystémique

Les pings urgents (incidents, codes d'invitation, changements de statut) atteignent les téléphones tandis que les autres canaux portent la forme longue. Même API d'intention que email/push.

## Non-objectifs

Aucune règle de campagne ou de segmentation — le domaine appelant décide.

## Limite de responsabilité

Possède la connectivité du fournisseur SMS et le formatage de la charge utile ; ne possède pas les règles de segmentation campagne/métier.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- Non inclus dans une solution prédéfinie

## Source

`modules/lambdas/providers/lm-sms`
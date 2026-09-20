# lm-smtp

## Objet

Branche SMTP de la diffusion partagée des notifications : transport fournisseur simple derrière le contrat rp-notify.

## Valeur pour l’écosystème

Le domaine émet une intention de notification unique via rp-notify → cet adaptateur la distribue via SMTP. Remplacer ou ajouter des fournisseurs d’e-mails ne touche jamais les domaines.

## Non-objectifs

Pas de politique de canal, de nouvelles tentatives ni de modèles — cela relève de rp-notify et du domaine appelant.


## Limite de responsabilité

Possède le transport SMTP et la gestion de la distribution au niveau protocole ; ne possède pas l’orchestration des notifications de haut niveau.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- Non inclus dans une solution prédéfinie

## Source

`modules/lambdas/providers/lm-smtp`
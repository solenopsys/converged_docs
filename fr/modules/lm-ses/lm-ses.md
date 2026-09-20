# lm-ses

## Objectif

Branche SES de la diffusion partagée des notifications : transport e-mail AWS derrière le contrat rp-notify.

## Valeur pour l'écosystème

Les e-mails en masse et transactionnels (invitations à évaluer, mises à jour de commandes, invitations d'équipe) transitent par une seule intégration SES. Les identifiants sont résolus via lm-secrets.

## Hors objectifs

Pas de politique de canal ni de modèles — cela relève de rp-notify et du domaine appelant.


## Périmètre de responsabilité

Possède l'intégration d'envoi et le mappage spécifiques à SES ; ne possède pas le domaine de création de modèles d'e-mails.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- Non inclus dans une solution prédéfinie

## Source

`modules/lambdas/providers/lm-ses`
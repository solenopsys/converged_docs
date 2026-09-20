# rp-access

## Objectif

La couche d'autorisation partagée : chaque `rp-*` demande ici « cet acteur peut-il faire ceci » au lieu d'inventer ses propres vérifications d'autorisation. Un seul arbre d'autorisations, une seule règle d'évaluation, appliquée avant l'exécution de tout gestionnaire.

## Modèle mental

Deux questions, deux couches : l'accès aux méthodes (« peut appeler X ») est conservé dans l'arbre d'autorisations et appliqué par le guard ; l'accès aux objets (« quelles lignes l'appel retourne ») est évalué par entité. Sans le premier, n'importe qui pourrait appeler `deleteTopic`.

## Valeur pour l'écosystème

Racine de confiance unique pour les décisions :

- L'arbre d'autorisations, les préréglages, les étiquettes et les jetons émis se trouvent au même endroit.
- Chaque service vérifie le même arbre au lieu de créer ses propres tables de stratégies.

## Non-objectifs

- Ni connexion ni émission de session.
- Ni stockage de secrets.
## Limite de responsabilité

Possède l'évaluation des politiques d'autorisation et les périmètres d'accès ; ne possède pas la vérification d'identité / la connexion d'authentification.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `security`

## Source

`modules/repositories/sequrity/rp-access`
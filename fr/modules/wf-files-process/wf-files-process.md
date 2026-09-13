# wf-files-process

## Objectif

Réception des fichiers téléversés : il décompresse les archives et classe tout ce qui en est extrait, en indiquant quels fichiers sont des modèles de production. Il ne crée pas de demande et n'effectue aucune analyse — cela relève de la décision de l'assistant, suivie de `wf-request-analyze`.

## Limite de responsabilité

La limite du module est définie par ses contrats publics et son répertoire d'implémentation.

## Dépendances directes du module

- Aucune

## Appartenance à la solution

- `requests`

## Source

`modules/workflows/wf-files-process`

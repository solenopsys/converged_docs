# rp-calls

## Objet

Sessions d'appel et métadonnées : configuration, participants et liaison aux enregistrements (flux de blocs dans rp-store) et aux transcriptions/fils (rp-threads). Résumés via wf-dialogue-summary.

## Périmètre de responsabilité

Possède la logique métier de session d'appel et les métadonnées d'appel ; ne possède pas l'infrastructure de l'opérateur télécom, les octets audio ni les fils de messages.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `ai`

## Source

`modules/repositories/communications/rp-calls`
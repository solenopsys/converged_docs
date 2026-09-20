# rp-threads

## Objectif

La couche conversationnelle unique de l'écosystème : tout module où des personnes
ou des agents échangent des messages ne conserve aucun message propre — il détient un
`threadId`, et le dialogue lui-même vit ici.

## Modèle mental

L'entité (salon de discussion, sujet de forum, appel, demande) stocke uniquement un `threadId`.
Tous les messages, l'ordre et le contexte vivent dans le fil. Créer une entité
= créer un `threadId` et le remettre à l'appelant, qui l'enregistre.

## Valeur pour l'écosystème

Un format de dialogue partout :

- Fils et messages ordonnés derrière une API unique, identifiés par id de fil opaque.
- Toute entité joint une discussion sans ses propres tables de messages.

## Non-objectifs

- Ni salons de discussion ni sujets de forum — uniquement les fils de messages associés.
- Ni distribution de notifications ni résumés de dialogues.
## Limite de responsabilité

Possède le cycle de vie des fils, l'ordonnancement des messages et les métadonnées au niveau du fil ; ne
possède ni salles/sujets, ni appartenance, ni passerelles de transport pour
email/SMS/push.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `ai`

## Source

`modules/repositories/communications/rp-threads`
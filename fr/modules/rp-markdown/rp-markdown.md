# rp-markdown

## Objectif

Le pipeline Markdown partagé : analyse, transformation et rendu pour
chaque module qui traite du contenu textuel. Un seul comportement d’analyseur au lieu
de variantes par surface.

## Modèle mental

Source Markdown en entrée → analyser/transformer → sortie rendue (HTML, blocs).
Les auteurs de contenu écrivent une fois ; docs, chats, landing pages et notifications rendent
la même source de manière cohérente.

## Valeur pour l’écosystème

Épine dorsale textuelle unique :

- Fichiers Markdown plus conversion JSON derrière une seule API.
- Chaque producteur stocke le texte humain de la même manière au lieu de sa propre gestion de fichiers.

## Non-objectifs

- Pas de stockage de blocs typés.
- Pas de rendu HTML.
## Limite de responsabilité

Possède le comportement de conversion/analyse Markdown ; ne possède ni le transcodage
de médias riches ni la composition de pages.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `content`

## Source

`modules/repositories/content/rp-markdown`
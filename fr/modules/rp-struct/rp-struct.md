# rp-struct

## Objectif

Le constructeur de structures partagé : transforme le contenu libre en représentations typées, conformes au schéma,
sur lesquelles chaque consommateur peut compter. Un point de modélisation unique entre le contenu brut
et le rendu de canal.

## Modèle mental

Contenu brut en entrée → la modélisation de structure applique schémas et formes → blocs typés
en sortie. Les canaux (`sf-*`, markdown, modèles de notification) affichent les blocs
sans ré-analyser la source.

## Valeur pour l'écosystème

Une étagère JSON sans type :

- Documents JSON derrière une seule API de fichiers.
- Tout producteur stocke des blobs structurés sans sa propre gestion de fichiers.

## Non-objectifs

- Pas de taxonomie ni d'étiquetage.
- Pas de rendu markdown.
## Limite de responsabilité

Responsable de la modélisation de structure et de la mise en forme au niveau du schéma ; n'est pas responsable du rendu final
spécifique au canal.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `content`

## Source

`modules/repositories/content/rp-struct`
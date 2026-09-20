# lm-compressors

## Objectif

Le cheval de trait partagé en octets du pipeline de fichiers : assemblage, décompression,
analyse ZIP, découpage de sortie et staging. Sans état — aucun client `files` ou
`store` à l'intérieur ; il renvoie des octets et des références de cache, la persistance
relève du workflow.

## Modèle mental

Le workflow transmet les réfs de chunks + l'opération (décompacter, assembler, découper) → lambda
effectue un pur travail d'octets → renvoie les octets stagés/réfs de cache. Il ne décide jamais
de ce que signifie un fichier et ne stocke jamais rien.

## Valeur pour l'écosystème

Un seul endroit où les octets d'archive sont manipulés :

- Chunks compressés en entrée, entrées stagées en sortie — une seule forme de décompactage pour tout appelant.
- Tout futur format d'archive ou de compression arrive ici une fois et met à niveau toutes les admissions à la fois.

## Non-objectifs

- Ni stockage ni classification de fichiers.
- Ni conversion de modèles ni rendu d'aperçus.
## Limite de responsabilité

Possède l'assemblage d'octets, la décompression, l'analyse d'archives, le découpage de sortie et
le staging ; ne possède ni enregistrements de fichiers ni persistance.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `requests`

## Source

`modules/lambdas/data/lm-compressors`
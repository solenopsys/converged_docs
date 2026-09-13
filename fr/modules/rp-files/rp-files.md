# rp-files

## Objectif

Fournit des API de métadonnées de fichiers et des workflows de gestion de fichiers.

## Limites de responsabilité

Gère les enregistrements de fichiers et les opérations au niveau des fichiers ; ne gère pas les détails d’implémentation du stockage des objets.

## Dépendances directes du module

- `rp-store` — le magasin de blocs adressé par contenu dans lequel sont stockés les octets de chaque fichier.
  rp-files conserve les noms, les collections et la liste des blocs ; il ne stocke aucune donnée.

## Appartenance à la solution

- `requests`

## Source

`modules/repositories/data/rp-files`

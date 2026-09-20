# rp-store

## Objet

Magasin de blocs à adressage par contenu — la couche la plus basse de stockage binaire de
tout l'écosystème. Stocke les fragments par hachage de contenu ; ne connaît rien des fichiers,
commandes, utilisateurs ou entités métier.

## Modèle mental

Le producteur découpe les octets en fragments → les dépose dans le magasin → récupère
des références. Le consommateur réassemble les octets à partir des références. Le magasin
lui-même est une simple table key(blob_hash) → octets avec déduplication : un
fragment identique téléversé deux fois est stocké une fois.

## Valeur pour l'écosystème

Fondation d'octets à adressage par contenu :

- Blobs d'octets opaques indexés par hachage, stockés une fois, référencés partout.
- Tout producteur persiste des octets sans son propre stockage binaire.

## Non-objectifs

- Ni métadonnées de fichiers ni collections.
- Ni entrées de cache intermédiaires.
## Limite de responsabilité

Possède le put/get de blocs par référence de contenu et le cycle de vie des fragments ; ne possède
ni nommage/collections au niveau fichier ni sémantique métier des services appelants.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `requests`

## Source

`modules/repositories/data/rp-store`
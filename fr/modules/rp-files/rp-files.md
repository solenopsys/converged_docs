# rp-files

## Objectif

L'abstraction de fichiers unique de l'écosystème : tout module ayant besoin
de « fichiers » vient ici au lieu de créer sa propre table de noms et de chemins.
Conserve les métadonnées, les collections et les listes de blocs ; les octets eux-mêmes résident dans
le stockage bloc, accessibles via un client de service de stockage.

## Modèle mental

Fichier = enregistrement (nom, extension, collection, propriétaire) + liste ordonnée de références de blocs
 dans le stockage bloc. La classification (`detectType`), la matérialisation
et la persistance opèrent sur les métadonnées — les octets ne sont chargés que lorsque c'est vraiment nécessaire
(préparation de modèle, service de téléchargement).

## Valeur pour l'écosystème

Le point d'entrée de l'ingestion des fichiers :

- Fichiers, blocs, collections et métadonnées derrière une seule API ; les octets des blocs sont délégués au stockage bloc.
- Tout domaine lie un id de fichier opaque à son entité au lieu de copier des octets.

## Non-objectifs

- Pas le stockage bloc brut — les octets des blocs résident dans le magasin de blocs.
- Pas la décompression d'archives ni la conversion de modèles.
## Limite de responsabilité

Possède les enregistrements de fichiers, les collections et le cycle de vie des listes de blocs ; ne possède pas
les détails d'implémentation du stockage objet ni les transformations d'octets.

## Dépendances directes de modules

- Aucune — les octets des blocs passent par un client de service de stockage, qui est un appel
  de transport comme celui effectué par tout consommateur externe, et non un lien de module à module.
  rp-files conserve les noms, les collections et la liste de blocs ; il ne stocke aucune donnée.

## Appartenance à la solution

- `requests`

## Source

`modules/repositories/data/rp-files`
# rp-classifier

## Objectif

Le service partagé d'étiquetage : toute ingestion y dirige le contenu brut et reçoit
en retour des catégories, des étiquettes ou des intentions. Une seule logique de classification au lieu de
chaînes de if par domaine.

## Modèle mental

Le producteur envoie des éléments bruts (fichiers, textes, requêtes) → le classifieur attribue
des étiquettes → l'appelant route par étiquette (modèle de production vs dessin, urgent
vs bruit). Les étiquettes sont des conseils ; la décision métier reste à l'appelant.

## Valeur pour l'écosystème

Une seule étagère taxonomique :

- Nœuds d'arbre et mappages de clés derrière une seule API.
- Toute ingestion résout les étiquettes à partir du même arbre au lieu de ses propres dictionnaires.

## Non-objectifs

- Pas d'octets de fichiers ni de conversion.
- Pas de stockage de documents JSON.
## Limite de responsabilité

Possède la logique de classification et l'attribution des étiquettes ; ne possède pas les pipelines d'ingestion de contenu source ni le routage métier en aval.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- Non inclus dans une solution prédéfinie

## Source

`modules/repositories/content/rp-classifier`
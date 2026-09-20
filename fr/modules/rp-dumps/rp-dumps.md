# rp-dumps

## Objectif

Le quai d'exportation partagé : tout domaine y capture ses données pour migration,
sauvegarde ou transfert au lieu d'inventer son propre format de dump. Instantanés
conditionnés avec métadonnées de récupération.

## Modèle mental

Le domaine demande un dump (périmètre, temps) → le dump est généré et conditionné →
les métadonnées de récupération pointent vers l'artefact stocké.
La génération et la comptabilité vivent ici ; l'archivage à long terme vit ailleurs.

## Valeur pour l'écosystème

Une seule histoire d'export pour la plateforme :

- Listage du stockage, statistiques, compactage et segments de dump derrière une API.
- Tout domaine devient exportable sans sa propre machinerie d'instantanés.

## Non-objectifs

- Pas de diffusion de fichiers en direct.
- Pas de stockage d'octets parallèle.
## Périmètre de responsabilité

Possède la génération, le conditionnement et les métadonnées de récupération des dumps ; ne possède pas
la plateforme d'archivage à long terme.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- Non inclus dans une solution prédéfinie

## Source

`modules/repositories/data/rp-dumps`
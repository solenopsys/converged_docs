# rp-telemetry

## Objectif

Le flux technique partagé de santé : les services signalent « comment ils vont » (latence, erreurs, signaux de ressources) ici au lieu que chaque outil d’exploitation les collecte individuellement. Ingestion normalisée, une seule surface de requête pour la santé.

## Modèle mental

Le service pousse des événements de santé (source, signal, temps, payload) → la télémétrie les normalise en une forme uniforme. Les consommateurs ops (tableaux de bord, workflows d’incident) lisent la santé par service au fil du temps. Le sens métier est attribué par le lecteur, non par le stockage.

## Valeur pour l’écosystème

Un journal d’échantillons numériques :

- Tout producteur écrit des lignes (appareil, paramètre, valeur, unité, temps) dans des stockages hot/cold.
- Une chronologie unique pour les nombres de toute origine — capteurs d’équipement ou tout autre.

## Non-objectifs

- Pas de stockage de journaux texte.
- Pas d’enregistrements d’usage.
- Pas de politique d’alerte ni de résolution d’incidents.
## Limite de responsabilité

Responsable de l’ingestion et de la normalisation des événements de télémétrie ; non responsable des définitions d’analytics produit, de l’alerting ou de la remédiation.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `analitycs`

## Source

`modules/repositories/analytics/rp-telemetry`
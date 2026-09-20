# rp-logs

## Objectif

Le journal unique en ajout seul de l'écosystème : tout service, équipement
ou flux de travail y écrit « ce qui s'est passé » au lieu de développer son propre stockage
de journaux. Écritures peu coûteuses, lectures par heure/source.

## Modèle mental

Le producteur envoie un événement (heure, source, niveau, texte/payload) → il arrive sur
le flux partagé. Le consommateur lit une tranche par source ou intervalle. Aucune
agrégation ni alerte à l'intérieur — juste l'enregistrement du fait.

## Valeur pour l'écosystème

Un flux réutilisé par tous :

- Services : journaux opérationnels sans stockage propre par `rp-*`.
- Équipements : journaux de machines/dispositifs — même API, source différente, des imprimantes 3D
  à tout module ou système externe.
- Tout producteur écrit « ce qui s'est passé » au même endroit au lieu de développer
  son propre stockage de journaux ; l'audit et la revue lisent une seule chronologie.

## Non-objectifs

- Pas de compteurs ni d'agrégats.
- Pas d'échantillons numériques ni d'enregistrements d'usage.
- Pas de traçage d'appels distribués ni d'alertes.
## Limite de responsabilité

Possède les API d'ingestion et de récupération des journaux ; ne possède pas les métriques métier,
l'agrégation, les alertes ni la stratégie de traçage.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `analitycs`

## Source

`modules/repositories/analytics/rp-logs`
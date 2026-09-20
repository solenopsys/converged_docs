# rp-counters

## Objectif

Configuration par tenant des compteurs d'analyse externes : stocke les ID de suivi (GA4, GTM, Yandex Metrika, Meta Pixel) ou un snippet head personnalisé, afin que le SSR puisse injecter les bons scripts par tenant.

## Modèle mental

L'opérateur enregistre un compteur (type, ID de suivi ou snippet, indicateur d'activation) → le store conserve la configuration. Le SSR lit les compteurs activés pour le tenant actuel et restitue les balises correspondantes. Aucun chiffre n'est collecté ici, uniquement les paramètres des compteurs.

## Valeur pour l'écosystème

Un seul endroit pour le câblage analytique :

- Les compteurs externes (GA4, GTM, Metrika, Pixel) et les snippets personnalisés sont configurés par tenant au lieu d'être codés en dur par landing page.

## Non-objectifs

- Pas de stockage d'événements bruts.
- Pas de journaux d'échantillons numériques.
- Pas d'enregistrements d'utilisation ni de facturation.
## Limite de responsabilité

Possède les configurations de compteurs (type, ID de suivi ou snippet, indicateur d'activation) ; ne collecte pas de métriques, n'agrège pas l'utilisation et ne facture pas.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `analitycs`

## Source

`modules/repositories/analytics/rp-counters`
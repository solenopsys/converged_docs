# rp-usage

## Objet

Le compteur de consommation partagé : toute fonctionnalité signale ici « la quantité utilisée »
au lieu de suivre les quotas localement. Agrégé par consommateur et par période —
la source à partir de laquelle la facturation et les limites lisent.

## Modèle mental

La fonctionnalité enregistre la consommation (qui, quoi, combien, période) → l'usage
l'agrège par compte/période. La facturation en aval transforme les agrégats en argent ;
les contrôles de limites lisent les totaux actuels. La mesure vit ici, la tarification vit
en aval.

## Valeur écosystémique

Un journal d'événements d'usage :

- Toute fonctionnalité enregistre les lignes (fonction, utilisateur, date) de la même manière.
- Les liens solution-fonction permettent à tout rapport de regrouper les appels par solution sans tables de quotas par module.

## Non-objectifs

- Pas de facturation ni d'exécution de paiement.
- Pas d'authentification ni de contrôles d'autorisation.
- Pas de compteurs bruts pour les tableaux de bord.
## Limite de responsabilité

Possède la mesure et l'agrégation de l'usage ; ne possède ni la facturation, ni l'exécution des paiements,
ni la politique tarifaire.

## Dépendances directes de modules

- Aucune

## Appartenance aux solutions

- `analitycs`

## Source

`modules/repositories/analytics/rp-usage`
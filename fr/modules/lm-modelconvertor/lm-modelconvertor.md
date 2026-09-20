# lm-modelconvertor

## Objectif

Le pont partagé de formats de modèles : convertit les modèles de production entre représentations internes et externes (p. ex. en aperçus GLB) afin qu'aucun workflow ne lie directement une bibliothèque de conversion native.

## Modèle mental

Le workflow prépare les octets du modèle → le convertisseur transforme le format → renvoie les octets d'aperçu/convertis comme refs de cache pour `rp-files.persist`. Transformation pure : pas de stockage, pas d'estimations, pas de décisions métier.

## Valeur pour l'écosystème

Un point de conversion unique pour les modèles de production :

- Un fichier préparé en entrée, sorties converties comme refs de cache en sortie — même forme pour tout appelant.
- Nouveaux formats et versions du convertisseur intégrés une fois et mettant à niveau chaque parcours d'analyse.
- Tient les dépendances natives lourdes hors des workflows et dépôts.

## Non-objectifs

- Pas de stockage de fichiers ni d'orchestration d'admission.
- Pas de rendu d'aperçu ni d'estimations de découpage.

## Limite de responsabilité

Possède les routines de conversion/transformation ; ne possède ni l'entraînement des modèles en amont, ni la desserte en aval, ni la persistance.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- Non inclus dans une solution prédéfinie

## Source

`modules/lambdas/convertors/lm-modelconvertor`
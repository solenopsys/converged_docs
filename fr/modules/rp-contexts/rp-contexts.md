# rp-contexts

## Objet

Le magasin partagé de contextes nommés pour l'IA : les prompts, les variantes linguistiques et
les connaissances métier se trouvent ici au lieu d'être codés en dur dans chaque workflow.
Versionné par nom, résolu par langue.

## Modèle mental

Le workflow ou l'assistant demande un contexte par nom (+ langue) → obtient le
texte actuel. Les éditeurs mettent à jour les contextes sans redéployer les consommateurs.
Le stockage et la récupération se font ici ; l'ingénierie des prompts relève des éditeurs.

## Valeur pour l'écosystème

Une étagère de connaissances pour les parcours d'IA :

- Contextes nommés avec variantes linguistiques derrière une API.
- Tout parcours d'IA résout le même contexte nommé au lieu de ses propres copies de prompts.

## Non-objectifs

- Pas d'historique de chat ni de fils de dialogue.
- Pas d'exécution de prompts — uniquement des textes de contexte stockés.
## Périmètre de responsabilité

Possède le stockage et la récupération des contextes d'IA nommés et des variantes linguistiques ;
ne possède pas l'infrastructure du fournisseur de modèles ni le comportement de dialogue.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `ai`

## Source

`modules/repositories/ai/rp-contexts`
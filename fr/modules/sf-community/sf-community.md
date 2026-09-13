# sf-community

## Objectif

Le forum, sous la forme de trois onglets distincts : les sections, les sujets d'une section et la discussion d'un sujet. L'ouverture d'une ligne ouvre un onglet à côté de l'onglet actuel — aucun écran n'affiche simultanément une arborescence de sections, un tableau de sujets et un fil de discussion.

## Limites de responsabilité

Gère la navigation du forum et l'écran d'un sujet. Les messages eux-mêmes appartiennent à `rp-threads`, que le navigateur lit directement ; les pièces jointes appartiennent à `rp-files` via un message `link`. Les adhésions, les rôles et les tickets n'en font pas partie.

## Création d'un sujet

`createTopic` sur `rp-community` génère l'identifiant du sujet et celui du fil, puis renseigne l'auteur à partir du jeton ; cette surface enregistre ensuite le fil et écrit le message initial dans `rp-threads`. Cette séparation est intentionnelle : les identifiants qu'un client peut choisir sont des identifiants qu'il peut usurper, et le fait qu'un dépôt en appelle un autre est précisément ce que l'architecture interdit.

## Mises à jour en temps réel

Les réponses arrivent via le canal métier de Fujin (`pushrouter`) par l'intermédiaire de la bibliothèque `threads-state`, et non par interrogation périodique. Une notification ne contient que des identifiants ; le texte est relu depuis `rp-threads`, où le prédicat de lecture s'applique.

## Dépendances directes du module

- `front-core`, `g-community`, `g-threads`, `signal-channel`, `threads-state`

## Appartenance à la solution

- `communications`

## Source

`modules/surfaces/communications/sf-community`

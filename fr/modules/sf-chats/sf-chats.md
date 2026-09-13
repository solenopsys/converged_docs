# sf-chats

## Objectif

Salles de discussion, sous la forme de trois onglets distincts : la liste des
salles, la conversation d'une salle et les membres d'une salle. Gérer les
personnes présentes dans une salle et lire ce qu'elles ont dit sont deux tâches,
et donc deux onglets.

## Limite de responsabilité

Prend en charge la navigation entre les salles, l'écran de conversation et la
modification des membres. Les messages appartiennent à `rp-threads`, lus
directement depuis le navigateur ; les fichiers appartiennent à `rp-files` par
l'intermédiaire d'un message `link`.

## Création d'une salle

`createRoom` sur `rp-chats` génère l'identifiant de la salle et celui du fil, et
enregistre le créateur issu du jeton comme `owner` ; cette interface enregistre
ensuite le fil auprès de `rp-threads`. `rp-chats` n'appelle jamais un autre
dépôt.

## Mises à jour en temps réel

Un nouveau message est publié à chaque membre par son nom via le `pushrouter` de
Fujin, jamais à l'ensemble du tenant : l'existence d'une salle privée n'est pas
publique, même lorsque son contenu reste protégé par le prédicat de lecture. La
notification ne contient que des identifiants.

## Dépendances directes du module

- `effector`, `front-core`, `g-chats`, `g-threads`, `signal-channel`, `threads-state`

## Appartenance à la solution

- `communications`

## Source

`modules/surfaces/communications/sf-chats`

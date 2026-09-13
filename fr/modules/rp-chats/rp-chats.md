# rp-chats

## Objectif

Salles de discussion, leur appartenance et leurs contextes par salle. La conversation
elle-même ne se trouve pas ici : une salle contient un `threadId` et les messages résident dans
`rp-threads`.

## Limite de responsabilité

Gère les salles, les rôles et les contextes. N'appelle aucun autre dépôt — `createRoom` génère
le `threadId` et le renvoie, puis l'appelant enregistre le fil.

## Identité et accès

L'appelant provient du jeton vérifié, jamais d'un paramètre. Deux
conséquences méritent d'être mentionnées :

- `listRooms` est limité à l'appelant dans la requête, de sorte que la substitution de l'identifiant d'un autre
  utilisateur ne permet plus de lire ses salles, et que `totalCount` ne peut pas divulguer le nombre
  de salles qu'il a masqué ;
- tout ce qui s'adresse à une salle par son identifiant vérifie d'abord l'appartenance.

`chart_room_users` est conservé même après l'arrivée de `access_tags` : une balise exprime
l'appartenance, mais pas la distinction entre `owner`, `admin` et `member`.

## Remarque sur les noms de tables

Les tables s'écrivent `chart_rooms` / `chart_room_users`. La faute de frappe est
cohérente dans les migrations, les entités et les requêtes, donc le code fonctionne ; renommer
est une migration, pas une modification.

## Dépendances directes du module

- `back-core`, `nrpc`, `g-chats`

## Appartenance à la solution

- `communications`

## Source

`modules/repositories/communications/rp-chats`

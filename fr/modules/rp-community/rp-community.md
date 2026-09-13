# rp-community

## Objectif

Structure et gouvernance du forum : sections, sujets, leurs auteurs et les personnes qui peuvent les voir. Les échanges sous un sujet ne se trouvent pas ici — un sujet contient un `threadId` et les messages se trouvent dans `rp-threads`.

## Limite de responsabilité

Gère les sections et les sujets. N'appelle ni `rp-threads` ni aucun autre dépôt : `createTopic` génère un `threadId` et le renvoie, puis l'appelant enregistre lui-même le fil et rédige le message d'ouverture.

## Identité et attribution

`createdBy` n'est jamais accepté d'un appelant. Il est lu depuis le jeton vérifié via `getCurrentWorkspaceContext()`, que `messaging-backend` privilégie par rapport à toute valeur déclarée dans l'enveloppe. Les identifiants des sujets et des fils sont générés ici pour la même raison — un identifiant qu'un client peut choisir est un identifiant qu'il peut usurper, et la table des balises d'accès n'enregistre aucun type d'objet permettant de détecter la collision.

## Visibilité

Les sections et les sujets possèdent une colonne `visibility` (`public` | `authenticated` | `private` | `tagged`), et un nouveau sujet hérite de la valeur de sa section, sauf s'il demande une valeur plus restrictive. Les balises associées à `tagged` appartiennent à la relation partagée `access_tags` décrite dans `access-control.md` ; cette partie n'est pas encore implémentée, donc aujourd'hui `visibility` est enregistrée mais n'est pas appliquée.

## Verrouillage

`touchTopicActivity` est le seul endroit où un verrou peut être appliqué : `rp-threads` accepte un message sans savoir que les sujets existent, donc un écran appelle cette fonction après la publication et considère un refus comme un échec de publication.

## Dépendances directes du module

- `back-core`, `nrpc`, `g-community`

## Appartenance à la solution

- `communications`

## Source

`modules/repositories/communications/rp-community`

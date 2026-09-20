# rp-auth

## Objectif

La porte d'entrée unique pour prouver « qui vous êtes » : sessions, identifiants et
émission de jetons pour tout l'écosystème. Aucun domaine ne gère sa propre connexion.

## Modèle mental

L'utilisateur présente ses identifiants → auth les valide et émet une session/un jeton →
chaque appel en aval le transporte et la couche d'accès décide de ce qu'il peut faire.
La connexion prouve l'identité ; les autorisations constituent une couche distincte.

## Valeur pour l'écosystème

Un backend de connexion unique pour toutes les surfaces :

- Liens magiques, sessions de rafraîchissement et enregistrements de clients OAuth au même endroit.
- Chaque frontend connecte les utilisateurs de la même manière au lieu d'utiliser ses propres tables de session.

## Non-objectifs

- Pas de politiques d'autorisation.
- Pas de dossiers de profil utilisateur.

## Périmètre de responsabilité

Possède les flux d'authentification et la logique d'émission de jetons/sessions ; ne possède pas
les adaptateurs de fournisseurs OAuth tiers ni l'évaluation des politiques d'autorisation.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `security`

## Source

`modules/repositories/sequrity/rp-auth`
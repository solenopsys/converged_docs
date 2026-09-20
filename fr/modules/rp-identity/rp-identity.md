# rp-identity

## Objectif

Le registre de profils partagé : un enregistrement d’identité par personne ou compte de service,
lié depuis chaque domaine. Commandes, discussions, cartes d’employés — tous pointent
vers le même profil au lieu de copier noms et attributs.

## Modèle mental

Identité = enregistrement stable (id, attributs principaux, état du cycle de vie). Les domaines
stockent l’id d’identité et lisent les attributs à la demande ; ils ne dupliquent jamais le
profil. L’auth prouve l’identité, l’accès la vérifie, les domaines la référencent.

## Valeur pour l’écosystème

Un « qui » pour la plateforme :

- Dossiers utilisateurs, liens de méthodes d’authentification et invitations au même endroit.
- Chaque domaine stocke un id utilisateur opaque et lit les attributs à la demande au lieu de dupliquer les profils.

## Non-objectifs

- Ni connexion ni sessions.
- Ni autorisations.
- Ni structure organisationnelle ni sémantique de staffing.
## Périmètre de responsabilité

Possède les enregistrements d’identité et l’état du cycle de vie des identités ; ne possède pas
les stratégies d’autorisation détaillées ni les flux d’authentification.

## Dépendances directes de modules

- Aucune

## Appartenance à la solution

- `security`

## Source

`modules/repositories/sequrity/rp-identity`
# wf-team-invite

## Objectif

Transforme une liste de personnes collée — « nom + adresse », quelle que soit la
forme sous laquelle un humain l’a écrite — en comptes utilisateur, rôles, fiches
de personnel et invitations, puis envoie à chaque personne le lien qui lui
permet de se connecter.

Cela existe parce que quatre services doivent avancer ensemble pour une ligne de
cette liste (`rp-identity`, `rp-access`, `rp-staff`, `rp-auth`, ainsi qu’une
lambda de messagerie), et que les microservices ne s’appellent pas entre eux.

## Pourquoi c’est aussi la frontière des privilèges

`rp-access` refuse catégoriquement un JWT utilisateur (`@Access("internal")`),
donc aucune surface ne peut attribuer un rôle. centimanus exécute ce script avec
`SERVICE_TOKEN`, et les personnes autorisées à l’exécuter sont définies par une
permission ordinaire — `wf/workflows/wf-team-invite.js(x)` — vérifiée à la
périphérie (`signal_provider.zig:146`) et inscrite dans un fichier de préréglages
unique. C’est pourquoi le produit ne possède pas de concept
« administrateur ».

Le script ne peut pas voir qui l’a appelé, donc la protection contre l’escalade
repose sur une liste fixe : `manager`, `operator`, `viewer`. `owner` et `root` ne
peuvent pas être attribués ici.

## Structure

1. sources textuelles — `files.materialize` + `files.extractText`, ainsi que
   `rawText` ;
2. personnes — `rt.llm` en premier, puis une expression régulière ligne par
   ligne en secours ;
3. une tentative `rt.attempt` par personne — utilisateur, préréglage de base +
   rôle, étiquettes de groupe, fiche, invitation ;
4. la lettre — sa propre tentative, afin qu’un relais refusé constitue une
   branche et non un compte perdu ;
5. le rapport, dont la surface transforme les `staffIds` en une table ouverte
   contenant exactement ces personnes.

Réexécuter la même liste est sans danger : une adresse connue est `updated`,
jamais un deuxième compte.

## Dépendances directes du module

- `g-access`, `g-auth`, `g-files`, `g-identity`, `g-notify`, `g-ses`, `g-smtp`,
  `g-staff`

## Appartenance à la solution

- `production`

## Source

`modules/workflows/wf-team-invite`

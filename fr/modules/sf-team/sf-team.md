# sf-team

## Objectif

L’équipe comme un espace de travail unique : qui y travaille, ce que chacun peut
faire et qui a été invité mais n’est pas encore arrivé.

## Projections

Quatre vues `setOf`, que le shell transforme en boutons permanents de l’onglet
— **Équipe**, **Invitations**, **Planning**, **Droits** — ainsi qu’une vue
`objectOf`, la fiche de la personne, qui s’ouvre comme un sous-onglet *dans* la
même zone. Lorsqu’aucun élément n’est sélectionné, la zone affiche son propre
écran (`team.statistic` résolu via sa vue `setOf`, le modèle utilisé par
`sf-logs` et `sf-equipment`).

## Ce qui façonne cette surface

**La console ne peut rien accorder.** `rp-access` est `@Access("internal")` et
le runtime refuse un JWT utilisateur avant même qu’une permission soit vérifiée
(`messaging-access.ts:176`). Ainsi, toute opération qui modifie ce que quelqu’un
peut faire exécute `wf-team-invite` sur centimanus, qui détient le jeton de
service du cluster. La personne autorisée à l’exécuter est définie par
l’autorisation ordinaire `wf/workflows/wf-team-invite.js(x)`, qui se trouve dans
un seul fichier de préréglages — cette autorisation constitue l’ensemble de
« qui peut ajouter des personnes ».

Trois méthodes d’invitation de `rp-identity` portent un `@Access("user")` au
niveau de la méthode, afin que la colonne de livraison puisse être lue sans
workflow à chaque actualisation de tableau ; elles sont contrôlées par
`rp/identity/listInvites(r)` dans les préréglages du propriétaire et du
responsable.

La projection **Droits** est composée dans le navigateur à partir de la liste
des membres et des invitations, car le service qui connaît la véritable réponse
ne peut pas être interrogé depuis ici. Elle affiche l’intention enregistrée — le
rôle attribué à une personne et les étiquettes qui l’accompagnaient — et non une
lecture de son jeton actif.

## Opérations

`team.member.import` (celle pour laquelle ce contour existe — une liste collée
en entrée, un tableau rempli exactement avec ces personnes en sortie),
`team.member.create`, `team.member.save`, `team.member.setRole`,
`team.member.deactivate`, `team.invite.revoke`, `team.shift.create`.

Trois d’entre elles sont publiées dans le catalogue de discussion de `llm.json`.

## Dépendances directes du module

- `front-core`, `g-centimanus`, `g-identity`, `g-staff`

## Appartenance à la solution

- `production`

## Source

`modules/surfaces/sequrity/sf-team`

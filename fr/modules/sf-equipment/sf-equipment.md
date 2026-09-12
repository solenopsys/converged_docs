# sf-equipment

## Objectif

L'atelier comme une seule zone de travail : quelles machines existent, dans quel état se trouve chacune,
quel travail elle exécute, ce que sa télémétrie indique actuellement, ce qui lui est arrivé,
et ce qui est ensuite planifié sur elle.

## Structure

La surface déclare trois vues `setOf` — machines, journal, planning — que
l'espace de travail transforme en boutons permanents de cet onglet, ainsi qu'une vue
`objectOf` pour une machine. Ouvrir une imprimante ouvre donc un sous-onglet *à l'intérieur de*
l'équipement plutôt que de quitter celui-ci. Lorsqu'aucun élément n'est sélectionné, la surface
affiche son propre écran, `EquipmentDashboardView`.

## Limite de responsabilité

Lit et écrit dans `rp-equipment`. Lit `rp-orders` pour le travail qu'une machine
exécute et `rp-telemetry` pour ses paramètres en temps réel — directement depuis le navigateur,
ce qui est l'endroit où une composition en deux appels doit se faire ; aucun des deux dépôts
ne connaît l'autre.

L'état de la machine est écrit ici car, jusqu'à ce qu'un pont de télémétrie le signale,
l'opérateur se tenant à côté de la machine en est la seule source de vérité.

## Dépendances directes des modules

- `g-equipment`
- `g-orders`
- `g-telemetry`

## Appartenance à la solution

- `production`

## Source

`modules/surfaces/business/sf-equipment`

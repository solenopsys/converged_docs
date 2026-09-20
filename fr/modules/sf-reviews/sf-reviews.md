# sf-reviews

## Objectif

Le système d’avis comme un espace de travail unique : ce que les clients ont dit
du travail, ce qui en est publié sur le site, ce que la boutique a répondu, et où
en est la demande — combien de liens ont été envoyés, combien ont été ouverts,
combien ont généré une réponse.

## Structure

La surface déclare deux vues `setOf` — les avis et les invitations qui les ont
sollicités — que l’espace de travail transforme en boutons permanents de cet
onglet, ainsi qu’une vue `objectOf` pour un avis. La file de modération, le mur
d’avis publiés et l’ensemble des avis rejetés sont des préréglages de la table
des avis plutôt que trois types : il s’agit d’une seule liste consultée de trois
manières. Ouvrir un avis ouvre donc un sous-onglet *à l’intérieur* des avis au
lieu de quitter cette section. Lorsqu’aucun élément n’est sélectionné, la
surface affiche son propre écran, `ReviewsDashboardView`.

## Limite de responsabilité

Lit et écrit dans `rp-reviews`. Lit `rp-orders` pour le travail concerné par un
avis — directement depuis le navigateur, car c’est là qu’une composition en
deux appels doit avoir lieu ; aucun des deux dépôts ne connaît l’autre.

L’envoi n’est pas effectué depuis cet espace. `wf-order-review-request` génère
et envoie le lien personnel, et `wf-order-review-followup` le relance, car
atteindre une commande et un avis dans un même processus est précisément le rôle
d’un workflow. « Demander un avis » sur cette surface génère le lien et laisse
l’envoi à ce flux, afin qu’il n’y ait qu’un seul expéditeur et une seule trace.

## Filtrage des avis

Le formulaire public affiche les plateformes externes à tout le monde. Le seuil
de la boutique modifie l’*accent* — un client satisfait se voit proposer les
plateformes en premier, tandis qu’un client mécontent est d’abord invité à
échanger avec la boutique — mais jamais la disponibilité des liens, car ne
montrer le chemin vers un avis public qu’aux clients satisfaits est interdit par
Google et plusieurs autres plateformes. La carte indique vers quoi le formulaire
s’est orienté pour un avis donné ; elle ne filtre rien.

## Dépendances directes du module

- `g-reviews`
- `g-orders`

## Appartenance à la solution

- `production`

## Source

`modules/surfaces/business/sf-reviews`

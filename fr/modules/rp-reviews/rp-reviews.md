# rp-reviews

## Objectif

Le système d’avis de la boutique, réparti en trois tables qui répondent à trois questions différentes.

- `reviews` — ce qu’un client a dit, ce que la boutique lui a répondu et si l’avis
  est présent sur le site. La modération se fait ici : un avis provenant de
  l’extérieur naît avec le statut `pending` et n’est visible que dans la console
  jusqu’à ce qu’une personne le publie.
- `review_invites` — un lien personnel à usage unique par commande, et ce qu’il
  est devenu : envoyé, ouvert, traité, expiré. C’est l’entonnoir que la boutique
  consulte.
- `review_settings` — une ligne de JSON : les plateformes externes, le seuil,
  les modèles d’e-mails, les délais et la marge de relance.

## Limite de responsabilité

Gère les avis, les invitations et les paramètres de l’entonnoir. Ne sait rien
sur les commandes : `Review.orderId` et `ReviewInvite.orderId` sont des chaînes
opaques, et leur association avec les commandes réelles relève de
`wf-order-review-request` (qui les demande) et de `sf-reviews` (qui les affiche).
Ne gère pas les fils de discussion communautaires.

## Deux portes d’accès

L’accès se fait par tag, comme partout : un avis publié porte `public`, tandis que
les autres portent `authenticated` et `moderator`, ce qui permet à la boutique
 d’agir sur un avis que personne dans la boutique n’a rédigé.

La porte du client est différente. `getInviteByToken`, `markInviteOpened` et
`submitByToken` sont autorisés par le token lui-même — une capacité, pas une
session — de sorte que le formulaire public fonctionne sans aucune connexion.
Ils renvoient une vue restreinte qui ne contient ni les coordonnées ni l’identifiant
de l’invitation, et `submitByToken` consomme le lien de manière conditionnelle,
afin que deux envois depuis le même e-mail produisent un avis et un refus,
plutôt que deux avis.

## Filtrage des avis

`positiveThreshold` déplace l’*accent* du formulaire public et rien d’autre :
à partir de ce seuil, l’auteur se voit proposer d’abord les plateformes externes ;
en dessous, un mot adressé d’abord à la boutique. Les liens vers les plateformes
restent visibles dans les deux cas, car ne montrer le chemin vers un avis public
qu’aux clients satisfaits est interdit par Google et plusieurs autres plateformes.
Le comportement sûr est celui par défaut.

## Dépendances directes du module

- Aucune

## Appartenance à la solution

- `production`

## Source

`modules/repositories/business/rp-reviews`

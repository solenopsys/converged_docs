# wf-order-review-request

## Objectif

Périmètre 2 du système d’avis : demander une fois au client, une fois le travail terminé.

Une exécution trouve une commande terminée depuis suffisamment longtemps, avec un client à contacter, qui n’a encore jamais été sollicité ; elle crée son lien d’avis personnel à usage unique dans
`rp-reviews` ; puis envoie la demande via `lm-ses`.

## Pourquoi s’agit-il d’un workflow

La question « quelles commandes terminées n’ont pas encore fait l’objet d’une demande ? » couvre deux services
qui n’ont pas le droit de se connaître : `rp-orders` ne sait pas ce qu’est un
avis, et `rp-reviews` conserve `orderId` comme une chaîne opaque. Mettre les deux listes côte à côte est précisément le rôle d’un flow — et `rt.node` permet de faire
survivre la création du lien à un redémarrage sans en créer un second.

## Structure

```
read-settings → list-finished (completed, updatedAt ≤ now − delay)
              → list-invites (lesquelles ont déjà fait l’objet d’une demande)
              → create-invite → send-email → mark-sent | mark-failed
```

Un seul e-mail par exécution, afin qu’une adresse bloquée ne bloque jamais la file derrière elle, le planning déterminant le débit. `dryRun` génère l’e-mail sans rien créer : une répétition qui laisserait un lien actif ferait que la prochaine exécution réelle ignorerait cette commande, considérée comme déjà sollicitée.

Un e-mail refusé revient de `lm-ses` sous la forme `{ success: false }`, et non sous forme d’exception ; il s’agit donc d’une branche ordinaire qui marque l’invitation comme `failed` — et non d’une limite d’erreur.

## Paramètres

- `from` (obligatoire) — adresse de l’expéditeur.
- `ses` (obligatoire) — `SesCredentials`.
- `shopName` — injecté dans `{{shopName}}` dans les modèles.
- `delayHours` — remplace `ReviewSettings.requestDelayHours` pour un rattrapage.
- `dryRun` — générer et s’arrêter.

L’objet, le corps, la base du lien et le délai proviennent de `reviews.getSettings()`, afin que la boutique puisse modifier elle-même son texte sans toucher à ce flow.

## Dépendances directes du module

- `g-orders`
- `g-reviews`
- `g-ses`

## Source

`modules/workflows/wf-order-review-request`

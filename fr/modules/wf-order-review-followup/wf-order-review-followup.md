# wf-order-review-followup

## Objectif

La relance unique. Une exécution prend un lien d’avis qui a été envoyé, est resté
sans réponse pendant le nombre de jours configuré et n’a pas atteint son nombre
autorisé de relances, puis demande une nouvelle fois.

## Pourquoi ceci est un workflow

Le choix n’est pas le suivant : `reviews.findInvitesToFollowUp` est une question
sur les invitations et appartient à `rp-reviews`. Ce flux ajoute le nom de la
commande au courriel et l’envoi — deux services dans un même processus, ce qui
correspond ici à la définition d’un workflow.

## Ce qu’il ne fait délibérément jamais

Il ne relance jamais quelqu’un qui a ouvert le formulaire. Cette personne a lu
la demande et a choisi de ne pas rédiger d’avis ; demander à nouveau est ainsi
la manière dont une demande d’avis devient du spam. Cette condition réside dans
la requête du dépôt plutôt que dans ce flux, afin qu’un futur appelant ne puisse
pas l’oublier.

Une relance refusée laisse l’invitation à l’état `sent` plutôt que `failed` : le
premier courriel a bien été envoyé, et le client peut encore y répondre.

## Structure

```
read-settings → find-due (sent, jamais ouvert, sous le quota)
              → read-order (uniquement pour le nom)
              → send-email → count-followup
```

Compter la relance est ce qui la rend *unique* : la même requête ne renverra pas
ce lien une nouvelle fois. `dryRun` génère le courriel sans rien compter.
`maxFollowups: 0` désactive entièrement les relances, et le flux s’arrête avant
d’envoyer la demande.

## Paramètres

- `from` (obligatoire) — adresse de l’expéditeur.
- `ses` (obligatoire) — `SesCredentials`.
- `shopName`, `delayDays`, `maxFollowups`, `dryRun` — remplacements ; les valeurs
  par défaut proviennent de `reviews.getSettings()`.

## Dépendances directes du module

- `g-orders`
- `g-reviews`
- `g-ses`

## Source

`modules/workflows/wf-order-review-followup`

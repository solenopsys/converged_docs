# rp-dag

## Objectif

Gère les déclencheurs de workflow et le journal d’exécution. Il n’exécute rien.

## Limite de responsabilité

Deux éléments appartiennent ici, et rien d’autre :

- **Déclencheurs** — « lorsque ce sujet de bus apparaît, exécuter ce workflow ». Configuration système : des dizaines de lignes gérées par un opérateur, conservées intégralement en mémoire du runtime plutôt que requêtées.
- **Le journal d’exécution** — un arbre de ce qu’une exécution a fait. Le runtime l’écrit pendant l’exécution du script : un nœud est ouvert avant l’exécution de son corps et fermé lorsqu’il se termine, de sorte qu’une exécution en cours affiche le nœud sur lequel elle se trouve.

Le catalogue des workflows n’est pas géré ici. Ptah place les descripteurs de la Solution active dans l’environnement de ce service (`WORKFLOWS`, `WORKFLOW_DIGESTS`, `MODULE_PROXY`) et `listAvailableWorkflows` les republie pour le runtime et l’interface utilisateur. Les octets source restent derrière Ptah-proxy.

## Le journal est écrit par le runtime, pas par ce service

Rien ici n’écrit d’entrée dans un journal. Le runtime la formate, la place dans Valkey sous une clé qu’il compose lui-même, puis transmet les clés — jamais les entrées. `commitLog` transforme chaque clé en emplacement de stockage et demande au stockage de récupérer l’entrée ; le stockage lit directement le cache, de sorte qu’une entrée ne traverse le transport qu’une seule fois, sous forme d’octets que personne ne réencode.

```text
workflow thread ─► queue ─► log writer ─► valkey
                                 │
                                 └─ commitLog([keys]) ─► rp-dag ─► storage reads valkey
                                                                        │
                                 ◄──── committed ────────────────────────┘
                                 └─ delete the committed keys
```

C’est ce qui maintient la journalisation hors du chemin critique du workflow : un nœud ne coûte au runtime qu’un ajout à la file, et rien d’autre. Cela signifie également que le journal est, par construction, soumis à une garantie de meilleure qualité : une entrée peut être abandonnée sous l’effet de la contre-pression, et un lot peut être validé deux fois après un crash. Les clés sont dérivées de l’exécution et de la séquence du nœud, donc la seconde validation est une réécriture plutôt qu’un doublon.

Les clés proviennent du runtime pour cette raison : un numéro attribué par ce service coûterait un aller-retour par nœud et ne serait pas reproductible après un redémarrage.

- `dag:log:<executionId>:exec` — l’exécution
- `dag:log:<executionId>:n:<seq>` — l’un de ses nœuds, complété par des zéros jusqu’à six chiffres

`commitLog` déduit l’emplacement de stockage à partir de la clé et refuse tout ce qui se trouve en dehors du préfixe `dag:log:`, de sorte qu’une clé constitue l’intégralité de l’autorité portée par l’appel.

## Le journal est un arbre

```text
exec:<id>              l’exécution
node:<id>:<seq>        ses nœuds, dans l’ordre de leur ouverture
```

Un nœud qui délègue via `rt.sub` contient l’identifiant de l’exécution enfant, et l’enfant est une exécution ordinaire avec ses propres nœuds. `executionTree` parcourt ce lien en profondeur et renvoie le résultat à plat, chaque ligne étant marquée par sa `depth` — ainsi, un client restitue l’arbre en indentant, et rien d’autre. Aucun index parent n’est nécessaire : le lien est le nœud qui l’a créé.

Les séquences sont complétées par des zéros dans la clé, car le magasin KV renvoie une plage de préfixe dans l’ordre lexicographique, et cet ordre doit être celui dans lequel les nœuds se sont exécutés. Le runtime complète jusqu’à la même largeur lorsqu’il compose la clé du cache ; les deux largeurs constituent un seul contrat.

La rétention est plafonnée en nombre d’exécutions (`5000` par défaut), avec application à chaque centième ouverture. Le journal sert aux diagnostics, pas à l’archivage.

## Les modifications des déclencheurs atteignent le runtime via le bus

La création, la modification ou la suppression d’un déclencheur publie `dag.triggers.changed`. Le runtime s’abonne à ce sujet en plus de ceux propres aux déclencheurs, de sorte qu’une modification est active pour l’événement suivant au lieu d’attendre la fin d’un intervalle d’interrogation. La publication est soumise à une garantie de meilleure qualité — un bus hors service ne doit pas faire échouer la modification d’un opérateur — et l’actualisation périodique du runtime reste le mécanisme de secours.

## Dépendances directes du module

- g-bus — pour annoncer une modification de déclencheur

## Appartenance à une Solution

- Non inclus dans une solution prédéfinie

## Source

`modules/repositories/automation/rp-dag`

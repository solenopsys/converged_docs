# Automatisation

## Objectif

Gère l’espace de travail d’automatisation : les workflows et leurs exécutions, les déclencheurs du bus qui les démarrent, les planifications récurrentes et les points de terminaison de webhooks entrants.

## Limites de responsabilité

Contrôle l’expérience de l’espace de travail. Il n’exécute pas les workflows, ne conserve pas les planifications et ne distribue pas les webhooks — il démarre une exécution via le runtime et relit le journal depuis rp-dag.

## La section DAG

- **Workflows** — le catalogue publié par la Solution active, en lecture seule. Ouvrir un workflow revient à demander son exécution : les paramètres sont typés en JSON et transmis à `centimanus.runWorkflow`.
- **Exécutions** — chaque exécution, avec son statut.
- **Détails de l’exécution** — l’arbre de ce que l’exécution a effectué. Une ligne par nœud : sa profondeur, s’il est terminé et la durée de son exécution. Déplier un nœud affiche les appels de service qu’il a effectués et ce qui lui a été renvoyé. Un nœud qui délègue via `rt.sub` est suivi par les nœuds de l’exécution à laquelle il a délégué, sur un niveau. Une exécution toujours en cours s’actualise automatiquement.
- **Déclencheurs** — « lorsque ce sujet du bus apparaît, exécuter ce workflow ». Sujet, workflow, paramètres JSON, activé/désactivé.
- **Variables** — état du workflow écrit par `rt.set`.

Les paramètres sont typés en JSON partout plutôt que générés dans un formulaire : les paramètres d’un workflow lui sont propres et évoluent avec lui, de sorte qu’un champ texte reste adapté lorsqu’ils changent et que ce qui est saisi correspond à ce que le workflow reçoit.

## Dépendances directes du module

- Aucune

## Appartenance à une Solution

- Non inclus dans une solution prédéfinie

## Source

`modules/surfaces/automation/sf-automation`

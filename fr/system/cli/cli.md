# Interface de ligne de commande Converged

La CLI Converged est un moteur de commandes destiné aux opérateurs. Elle fournit
une interface de commandes cohérente pour les diagnostics de plateforme,
l'automatisation, le stockage et les opérations de domaine, tout en permettant à
chaque fonctionnalité de rester dans son propre module de commandes.

## Interface de commandes modulaire

Le cœur de la CLI ne contient pas de registre fixe de commandes métier. Au démarrage,
il lit un ou plusieurs répertoires passés via `--commands` et charge le module
TypeScript sélectionné pour chaque section de commandes. Un module exporte une
fabrique qui renvoie un processeur ; le processeur déclare ses commandes et
redirige chaque nom de commande vers un gestionnaire.

```text
bun cli <section> <command> [param]
          |          |
          |          +-> gestionnaire de commande
          v
  module de commandes -> processeur -> client NRPC généré
```

Cela rend la CLI extensible sans modifier son environnement d'exécution. Une
solution ou un produit peut ajouter un répertoire de commandes, et un nouveau
module `<section>.ts` devient une nouvelle section de la CLI. Le cœur ne charge
que la section demandée pour l'exécution, de sorte qu'un module facultatif ou
défectueux ne puisse pas empêcher l'exécution de commandes sans rapport.

`BaseCommandProcessor` fournit la table commune des commandes, l'affichage de
l'aide, la propagation des erreurs et un comportement cohérent pour les listes.
Les modules se concentrent sur leurs propres arguments et actions métier ; le
lanceur prend en charge l'établissement de la connexion, les rapports de cycle
de vie, le chronométrage, le statut de sortie et l'arrêt du canal.

## Un seul modèle d'autorisation

Tous les modules de commandes utilisant NRPC empruntent le même chemin de
session et d'autorisation de la CLI. La CLI lit d'abord le JWT de l'utilisateur
dans le fichier de session local, puis utilise `SERVICE_TOKEN` si aucune session
n'est disponible. La session utilisateur est prioritaire, car les actions de
l'opérateur peuvent nécessiter l'identité de l'appelant.

Le jeton est envoyé lors de la poignée de main WebSocket partagée de Fujin et
est également fourni à la configuration du client NRPC. Si une session stockée
est rejetée, le lanceur la supprime de la connexion active et réessaie une fois
avec le jeton de service lorsqu'il est configuré. Les erreurs d'authentification
sont signalées uniformément, avec une indication invitant à se reconnecter,
plutôt que de laisser chaque module de commandes gérer lui-même l'état du jeton.

L'autorisation continue d'être appliquée par le service destinataire. La CLI
transporte les identifiants de l'appelant et la portée de l'espace de travail ;
elle n'interprète pas les autorisations et n'accorde pas d'accès localement. Une
commande peut ne pas utiliser le canal WebSocket uniquement lorsqu'elle
communique délibérément avec un point de terminaison non NRPC, comme une
opération de diagnostic directe.

## Intégration NRPC

Les modules de commandes créent des clients à partir des packages `g-<service>`
générés et leur transmettent la configuration partagée
`createCliNrpcClientConfig`. NRPC sérialise l'appel de méthode typé en une
requête WebSocket, adressée à une cible et à un service Fujin logiques. Fujin la
transmet au pair d'exécution actif, et le service applique sa politique d'accès
normale avant d'exécuter la méthode.

Le même canal prend en charge les méthodes ordinaires de requête-réponse ainsi
que les méthodes de diffusion en continu. Les identifiants de requête, les
échéances, l'ordre des réponses et la gestion des défaillances de connexion sont
centralisés dans le canal de la CLI ; chaque module bénéficie donc du même
comportement sans réimplémenter le code du protocole.

## Limites des responsabilités

La CLI prend en charge la découverte des commandes, le cycle de vie de
l'exécution des commandes, la sélection de la session locale et le canal client
NRPC/WebSocket commun. Elle ne prend pas en charge la logique métier du domaine,
les décisions d'autorisation, l'implémentation des services ni le routage Fujin.
Ces responsabilités restent du ressort des modules de commandes, des services
backend et de l'infrastructure d'exécution qui reçoit l'appel.

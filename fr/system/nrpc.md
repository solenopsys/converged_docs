# Runtime du contrat NRPC

NRPC est la couche d'appels distants typés de Converged. Elle transforme un contrat
 de service TypeScript en clients correspondants et en métadonnées de service, afin qu'un navigateur,
un microservice, un workflow ou un runtime natif puisse appeler la même capacité sans
maintenir des définitions d'API distinctes fondées sur des chaînes de caractères.

## Pourquoi il existe

La plateforme est composée de modules déployés indépendamment. Appeler directement un module
via une adresse obligerait ses appelants à dépendre de l'endroit où il s'exécute et du
transport qu'il utilise. NRPC sépare ces préoccupations : un contrat nomme le service et ses
méthodes, tandis que le runtime achemine un appel vers le processus qui possède actuellement
la cible demandée.

Cela maintient l'accord entre les appelants et les implémentations en un seul endroit. Les
paramètres d'une méthode, son type de retour, son comportement de streaming et son niveau
d'accès sont connus de la génération de code et disponibles pour chaque client pris en charge.

## Du contrat à l'appel

Les contrats sont des interfaces TypeScript situées sous `modules/types/<domain>`. L'exécution de
`bun run gen` dans `core/tools/nrpc` analyse ces interfaces et crée un package
`modules/generated/g-<service>`. Le package contient les métadonnées du contrat,
une interface serveur et des fabriques de clients sûres du point de vue des types pour chaque runtime.

```text
Interface TypeScript
        |
        v
Générateur NRPC -> package g-<service>
        |                    |
        |                    +-> client navigateur
        |                    +-> client de cluster
        |                    +-> client de runtime de workflow
        v
implémentation du service -> backend de messagerie
```

Un service enregistre son implémentation avec `createMessagingBackend`. NRPC utilise les
métadonnées générées pour trouver la méthode demandée, valide la forme de l'appel à la
frontière du client, restaure les valeurs typées et invoque la méthode d'implémentation
correspondante. Une méthode qui renvoie un `AsyncIterable` est fournie sous forme de flux ;
les méthodes ordinaires produisent une seule réponse.

## Chemins d'acheminement

NRPC préserve le même contrat dans plusieurs environnements d'exécution :

- Les clients navigateur utilisent un canal WebSocket partagé pour envoyer les requêtes à Fujin.
- Les clients de service et natifs utilisent le transport de cluster via Fujin, adressés
  à une cible de processus logique plutôt qu'à une adresse d'hôte.
- Les clients de workflow utilisent le point d'entrée RT, qui appelle le transport hôte
  QuickJS/Zig et reste synchrone pour une seule évaluation de workflow.

Fujin achemine une requête vers la connexion cible. Le processus récepteur choisit le service
et la méthode NRPC à partir des métadonnées de la requête ; Fujin n'a pas besoin de
comprendre les services métier de la plateforme. `createHttpBackend` est disponible lorsqu'une
couche HTTP en périphérie est requise et peut enregistrer la même implémentation de service
sur le runtime de messagerie, en maintenant l'alignement entre les appels HTTP et internes.

## Contexte et accès

Les appels transportent dans leur enveloppe les données de corrélation, les délais d'expiration
et un contexte d'espace de travail ou de portée fiable. Le service récepteur s'exécute avec ce
contexte, ce qui permet au code de stockage et d'autorisation d'utiliser la même limite de
locataire que celle établie à la périphérie. Les services ne doivent pas déduire l'identité de
l'espace de travail à partir d'une charge utile métier.

Le décorateur `@Access` déclare une classe ou une méthode comme étant `public`, `user` ou
`internal`. NRPC détermine le niveau déclaré le plus spécifique et applique les règles
d'autorisation configurées avant d'invoquer l'implémentation. La politique d'accès fait ainsi
partie de la frontière du service plutôt que d'une convention incohérente entre clients.

## Limites de responsabilité

NRPC prend en charge les métadonnées de contrat, les clients typés générés, la sérialisation
des valeurs, la distribution des appels et les adaptateurs de transport utilisés par ces
appels. Il ne prend pas en charge les règles métier, la découverte des services, le placement
des déploiements, la persistance métier ni le routage du bus de messages. Ces responsabilités
restent respectivement au service, au plan de contrôle des déploiements, à la couche de
stockage et à Fujin.

# Bus de messages Fujin

Fujin est le centre de communication de l'environnement d'exécution Converged. Il offre aux navigateurs,
aux services de domaine, au stockage, aux workflows, aux services multimédias et aux processeurs un moyen
partagé d'échanger des messages.

## Pourquoi il existe

Une plateforme modulaire a besoin que ses composants évoluent indépendamment. Des liens HTTP directs
obligeraient chaque service à connaître les adresses, les répliques et la topologie de déploiement.
Fujin remplace ces liens par des cibles logiques : un émetteur indique quel pair d'exécution doit recevoir
un message, et Fujin le transmet à la connexion active qui possède actuellement cette cible.

```text
émetteur -> cible logique -> Fujin -> connexion active -> service local
```

L'émetteur ne sait pas où s'exécute le récepteur. Un processus peut redémarrer ou se déplacer vers un autre
nœud et récupérer la même cible sans modifier ses appelants.

## Modèle de routage

Fujin prend une seule décision de routage : il associe une cible à une connexion. La cible sélectionne un
processus tel que l'environnement d'exécution de l'interface utilisateur, les services de domaine ou
Centimanus. Le nom du service dans le message n'est interprété qu'après sa réception par le processus
récepteur.

Il est important de séparer ces décisions. Fujin reste un petit courtier de messages plutôt que de devenir
un registre de chaque service métier, unité de stockage ou workflow.

## Trois flux

Fujin transporte trois types de trafic qui partagent un transport, mais rien d'autre. La messagerie de
services déplace les requêtes entre pairs. L'ingestion des journaux reçoit tout ce que les collecteurs du
déploiement émettent, le regroupe et remet des blocs entiers aux référentiels d'analyse, afin que le stockage
reçoive des lots plutôt qu'un flux de lignes individuelles. Les notifications utilisateur sont des messages
métier adressés à une personne : une commande est arrivée, une tâche est terminée, une lettre est en attente.

Le troisième est celui qui a besoin de son propre nom. `pushrouter` est un service hébergé par Fujin plutôt
que routé vers lui, car la distribution dépend des sessions actives que Fujin possède déjà — aucun autre
processus ne sait lesquels des navigateurs d'une personne sont actuellement connectés. Il indique le nombre
de sessions qu'un message a atteintes, ce qui permet à l'appelant de décider si un canal durable est également
nécessaire, et conserve une fenêtre de rejeu limitée afin qu'un navigateur qui se reconnecte voie ce qu'il a
manqué. Tout ce qui doit survivre à un redémarrage appartient à un référentiel, pas ici.

Les notifications transportent des clés de traduction plutôt que des phrases. Le service qui en publie une
ne connaît pas la langue du lecteur ; une chaîne rendue ne pourrait donc être correcte que pour l'un d'entre eux.

## Trafic des navigateurs et du cluster

Les pairs natifs se connectent via le transport du cluster. Les navigateurs et les clients mobiles entrent
par WebSocket et participent au même modèle de messagerie. Les interfaces interactives peuvent ainsi recevoir
des événements en direct sans introduire un second système de routage applicatif.

Les charges utiles volumineuses restent en dehors du canal de contrôle du navigateur. Les clients reçoivent
un événement de disponibilité et récupèrent les données via le chemin de contenu approprié, ce qui maintient
la réactivité de la signalisation en temps réel.

## Contexte et confiance

L'enveloppe de message commune transporte les données de corrélation, les délais, les erreurs et la portée
de locataire approuvée. Fujin transporte ce contexte sans le déduire d'une charge utile métier ni en modifier
la signification. Les services récepteurs peuvent appliquer les règles d'autorisation et de stockage au même
contexte établi à la périphérie.

## Limite des responsabilités

Fujin gère la connectivité et le routage des cibles. Il n'exécute pas de logique métier, ne sélectionne pas
un gestionnaire à l'intérieur d'un autre processus, ne stocke pas de données de domaine et ne décide pas du
placement du déploiement. Ces responsabilités restent du ressort du pair d'exécution qui reçoit le message
et de Ptah en tant que plan de contrôle.

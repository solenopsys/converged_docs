## Architecture

Converged est conçu comme une plateforme modulaire, mais pas comme une collection chaotique de microservices. La séparation est simple : l’interface affiche les données et lance les actions, Runtime exécute les processus, les microservices possèdent les données, et les adaptateurs connectent les équipements et systèmes externes.

```text
Utilisateur / client
        ↓
UI et micro-frontends
        ↓
Runtime : workflows, cron, intégrations, actions IA
        ↓
Microservices : API typées et données propres
        ↓
Storage / Behemoth / fichiers / SQL / KV / métriques
        ↓
Équipements, messageries, paiements et services externes
```

Les microservices restent volontairement fins. Chaque service est responsable de son domaine de données, de la validation et d’une API typée. Il ne doit pas connaître la logique interne des services voisins ni devenir un centre caché de processus métier. Cela réduit le couplage et simplifie la maintenance.

Toute la logique transversale est déplacée dans Runtime. Si le système doit accepter une commande, interroger plusieurs services, créer une tâche, envoyer une notification, attendre un événement et mettre à jour un statut, cela s’exécute dans un workflow. Runtime ne stocke pas d’état persistant lui-même : il écrit l’historique, les variables et les résultats via les services qui possèdent leur stockage.

Le stockage est construit autour de l’isolation. Au lieu d’une base commune, chaque domaine obtient ses propres limites de données : SQL, key-value, fichiers, données colonnes, index vectoriels ou relations de graphe quand c’est nécessaire. Cette approche aide à déplacer les workspaces, limiter les accès et éviter une base partagée où les données de clients différents se mélangent.

Le frontend est également modulaire. Le shell commun charge des micro-frontends indépendants via import map, ce qui permet à certaines zones de l’interface d’évoluer sans reconstruire tout le produit. Pour l’utilisateur, cela reste un seul système ; pour le développement, ce sont des zones de responsabilité claires.

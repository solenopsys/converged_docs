# Environnement d’exécution des workflows Centimanus

Centimanus exécute les processus en plusieurs étapes qui relient des modules
Converged autrement indépendants. Le routage des commandes, les notifications,
les approbations, le travail assisté par l’IA et les séquences de production
peuvent évoluer sous forme de workflows, sans déplacer l’orchestration dans les
services de domaine.

## Exécution rejouable

Un workflow est un programme dont les opérations importantes sont réparties en
nœuds nommés. Centimanus exécute un nœud non terminé, enregistre son résultat,
puis évalue à nouveau le workflow. Les nœuds terminés renvoient leurs résultats
enregistrés au lieu de répéter leurs effets de bord.

```text
first pass:   find order -> store result
second pass:  replay order -> reserve machine -> store result
third pass:   replay both -> notify operator -> complete
```

Les branches et les boucles peuvent dépendre de résultats antérieurs : le graphe
émerge donc du processus lui-même plutôt que d’un diagramme statique distinct.
Les résultats enregistrés des nœuds rendent la progression explicite et
permettent de reprendre l’exécution à partir de la première étape non terminée.

## Pourquoi les workflows sont séparés

Les microservices de domaine de Converged possèdent les données et de petites
capacités métier. Ils ne s’appellent pas les uns les autres pour mettre en
œuvre un processus de bout en bout. Cela évite les chaînes cachées dans
lesquelles une modification ou une défaillance d’un service affecte
inopinément de nombreux autres services.

Centimanus est l’endroit où la coordination inter-domaines est visible. Un
workflow peut appeler des services, demander un travail d’IA et choisir l’étape
suivante, tandis que chaque service reste concentré sur sa propre frontière.

## Livraison des workflows

Les solutions déterminent quels workflows sont actifs. Ptah publie cette
sélection, le service DAG expose les descripteurs sélectionnés et Centimanus
charge le contenu correspondant via le proxy adressé par contenu de Ptah. Un
workflow qui ne fait pas partie de la solution active n’est pas disponible pour
l’exécution.

Cela sépare quatre préoccupations : la sélection du produit, la livraison du
contenu, l’exécution et l’observabilité. Chacune peut évoluer sans transformer
l’environnement d’exécution des workflows en registre de modules ou en
contrôleur de déploiement.

## Limite de fiabilité

Centimanus enregistre les résultats des nœuds terminés, mais les opérations
externes doivent toujours respecter leurs propres règles d’idempotence. La
télémétrie des workflows sert à la visibilité ; elle ne détermine pas l’état
d’exécution. Les données métier restent dans les services qui en sont
propriétaires au lieu de devenir l’état du moteur de workflow.

## Place dans le système

Centimanus reçoit le travail et appelle les services via Fujin. Il utilise le
stockage de la plateforme pour la progression des workflows et signale les
événements du cycle de vie à des fins de supervision. Il ne possède pas les
enregistrements de domaine, ne sélectionne pas les solutions actives et
n’achemine pas les messages entre les autres pairs.

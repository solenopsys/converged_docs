## Processus

### Une architecture sans réseau de dépendances

Converged est une plateforme ouverte où la communauté peut créer, connecter et mettre à jour en continu des milliers de Services, de modules et de Workflows. Ces composants évoluent indépendamment tout en devant fonctionner ensemble avec précision.

Dans les architectures de services traditionnelles, cela crée un problème sérieux lorsque le système grandit : chaque nouveau composant peut introduire de nouvelles connexions avec les composants existants. Les appels directs, les chaînes de dépendances, le service mesh, le routage et la gestion des défaillances finissent progressivement par créer une couche distincte d’une complexité croissante. Lorsque des milliers de composants sont développés et mis à jour indépendamment, la maintenance d’un tel réseau de connexions devient de plus en plus difficile.

**Converged résout ce problème sur le plan architectural : les Services ne savent rien les uns des autres et ne s’appellent jamais directement.** Au lieu d’un réseau de dépendances directes, le système utilise deux niveaux de composition : l’interface utilisateur combine les données, tandis que les Workflows combinent les opérations en processus métier.

### Composition des données et des processus métier

Au niveau de l’interface utilisateur, les données provenant de plusieurs Services peuvent être demandées en parallèle et combinées dans un même contexte utilisateur. Des fonctions légères sans état peuvent récupérer des données provenant de sources différentes, les transformer et produire les données nécessaires à une Surface ou à une Projection. Les Services eux-mêmes n’ont pas besoin de savoir où ni avec quelles autres données leurs résultats seront utilisés.

Les opérations et les processus automatisés sont gérés par des **Workflows**. Un Workflow est un scénario individuel composé d’une séquence de scripts et d’opérations. Il définit les actions à effectuer, leur ordre, les étapes pouvant s’exécuter en parallèle, les endroits où le processus doit attendre un événement et ce qui se passe lorsqu’une opération échoue.

La plateforme peut contenir **des milliers de Workflows indépendants**. Chacun peut utiliser des Services et des scripts existants sans créer de dépendances directes entre les Services eux-mêmes.

Par exemple, un Workflow peut combiner une demande, le calcul d’un prix, une approbation, la mise en file d’attente, la production, le contrôle qualité, le paiement et la livraison. Un autre Workflow peut utiliser les mêmes Services pour un processus entièrement différent.

### Exécution par Centimanus

**Centimanus** est le moteur DAG qui exécute les Workflows. Il gère les dépendances entre les étapes, l’exécution parallèle, l’attente d’événements, les nouvelles tentatives, la récupération après défaillance et l’état des processus de longue durée.

Chaque Workflow est un scénario indépendant, tandis que Centimanus fournit un mécanisme d’exécution unifié pour l’ensemble d’entre eux. L’ajout d’un nouveau processus ne nécessite donc pas de modifier les Services existants ni de créer de nouvelles connexions directes entre eux.

Cela est particulièrement important pour une plateforme ouverte. La communauté peut ajouter de nouveaux Services, scripts et Workflows sans créer une cascade de dépendances dans tout le système.

**Ainsi, le nombre de composants et de processus peut atteindre des milliers sans que la complexité de leurs relations augmente proportionnellement.** Les Services restent indépendants, les données sont composées au niveau de l’interface utilisateur et les opérations sont combinées par des Workflows individuels.

Cela confère à Converged un avantage architectural en matière de mise à l’échelle : le système peut s’étendre grâce à de nouveaux composants et scénarios sans transformer leurs interactions en un réseau toujours plus vaste de dépendances directes.

### Écosystème ouvert

Pour les développeurs, les nouvelles capacités sont ajoutées au moyen de Services, de scripts sans état et de Workflows. Les agents IA peuvent également lancer des actions autorisées au sein de scénarios existants, tout en respectant des règles et contraintes définies.

Pour les utilisateurs ordinaires, cette complexité reste masquée. Ils n’ont pas besoin de gérer des Services, de construire des graphes ou de comprendre leurs dépendances. Des Workflows prêts à l’emploi sont fournis avec les solutions, tandis que les utilisateurs peuvent les configurer au moyen de règles, de rôles, de délais, d’intégrations et de notifications.

**L’utilisateur active simplement le processus requis et obtient un résultat géré.**

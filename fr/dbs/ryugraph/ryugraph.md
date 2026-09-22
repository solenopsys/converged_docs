# RyuGraph

RyuGraph fournit le stockage en graphe pour les données dont la signification est portée par les connexions entre les enregistrements : dépendances, propriété, topologie, lignage et modèles similaires riches en relations. Il s’agit d’un moteur de graphes de propriétés intégré prenant en charge les requêtes Cypher ; ainsi, un parcours et les jointures qu’il nécessite s’exécutent dans le processus natif au lieu d’être reconstruits dans le code de l’application.

Le moteur stocke les données du graphe sur disque et exécute des requêtes analytiques sur les graphes grâce à un stockage en colonnes, à des structures d’adjacence compressées et à un traitement vectorisé des requêtes. Converged utilise ce wrapper pour rendre le moteur disponible sous forme de bibliothèque partagée native aux côtés de ses autres composants de stockage.

La compilation omet volontairement les liaisons de langage en amont, les exemples, le shell et les cibles de benchmark. L’artefact obtenu contient le moteur de graphes ainsi que l’ABI requise par la plateforme.

## Technologies

Converged repose sur une base système compacte conçue pour offrir de hautes performances et une utilisation efficace des ressources dans des environnements Kubernetes de toute taille, d’un micro-ordinateur unique à un cluster distribué.

Au cœur de l’infrastructure se trouve **Zig**, un langage moderne, extrêmement rapide et simple de programmation système. Zig est utilisé pour les éléments d’infrastructure où les performances, l’efficacité des ressources, l’accès au matériel et le contrôle de bas niveau sont importants.

**Cruller** fournit l’environnement d’exécution de TypeScript et JavaScript. Il s’agit d’un runtime spécialisé dérivé de Bun et adapté à l’architecture et aux exigences de Converged.

**Behemoth** fournit une couche de données unifiée prenant en charge différents modèles de stockage, notamment SQL, les données clé-valeur, les fichiers, les vecteurs et d’autres structures de données spécialisées. Le stockage peut être distribué et mis à l’échelle selon les exigences de chaque déploiement.

**Fujin** fournit la couche de communication, reliant les Services, les interfaces, les événements et les équipements via une structure de communication unifiée en temps réel. **Centimanus** exécute les Workflows et gère leurs dépendances, leur exécution parallèle, les événements, les nouvelles tentatives et les opérations de longue durée.

Converged fonctionne toujours dans **Kubernetes**. L’environnement de base est **k3s**, une distribution Kubernetes légère qui rend le même modèle de déploiement pratique même sur de petits appareils edge tels que Raspberry Pi. Sur une seule machine, Converged s’exécute comme un cluster compact à nœud unique ; lorsque cela est nécessaire, le même cluster peut être distribué sur plusieurs machines.

Cela fournit une base technologique cohérente dans toute l’infrastructure, d’un petit appareil edge à un cluster cloud distribué.

## Architecture

Converged est conçu comme un environnement d’exécution modulaire dans lequel l’interface, la logique métier et l’infrastructure sont séparées tout en fonctionnant comme un système unique.

Au niveau utilisateur, le système se compose de **Surfaces**, qui organisent le contexte de travail, et de **Projections** — des écrans individuels conçus pour résoudre des tâches utilisateur spécifiques.

La logique métier est implémentée en **TypeScript** au moyen de plusieurs types de **Services** : Repositories, Lambdas et Runtimes. Les processus plus complexes sont assemblés en **Workflows**, exécutés par le moteur de traitement DAG Centimanus.

À la base du système se trouvent les **Apps**. Ce sont des environnements d’exécution d’infrastructure dotés d’un cœur Zig compact dans lequel s’exécutent des scripts TypeScript. Les Apps fournissent les capacités fondamentales sur lesquelles reposent les Services, les Workflows et l’interface utilisateur.

```text
Utilisateur
  ↓
Surfaces
  └── Projections
        ↓
Services — TypeScript
  ├── Repositories
  ├── Lambdas
  └── Runtimes
        ↓
Workflows
        ↓
Apps — Zig + TypeScript
  ├── Fujin
  ├── Centimanus
  ├── Resonus
  ├── Behemoth
  ├── Ptah
  └── Cruller
        ↓
Kubernetes
  ↓
Edge / Serveur / Cluster
```

### Surfaces et Projections

Une **Surface** est un espace de travail utilisateur organisé autour d’un contexte de travail spécifique. Elle rassemble les données, les actions et les vues nécessaires pour travailler dans un domaine particulier.

Une Surface ne doit pas nécessairement correspondre à un seul Service. Elle peut combiner des données et des actions provenant de plusieurs Repositories, Lambdas, Runtimes et Workflows.

Une **Projection** est un écran individuel au sein d’une Surface, conçu pour remplir une fonction spécifique. Elle présente les données sous une forme pratique pour l’utilisateur et fournit les actions requises.

L’interface est donc organisée autour de **ce avec quoi l’utilisateur travaille**, plutôt qu’autour de la structure interne des Services.

### Services

La logique métier de Converged est écrite en TypeScript et divisée en plusieurs types de Services.

Les **Repositories** encapsulent l’accès aux données. Ils fournissent une interface permettant de lire, modifier et interroger les données tout en masquant le mécanisme de stockage sous-jacent.

Les **Lambdas** sont des fonctions sans état conçues pour des opérations individuelles telles que le traitement et la transformation des données, le calcul, la validation ou le rôle de passerelles vers des API externes.

Les **Runtimes** fournissent des environnements d’exécution spécialisés pour la logique qui nécessite son propre contexte d’exécution.

Les Services sont les éléments constitutifs du système. Ils n’ont pas besoin de connaître les processus métier dans lesquels ils seront utilisés et peuvent être réutilisés par différentes Surfaces et différents Workflows.

### Workflows

Un **Workflow** combine des Services en un processus métier complet.

Au lieu de relier les Services par des appels directs, un Workflow définit les opérations à effectuer, leur ordre, les étapes pouvant s’exécuter en parallèle, les endroits où le système doit attendre un événement et ce qui doit se produire lorsqu’une opération échoue.

Par exemple :

```text
Commande
  ↓
Paiement
  ↓
Découpage
  ↓
Production
  ↓
Livraison
```

Un Workflow peut utiliser des Repositories pour les opérations sur les données, des Lambdas pour les opérations individuelles et des Runtimes ou des Apps pour les tâches spécialisées.

### Centimanus

**Centimanus est le moteur DAG qui exécute les Workflows.**

Un Workflow est représenté comme un graphe d’opérations, tandis que Centimanus gère son exécution : dépendances entre les étapes, nouvelles tentatives, attente d’événements, opérations parallèles et compensation en cas d’échec.

Chaque exécution produit une piste d’audit indiquant ce qui a été démarré, ce qui s’est terminé, quelles opérations ont été relancées et pourquoi un échec s’est produit.

Cela permet de créer des processus résilients et de longue durée qui préservent leur état d’exécution et peuvent reprendre après un redémarrage.

Les Services restent indépendants, car ils n’ont pas besoin d’être reliés par des chaînes d’appels directs pour mettre en œuvre un processus métier particulier.

### Apps

**Les Apps constituent le fondement de l’infrastructure de Converged.**

Une App est un environnement d’exécution virtuel léger. Son cœur système est écrit en **Zig**, tandis que la logique mutable s’exécute sous forme de **scripts TypeScript**.

Cette séparation maintient l’infrastructure critique dans un cœur compact et performant tout en conservant la flexibilité de TypeScript pour la logique applicative et la configuration.

Les Apps fournissent les capacités d’infrastructure utilisées par le reste du système :

* **Fujin** — réseau de communication pour les commandes, les événements, les WebSockets et la télémétrie machine.
* **Centimanus** — traitement DAG et exécution des Workflows.
* **Resonus** — passerelle temps réel pour la voix, les médias, la transcription et les fournisseurs d’IA.
* **Behemoth** — stockage multiple isolé pour différents types de données.
* **Ptah** — gestion du déploiement et de la topologie Kubernetes.
* **Cruller** — environnement d’exécution dans lequel s’exécutent les modules d’interface utilisateur et TypeScript.

Les Apps ne constituent pas une couche supplémentaire de logique métier. Elles fournissent les **infrastructures et environnements d’exécution** dans lesquels fonctionne la couche TypeScript.

### Fujin

**Fujin est le réseau unifié pour les commandes, les événements et la télémétrie.**

Tous les composants du système communiquent via Fujin au lieu de s’appeler directement. Une commande provenant de l’interface, un événement de Workflow, une mesure de capteur machine ou une mise à jour de l’avancement de la production passent tous par la même couche de communication.

Les WebSockets transmettent les changements à l’interface en temps réel, sans interrogation périodique.

Comme les communications passent par une couche unique, elles peuvent être suivies, rejouées et limitées en débit de manière centralisée.

**Résultat :** les Services restent indépendants, le temps réel devient une partie de l’infrastructure commune et les événements système deviennent observables.

### Resonus

**Resonus est une interface temps réel unifiée pour la voix, les médias et l’IA.**

Elle combine les appels téléphoniques, les flux audio, la transcription et les adaptateurs de fournisseurs d’IA au sein d’une même couche.

Une conversation peut passer d’un appel téléphonique à la transcription, puis à l’analyse par l’IA, sans transiter entre des systèmes distincts. Les médias peuvent être directement associés aux commandes, aux équipements et aux événements.

Les adaptateurs de fournisseurs isolent le système des fournisseurs individuels de services vocaux et d’IA.

**Résultat :** la voix, les médias et l’IA deviennent partie intégrante de l’environnement commun des Workflows, tandis que les fournisseurs peuvent être remplacés sans restructurer la logique applicative.

### Behemoth

**Behemoth est le système unifié de stockage multiple pour les données de Converged.**

Les différents types de données disposent d’un stockage approprié : SQL pour les commandes et les clients, fichiers pour les modèles et les documents, vecteurs pour la recherche IA, cache pour l’état chaud, ainsi que d’autres types de stockage spécialisés lorsque cela est nécessaire.

L’isolation est structurelle : les données de différents espaces de travail ne sont pas mélangées et peuvent être mises à l’échelle, sauvegardées et déplacées indépendamment.

Le même modèle fonctionne dans les déploiements Edge, Server et Cluster. Sur un petit appareil Edge, tous les domaines de stockage peuvent résider sur un seul nœud ; dans un Cluster, ils peuvent être répartis sur du matériel de stockage spécialisé.

**Résultat :** les données sont isolées par construction, tandis que l’infrastructure de stockage peut évoluer avec l’installation sans modifier la couche applicative.

### Ptah

**Ptah est l’orchestrateur de déploiement de Converged au-dessus de Kubernetes.**

Il gère le placement des Apps, des conteneurs et des données en fonction de la topologie de déploiement : Edge, Server ou Cluster.

Le cœur de Ptah est écrit en Zig, tandis que les règles de gestion sont implémentées sous forme de scripts TypeScript. Le placement, l’ordre de déploiement, le basculement et la logique de distribution des données peuvent ainsi évoluer sans reconstruire le cœur.

Le même mécanisme est utilisé pour différents types d’installation — d’un nœud Edge unique à un cluster distribué.

**Résultat :** l’ensemble du système est géré par une couche de déploiement unifiée, tandis que la logique de déploiement reste dynamique et modifiable.

### Cruller

**Cruller est l’environnement d’exécution de l’interface utilisateur et des modules TypeScript.**

Il fournit l’environnement dans lequel s’exécute la logique TypeScript de Converged, notamment l’interface utilisateur et les modules applicatifs.

Cruller relie la couche TypeScript dynamique aux capacités d’infrastructure fournies par les Apps, ce qui permet à la couche applicative d’évoluer sans modifier le cœur de bas niveau.

### Kubernetes et topologie

Toutes les Apps et les composants associés sont déployés via **Kubernetes**.

Converged utilise le même modèle architectural quelle que soit l’échelle de l’installation :

```text
Edge
  → nœud unique

Server
  → serveur unique avec davantage de ressources

Cluster
  → plusieurs nœuds et stockage distribué
```

La topologie physique change, mais le modèle applicatif ne change pas. Les Services, les Workflows, les Surfaces et les Projections fonctionnent de la même manière, que le système soit exécuté sur un appareil Edge ou au sein d’un cluster complet.

### Modèle unifié

Les différentes parties de Converged sont organisées autour de responsabilités distinctes :

**Surface** — contexte de travail utilisateur.
**Projection** — fonction spécifique et représentation visuelle correspondante.
**Repository** — accès aux données.
**Lambda** — opération individuelle sans état.
**Runtime** — environnement d’exécution spécialisé.
**Workflow** — processus métier qui combine des Services.
**Apps** — environnements d’exécution de l’infrastructure dotés d’un cœur Zig et de TypeScript à l’intérieur.
**Fujin** — communication et événements.
**Centimanus** — exécution des Workflows.
**Resonus** — voix, médias et IA en temps réel.
**Behemoth** — stockage.
**Ptah** — déploiement et gestion de Kubernetes.
**Cruller** — environnement d’exécution de l’interface utilisateur et de TypeScript.

Le principe central de Converged consiste à **séparer le contexte utilisateur, la logique applicative et l’infrastructure sans les contraindre à adopter la même structure**.

Une Surface peut combiner plusieurs Services. Un Workflow peut combiner plusieurs opérations. Et plusieurs Workflows et Services peuvent utiliser les mêmes Apps sous-jacentes.

Il en résulte un système qui reste modulaire au niveau de la logique métier, compact au niveau de l’infrastructure et unifié du point de vue de l’utilisateur.

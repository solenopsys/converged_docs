## Déploiement

Converged prend en charge plusieurs scénarios de déploiement — des appareils edge compacts et des serveurs locaux jusqu’à une infrastructure cloud desservant de nombreuses entreprises indépendantes. La plateforme de base fonctionne sur **k3s**, une distribution Kubernetes légère adaptée aux micro-ordinateurs, aux infrastructures locales et aux clusters cloud.

Il existe trois principaux profils de déploiement :

* **Mono** — l’interface utilisateur, les Services, le stockage et le cache fonctionnent dans une configuration compacte sur une seule machine. Ce profil convient parfaitement aux **micro-ordinateurs tels que Raspberry Pi et Orange Pi**, aux appareils edge, aux petits serveurs locaux, au développement, aux prototypes et aux démonstrations.
* **Multi** — le système est distribué sur plusieurs machines au sein d’un cluster Kubernetes. L’interface utilisateur, les groupes de Services, le stockage et le cache peuvent être déployés et mis à l’échelle indépendamment. Ce profil convient aux environnements de production nécessitant davantage de capacité, une tolérance aux pannes et un contrôle plus précis des ressources.
* **Cloud** — plusieurs entreprises fonctionnent au sein du **même cluster Kubernetes** grâce à une architecture multi-tenant. Chaque **tenant** dispose d’un environnement isolé avec ses propres données, sa configuration et ses ressources, tandis que l’infrastructure sous-jacente du cluster est partagée. Cela permet de servir efficacement de nombreuses entreprises sans nécessiter un cluster distinct pour chaque client.

Les trois profils utilisent la même base de code. Seules la topologie de déploiement et la configuration changent. Un système peut donc commencer comme une installation Mono compacte sur un micro-ordinateur, passer à un cluster Multi lorsque les besoins augmentent ou fonctionner comme un service Cloud partagé par de nombreuses entreprises indépendantes.

Dans un déploiement **auto-hébergé**, l’entreprise contrôle l’installation, le réseau, les sauvegardes, les mises à jour et l’emplacement physique de ses données. Cette option convient aux organisations qui ont besoin d’un contrôle complet de leur infrastructure.

Dans le **Cloud**, l’infrastructure est exploitée de manière centralisée. Plusieurs entreprises partagent le même cluster tout en restant isolées au niveau du tenant, notamment pour leurs données, leur configuration et les ressources qui leur sont allouées.

Un déploiement **hybride** est également possible : les données sensibles et les équipements peuvent rester en local, tandis que le cloud est utilisé pour les mises à jour, l’accès externe, les équipes distribuées ou certaines capacités d’IA.

Le principe essentiel est que **Converged n’enferme pas la plateforme dans un modèle de déploiement unique**. Le même système peut fonctionner sur un petit micro-ordinateur, au sein d’un cluster composé de plusieurs machines ou comme un service Cloud multi-tenant.

## Déploiement

Converged couvre plusieurs scénarios d’installation : du petit atelier au déploiement de production dans l’infrastructure de l’entreprise. La plateforme de base se déploie sur **k3s**, une distribution Kubernetes légère adaptée aux appareils edge, serveurs locaux et environnements cloud.

Il existe deux profils principaux :

- **Mono** — UI, Runtime, microservices, storage et cache sont regroupés de façon compacte. Ce mode sert au développement, aux prototypes, aux démonstrations et aux petites installations où la simplicité de démarrage est prioritaire.
- **Multi** — UI, groupes Runtime, groupes de microservices par domaine, storage et cache sont séparés. C’est le profil production standard lorsque l’isolation, la mise à l’échelle et le contrôle précis de la charge sont nécessaires.

Les deux profils utilisent le même code. Seules la topologie des conteneurs et la configuration changent. Une entreprise peut commencer par une installation compacte puis déplacer le même système vers une infrastructure plus sérieuse sans réécrire le produit.

En self-hosted, le client contrôle l’installation, le réseau, les sauvegardes, les mises à jour et l’emplacement physique des données. Cela convient aux entreprises avec des exigences internes de sécurité ou la volonté de garder la production entièrement chez elles. La livraison cloud retire les tâches opérationnelles : la plateforme est déployée et mise à jour par l’équipe du service, et le client reçoit un environnement prêt.

Une option hybride est aussi possible : les données sensibles et les équipements restent localement, tandis que le cloud sert aux mises à jour, à l’accès externe, à la coordination d’équipes distribuées ou à certaines fonctions IA. Le principe important est de ne pas enfermer le client dans un seul modèle de livraison.

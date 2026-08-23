## Sécurité

Converged part du principe que les données de production ne doivent pas être jetées dans un espace commun. Commandes, fichiers clients, paramètres techniques, paiements, messages et télémétrie des équipements doivent être séparés par workspaces et zones de responsabilité.

Architecturalement, cela repose sur l’isolation des données. Les microservices possèdent leurs stores, et les workspaces peuvent avoir des répertoires, clés, fichiers et limites d’accès séparés. Cela simplifie l’export, la migration self-hosted, les sauvegardes et l’audit.

Les droits d’accès s’appliquent non seulement aux personnes, mais aussi aux agents IA. Si un modèle lance une action, lit des données ou appelle un workflow, cela doit se faire dans son profil de permissions. Les actions sont journalisées, ce qui permet de reconstruire qui ou quel agent a initié une étape, quelles données ont été touchées et comment le scénario s’est terminé.

Les déploiements self-hosted et private donnent au client le contrôle complet de l’infrastructure : réseau, secrets, clés API, sauvegardes et emplacement physique des données. Le mode cloud est plus simple opérationnellement, mais ne doit pas devenir un vendor lock-in : les données doivent rester portables, et les scénarios reproductibles dans une autre installation.

# Architecture du système

Converged est une couche opérationnelle modulaire pour les entreprises de fabrication. Ses interfaces utilisateur, services de domaine, moteur de workflows, stockage, passerelle multimédia et processeurs industriels constituent un seul système sans devenir une seule application.

L’architecture sépare trois types de tâches :

- les modules de domaine possèdent les données métier et les fonctionnalités destinées aux utilisateurs ;
- les services natifs de l’environnement d’exécution acheminent les messages, exécutent les workflows, stockent les données et gèrent les médias en temps réel ;
- le plan de contrôle décide quelles parties s’exécutent pour chaque plateforme et chaque locataire.

## Un seul bus de messages

Les composants d’exécution communiquent via Fujin. Chaque processus ouvre une connexion, enregistre une cible et envoie des messages vers des destinations logiques. L’expéditeur n’a pas besoin de connaître l’adresse ou l’emplacement de déploiement du destinataire.

```text
clients navigateur et mobile
          |
          v
          bus de messages Fujin
       /     |      |      \
      ui     ms  Centimanus Resonus
              \      |      /
               \  Behemoth /
```

Cela supprime le graphe d’appels HTTP et le maillage de services de la couche applicative. Le routage, la corrélation des requêtes et le contexte de locataire approuvé transitent dans l’enveloppe de message commune. Un processus destinataire sélectionne ensuite le service ou le gestionnaire demandé à l’intérieur de sa propre limite.

## Environnement d’exécution central

| Composant | Responsabilité |
| --- | --- |
| Fujin | Connecte les pairs d’exécution et achemine les messages vers le propriétaire actif d’une cible. |
| Behemoth | Fournit un stockage SQL, clé-valeur, en colonnes, vectoriel, graphe et fichiers isolé. |
| Centimanus | Exécute des workflows métier en plusieurs étapes sous forme de graphes rejouables. |
| Resonus | Gère les médias en temps réel, les appels, la transcription et les sessions d’IA. |
| Ptah | Réconcilie la plateforme, les solutions et les locataires souhaités avec les ressources Kubernetes. |

Les composants sont volontairement spécialisés. Fujin ne comprend pas les services métier. Behemoth n’orches tre pas les opérations métier. Centimanus ne possède pas les données de domaine. Resonus ne décide pas de l’identité du locataire. Ptah crée et configure les charges de travail, mais ne participe pas à la messagerie d’exécution.

## Modules et solutions

Les fonctionnalités métier sont fournies sous forme de microservices, de surfaces et de workflows. Une solution est une sélection déclarative de ces modules pour un scénario opérationnel donné, comme la gestion des commandes, la planification de la production ou la surveillance des équipements.

Les microservices possèdent leurs données et exposent des contrats typés. Ils ne s’appellent pas les uns les autres pour coordonner un processus. Les séquences interdomaines appartiennent aux workflows, que Centimanus exécute une étape durable à la fois. Cela maintient les modules de domaine à une taille réduite et permet à une solution de les combiner sans créer de couplage caché.

## Isolation des données

Chaque microservice possède sa propre racine de stockage physique. Behemoth peut servir de nombreuses racines depuis un seul processus, mais il préserve leurs limites de propriété et refuse de créer des données en dehors des montages configurés.

Le même modèle s’adapte aux différents profils de déploiement :

- une installation en périphérie peut exécuter une seule instance Behemoth pour la plateforme ;
- une installation plus importante peut répartir les périmètres entre plusieurs partitions de stockage ;
- une installation cloud peut exécuter une instance de stockage isolée par locataire.

Modifier la topologie ne modifie pas le code applicatif, car les pairs continuent d’adresser des cibles logiques et des limites de stockage.

## Plan de contrôle

Ptah est le plan de contrôle et n’est pas connecté à Fujin. Il observe les ressources Platform, Solution et Tenant déclarées, calcule les charges de travail souhaitées et les réconcilie avec Kubernetes.

```text
Platform + Solutions + Tenants
              |
              v
             Ptah
              |
              v
Déploiements, services, volumes, configuration et routes
```

Cette séparation permet à l’environnement d’exécution de rester concentré sur le trafic métier, tandis que le modèle de déploiement gère le placement, la topologie du stockage, les routes des locataires et le cycle de vie. Les mêmes images applicatives peuvent donc s’exécuter sur un cluster périphérique compact ou dans un environnement cloud multi-locataire.

## Contexte approuvé

Le périmètre du locataire est établi à la périphérie de la plateforme et transporté dans l’enveloppe de message. Les services d’exécution utilisent ce contexte approuvé au lieu de déduire le locataire des charges utiles applicatives. Le placement du stockage, les appels de services et les sessions multimédias préservent tous la même limite de périmètre.

Ensemble, la messagerie logique, le stockage isolé, les workflows rejouables et un plan de contrôle séparé permettent à Converged de rester modulaire sans reporter la complexité des systèmes distribués sur chaque module métier.

# Stockage Behemoth

Behemoth est le socle de stockage natif de Converged. Il fournit plusieurs
modèles de données au moyen d’un même runtime compact, tout en préservant une
frontière de stockage physique distincte pour chaque microservice.

## Stockage pour les services modulaires

Chaque service de domaine possède ses données. Il ne partage ni tables ni
index avec des services sans lien, et n’a pas besoin d’exploiter une pile de
bases de données distincte. Behemoth sert les racines isolées depuis un
processus natif commun et achemine chaque requête vers le magasin approprié.

```text
orders service  -> orders volume  -> SQL and files
calls service   -> calls volume   -> key-value and audio fragments
search service  -> search volume  -> vector index
```

La séparation est physique plutôt qu’une simple convention de nommage. Si la
racine d’un service n’est pas montée et déclarée, Behemoth refuse de créer son
magasin. Une erreur de déploiement devient ainsi immédiatement visible au lieu
d’écrire les données dans le système de fichiers temporaire d’un conteneur.

## Plusieurs modèles de données

Les différentes charges de travail nécessitent des structures différentes.
Behemoth combine le stockage relationnel, clé-valeur, en colonnes, vectoriel,
graphe et fichiers derrière la même frontière de runtime. Un service choisit
le magasin adapté à ses données sans ajouter un nouveau produit de base de
données externe à la plateforme.

Les moteurs restent spécialisés en interne. La couche unifiée est responsable
du cycle de vie, de l’isolation, du transport et des métadonnées, et non de
faire semblant que tous les modèles de données se comportent de la même
manière.

## Placement et mise à l’échelle

Le placement du stockage est indépendant du code applicatif. Une installation
edge peut utiliser un seul processus Behemoth. Les déploiements plus importants
peuvent répartir les périmètres entre plusieurs instances, tandis qu’un profil
cloud peut attribuer à chaque tenant sa propre instance de stockage.

Chaque microservice conserve son propre volume dans chaque profil. Déplacer un
périmètre ou un service vers une autre instance Behemoth modifie la
configuration du déploiement, tandis que les appelants continuent d’utiliser
la même identité logique de stockage.

## Limites de défaillance et de récupération

Les petits magasins appartenant aux services réduisent l’impact de la
corruption, des migrations et des opérations de sauvegarde. Un problème dans
un magasin ne nécessite pas de restaurer une base de données partagée pour
l’ensemble de la plateforme. Les vidages et la récupération peuvent être
traités pour la limite du service concerné, tandis que les services sans lien
continuent de fonctionner.

## Rôle dans le système

Les requêtes de stockage atteignent Behemoth via Fujin, comme les requêtes
destinées à n’importe quel autre pair du runtime. Ptah fournit la disposition
des volumes et la configuration des montages. Behemoth exécute les opérations
de stockage, mais ne coordonne pas les workflows métier, ne sélectionne pas
les tenants et ne définit pas les services qui composent une solution.

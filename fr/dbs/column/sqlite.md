# SQLite

SQLite est le moteur de stockage relationnel qui sous-tend les wrappers de base de données natifs.
Il stocke une base de données dans un fichier local et exécute le SQL dans le processus appelant, ce qui
permet à un service Converged de conserver ses enregistrements, ses index et ses transactions à proximité
du code qui les utilise.

La même connexion SQLite héberge également des tables spécialisées. Stanchion ajoute des tables virtuelles
en colonnes pour les lectures analytiques ; `sqlite-vec` ajoute des tables vectorielles et des requêtes de
distance. Les tables ordinaires et ces extensions peuvent partager une base de données et participer au même
flux de travail au niveau de l'application.

Ce wrapper constitue l'interface SQLite native : il fournit la bibliothèque et le chemin de chargement des
extensions utilisés par l'implémentation du magasin de niveau supérieur.

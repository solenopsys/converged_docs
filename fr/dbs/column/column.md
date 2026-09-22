# Stanchion

Stanchion ajoute des tables en colonnes à SQLite. Il est utilisé lorsqu’un magasin Converged doit lire un petit ensemble de champs parmi de nombreux enregistrements : mesures, historique des événements, journaux et autres données auxquelles on ajoute principalement des éléments. Une table SQLite normale conserve une ligne dans son ensemble ; une table Stanchion conserve chaque colonne dans ses propres segments, de sorte qu’une requête ne lit que les colonnes qu’elle mentionne.

Stanchion est exposé via l’interface des tables virtuelles de SQLite. Une table est déclarée avec `USING stanchion` et une `SORT KEY` ; la clé de tri définit l’ordre physique des enregistrements et permet à l’extension d’ignorer les groupes de lignes qui ne peuvent pas satisfaire un prédicat. Les valeurs sont mises en mémoire tampon en tant qu’insertions en attente, puis écrites dans des segments de colonnes à l’aide des encodages sélectionnés par l’extension.

L’enveloppe compile l’extension pour l’environnement d’exécution SQLite natif. Stanchion est encore un logiciel alpha : son format sur disque et les opérations prises en charge sur les tables ne sont pas encore définis de manière définitive.

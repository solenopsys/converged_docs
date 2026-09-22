# sqlite-vec

`sqlite-vec` ajoute des colonnes vectorielles et des requêtes de recherche des
plus proches voisins aux bases SQLite utilisées par Converged. Une table de
vecteurs peut conserver les représentations vectorielles à côté des champs
qui identifient et décrivent l'objet source, de sorte qu'une requête de
recherche n'a pas besoin de quitter la base uniquement pour classer les
enregistrements similaires.

L'extension fournit des tables virtuelles `vec0` pour les vecteurs flottants,
entiers 8 bits et binaires. Les requêtes renvoient les lignes classées par
distance ; les métadonnées, les colonnes auxiliaires et les clés de partition
restent accessibles dans la même requête SQLite. Cela est utile pour les
chemins de recherche sémantique et de récupération de la plateforme, où le
filtrage et le classement font partie d'une seule opération.

L'enveloppe compile l'extension C en amont comme un artefact natif. SQLite la
charge dans le processus qui détient la base de données ; cette intégration ne
comprend aucun service distinct de recherche vectorielle.

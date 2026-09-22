# LMDBX

LMDBX est le magasin clé-valeur ordonné utilisé lorsque Converged doit accéder directement aux octets plutôt qu'à SQL. Le wrapper ouvre un environnement sur disque et expose les opérations d'ajout, de lecture et de suppression, les transactions et les curseurs via des API Zig et C. Les curseurs permettent d'effectuer des analyses par plage et des itérations ordonnées avec la même primitive de stockage que les recherches ponctuelles.

libmdbx stocke ses arbres B+ dans des fichiers mappés en mémoire et utilise la MVCC pour les lecteurs. Les transactions de lecture voient un instantané stable, tandis qu'un écrivain valide les modifications. Ce modèle convient aux index et à l'état des services qui sont lus fréquemment et mis à jour dans le cadre de transactions courtes.

Le wrapper lie statiquement libmdbx et produit des bibliothèques partagées natives pour les cibles prises en charge. Il s'agit de la couche FFI autour du moteur, et non d'un processus de base de données distinct.

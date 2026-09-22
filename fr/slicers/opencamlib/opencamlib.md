# OpenCAMLib

OpenCAMLib fournit la partie géométrique du flux de génération de trajectoires d'outil CNC dans Converged.
Il utilise la géométrie de surface STL et les paramètres de l'outil pour calculer les
trajectoires de fraisage et les estimations. Alors que CuraEngine construit des trajectoires additives couche par couche,
OpenCAMLib modélise le contact de l'outil avec la pièce pour les opérations
soustractives.

La bibliothèque implémente les opérations drop-cutter, push-cutter et waterline, et
prend en charge les outils cylindriques, sphériques, toroïdaux, coniques et composites. Le
wrapper local expose la petite ABI C nécessaire au flux existant d'estimation du
fraisage STL et compile la bibliothèque C++ amont en tant qu'artefact natif.

OpenCAMLib produit la géométrie des trajectoires d'outil. Son post-traitement dans le dialecte de commandes
d'un contrôleur particulier, puis son exécution sur une machine, relèvent des flux
CAM et équipements qui suivent.

# PARAMS

PARAMS extrait les valeurs dont une commande a besoin à partir de la demande de l'utilisateur. Il s'exécute
après que CASE a reconnu la commande. Pour « show order 4815 », CASE sélectionne la
commande de commande et PARAMS renvoie le numéro de commande. L'application peut alors
ouvrir l'écran de la commande avec ce numéro déjà appliqué.

La commande fournit les paramètres qu'elle accepte et, le cas échéant, les
valeurs disponibles qui peuvent être nommées dans le texte. PARAMS utilise le modèle
ONNX GLiNER2 pour trouver les valeurs dans la demande et les associer à ces paramètres. Le même
mécanisme gère une valeur directe telle qu'un numéro de commande et un choix nommé
tel qu'un client, un statut ou un équipement.

Ensemble, CASE et PARAMS transforment une demande en une commande et ses arguments.
L'application reçoit les deux parties et effectue la navigation ou
l'action habituelle.

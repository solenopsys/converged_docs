# CASE

CASE interprète la demande d'un utilisateur comme une commande de la plateforme. Il reçoit l'ensemble des commandes que la plateforme peut exécuter ainsi que des exemples des formulations qui expriment chacune d'elles. À partir de « afficher l'équipement », il sélectionne la commande qui ouvre la liste de l'équipement. À partir de « afficher la commande 4815 », il sélectionne la commande qui ouvre une commande.

Le service compare la demande aux exemples de commandes et renvoie la commande sélectionnée avec un score. `EXECUTE` signifie qu'une commande a été reconnue avec suffisamment de certitude pour être exécutée. `AMBIGUOUS` signifie que plusieurs commandes sont trop proches pour pouvoir choisir entre elles. `UNKNOWN` signifie que la demande ne correspond pas à l'ensemble des commandes.

CASE détermine ce que l'utilisateur demande de faire. Il n'extrait pas les détails de cette demande. Lorsqu'une commande en a besoin, PARAMS lit le même texte et renvoie les valeurs nécessaires pour ouvrir ou filtrer le résultat : dans « afficher la commande 4815 », CASE sélectionne la commande de commande et PARAMS extrait `4815`.

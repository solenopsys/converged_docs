# Valkey

Valkey fournit à Converged un service clé-valeur en mémoire. Il est utilisé pour
les données qui bénéficient des commandes et de la sémantique d’expiration de Valkey :
les valeurs mises en cache, les compteurs, l’état de coordination à courte durée de vie
et les autres valeurs partagées qui doivent être lues ou modifiées rapidement.

L’enveloppe compile le serveur fourni en tant que dépendance dans une bibliothèque
native et le démarre dans son propre thread. Le serveur écoute sur l’adresse et le port
locaux configurés ; l’enveloppe communique ensuite avec lui via libvalkey. Son API C
démarre et arrête le serveur, vérifie qu’il est prêt, indique l’utilisation de la mémoire
et exécute les opérations clé-valeur prises en charge.

Cette configuration intégrée désactive les instantanés et l’AOF, utilise une seule base de
données logique et applique la politique d’éviction `allkeys-lru` dans la limite de mémoire
configurée. Ces paramètres rendent le cycle de vie explicite au lieu de dépendre d’une
installation Valkey externe.

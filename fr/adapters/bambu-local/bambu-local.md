# Adaptateur local Bambu Lab

L’adaptateur Bambu Local permet à Converged de fonctionner avec une imprimante Bambu Lab via son interface réseau locale. Il se connecte au point de terminaison MQTT sur TLS de l’imprimante, s’authentifie avec le code d’accès LAN et identifie l’appareil par son numéro de série. Le contrôle de l’impression et la télémétrie restent sur le réseau local ; le Bambu Cloud n’intervient pas dans ce chemin.

L’adaptateur publie des commandes de pause, de reprise, d’arrêt, de JSON brut et de G-code. Il s’abonne aux rapports de l’appareil et transmet, via des rappels, le dernier état, les informations sur l’imprimante, les erreurs et les données de télémétrie de l’impression. Les appelants peuvent également demander un instantané JSON lorsqu’ils ont besoin de l’état actuel de manière synchrone.

La connexion par défaut accepte le certificat autosigné généralement présenté par les imprimantes en mode LAN. L’API de connexion étendue accepte un certificat CA lorsque la vérification du certificat est requise.

# Adaptateur direct UVtools

L’adaptateur UVtools prépare les fichiers pour les imprimantes à résine. Il exécute `UVtoolsCmd`
sur les fichiers tranchés, ce qui lui permet d’inspecter les couches, de valider un fichier, de le réparer,
de le convertir entre les formats pris en charge, d’extraire les miniatures et de signaler les
propriétés du fichier ou les problèmes détectés. Ce travail est effectué avant qu’un fichier ne soit
transmis à un adaptateur d’imprimante.

L’enveloppe conserve UVtools en tant qu’exécutable externe. Son API expose le chemin d’argument brut ainsi que des opérations nommées pour la conversion, l’inspection,
la comparaison, l’extraction de miniatures et le signalement des problèmes. Elle renvoie la sortie
standard, la sortie d’erreur standard, le statut de sortie et l’état de l’adaptateur du processus
enfant à l’appelant.

UVtools doit lui-même être installé sur l’hôte. L’enveloppe fournit la frontière du processus : délai
d’expiration de la commande, répertoire de travail, limites de sortie et capture du résultat.

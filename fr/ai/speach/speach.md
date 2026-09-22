# SPEACH

SPEACH constitue le chemin d’entrée vocale local de Converged. Il transforme l’audio du microphone et des appels en un texte identique à celui que CASE et PARAMS reçoivent depuis un clavier. Une instruction parlée peut ainsi suivre le flux normal des commandes et des paramètres sans envoyer l’audio à un service de transcription distant.

Pour une requête enregistrée, SPEACH accepte les fichiers audio WAV ou Opus, les convertit en une forme d’onde mono à 16 kHz, puis exécute le modèle CTC local. Pour une communication en direct, il décode les paquets Opus, utilise la détection d’activité vocale pour recueillir une phrase et émet des événements de transcription partiels et terminés. Les courtes pauses restent à l’intérieur d’une phrase ; le silence la clôt. Un segment est limité à quarante secondes.

La reconnaissance s’arrête au texte. SPEACH ne devine pas à quelle commande d’écran les mots font référence. La transcription est ensuite transmise au même routage contextuel et à la même extraction des paramètres que ceux utilisés pour les entrées saisies au clavier.

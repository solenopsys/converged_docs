# SPEACH

SPEACH es la ruta de entrada de voz local para Converged. Convierte el audio del micrófono y de las llamadas en el mismo texto que CASE y PARAMS reciben desde un teclado. Por lo tanto, una instrucción hablada puede entrar en el flujo normal de comandos y parámetros sin enviar el audio a un servicio remoto de transcripción.

Para una solicitud grabada, SPEACH acepta audio WAV u Opus, lo convierte en una forma de onda mono de 16 kHz y ejecuta el modelo CTC local. Para una conexión en directo, decodifica los paquetes Opus, utiliza la detección de actividad de voz para recopilar una frase y emite eventos parciales y de transcripción completada. Las pausas breves se mantienen dentro de una frase; el silencio la cierra. Un segmento está limitado a cuarenta segundos.

El reconocimiento termina en el texto. SPEACH no intenta adivinar a qué comando de pantalla se refieren las palabras. La transcripción pasa al mismo enrutamiento contextual y extracción de parámetros que se utilizan para la entrada escrita.

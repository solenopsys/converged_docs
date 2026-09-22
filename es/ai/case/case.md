# CASE

CASE interpreta la solicitud de un usuario como un comando de la plataforma. Recibe el conjunto de comandos que la plataforma puede ejecutar y ejemplos de las frases que expresan cada uno. A partir de «show equipment», selecciona el comando que abre la lista de equipos. A partir de «show order 4815», selecciona el comando que abre un pedido.

El servicio compara la solicitud con los ejemplos de comandos y devuelve el comando seleccionado con una puntuación. `EXECUTE` significa que se reconoció un comando con suficiente claridad como para ejecutarlo. `AMBIGUOUS` significa que hay varios comandos demasiado similares para elegir entre ellos. `UNKNOWN` significa que la solicitud no coincide con el conjunto de comandos.

CASE determina qué quiere hacer el usuario. No extrae los detalles de esa solicitud. Cuando un comando los necesita, PARAMS lee el mismo texto y devuelve los valores necesarios para abrir o filtrar el resultado: en «show order 4815», CASE selecciona el comando de pedido y PARAMS extrae `4815`.

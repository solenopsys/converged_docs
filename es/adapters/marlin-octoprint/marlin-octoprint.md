# Adaptador serial de Marlin

El adaptador de Marlin es la ruta serial directa desde Converged hasta una impresora FDM
que ejecuta el firmware Marlin. Abre el puerto serial de la impresora, envía G-code y
realiza un seguimiento de los detalles del protocolo que hacen fiable el flujo de impresión: números de línea,
sumas de comprobación, respuestas `ok` y solicitudes de reenvío.

La API cubre el control de trabajos, el movimiento y el posicionamiento inicial, los calentadores, la extrusión,
las operaciones con la tarjeta SD, la parada de emergencia y el G-code sin procesar. Las respuestas del firmware se analizan para obtener el estado de la impresora: temperaturas, coordenadas, identidad, progreso de la SD y
estado de impresión. Esto permite que la capa de equipos utilice un único modelo de estado mientras el
adaptador continúa comunicándose mediante el protocolo serial del firmware.

El nombre se mantiene por compatibilidad con la API circundante. El envoltorio no ejecuta OctoPrint ni llama a su API HTTP; se comunica directamente con Marlin.

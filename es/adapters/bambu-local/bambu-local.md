# Adaptador local de Bambu Lab

El adaptador local de Bambu permite que Converged funcione con una impresora
Bambu Lab a través de su interfaz de red local. Se conecta al punto final
MQTT sobre TLS de la impresora, se autentica con el código de acceso LAN y
dirige las comunicaciones al dispositivo mediante su número de serie. El
control de impresión y la telemetría permanecen en la red local; Bambu Cloud
no forma parte de esta ruta.

El adaptador publica comandos para pausar, reanudar, detener, enviar JSON sin
procesar y G-code. Se suscribe a los informes del dispositivo y reenvía el
estado más reciente, la información de la impresora, los errores y la
telemetría de impresión mediante callbacks. Los llamadores también pueden
solicitar una instantánea JSON cuando necesiten el estado actual de forma
síncrona.

La conexión predeterminada acepta el certificado autofirmado que suelen
presentar las impresoras en modo LAN. La API de conexión extendida acepta un
certificado de CA cuando se requiere la verificación del certificado.

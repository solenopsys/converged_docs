# MTConnect CppAgent

Este envoltorio ejecuta el agente C++ de MTConnect para Converged. El agente recibe
señales de los adaptadores de máquina configurados y las publica como un flujo de
datos MTConnect. Proporciona a los equipos CNC, robots, sensores y otros
dispositivos de planta un modelo común que el resto de la plataforma puede consumir.

El envoltorio inicia `cppagent` con un `agent.cfg`, espera hasta que su punto final HTTP
esté listo y detiene el proceso cuando se libera el servicio. El XML del dispositivo
describe el modelo del equipo; la configuración del agente selecciona los adaptadores,
los puertos y las opciones de ejecución. Los clientes leen los puntos finales
`/probe`, `/current` y `/sample` resultantes del agente en ejecución.

La integración se basa deliberadamente en procesos. Utiliza la configuración nativa
del agente y su interfaz HTTP en lugar de integrar su biblioteca C++ en el
entorno de ejecución de Zig.

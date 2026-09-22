# OpenCAMLib

OpenCAMLib proporciona la parte geométrica del flujo de generación de trayectorias CNC en Converged.
Trabaja con geometría de superficies STL y parámetros de la herramienta para calcular
trayectorias de fresado y estimaciones. Mientras CuraEngine construye trayectorias aditivas capa por capa,
OpenCAMLib modela el contacto de la herramienta con la pieza de trabajo para operaciones
sustractivas.

La biblioteca implementa operaciones de drop-cutter, push-cutter y waterline, y
admite herramientas cilíndricas, de bola, bull, cónicas y compuestas. El
wrapper local expone la pequeña ABI de C necesaria para el flujo existente de
estimación de fresado STL y compila la biblioteca C++ original como un artefacto nativo.

OpenCAMLib produce geometría de trayectorias de herramienta. El posprocesamiento para convertirla en el dialecto de comandos
de un controlador específico y su posterior ejecución en una máquina corresponden a las rutas de CAM y
equipamiento que siguen.

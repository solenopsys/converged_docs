# CuraEngine

CuraEngine prepara trabajos FDM y FFF para Converged. Dado un modelo y un perfil
de impresora, divide la geometría en capas, genera paredes, relleno y
trayectorias de soporte, y luego escribe el código G que ejecuta una impresora
de extrusión de material. Es el laminador del ecosistema de Cura, utilizado
aquí sin la interfaz de escritorio.

El envoltorio nativo ejecuta `CuraEngine slice` en un directorio temporal aislado
y devuelve el código G generado a través de su ABI de C. Ejecutar el laminador
fuera del proceso contiene su estado global y sus rutas de fallo, de modo que un
modelo o perfil no válido no detiene el procesador que solicitó el laminado.

El envoltorio prepara un trabajo; no envía código G a una impresora. El envío y
la ejecución se gestionan posteriormente mediante el adaptador de equipo
correspondiente.

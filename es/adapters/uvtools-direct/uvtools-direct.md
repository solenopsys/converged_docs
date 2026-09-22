# Adaptador directo de UVtools

El adaptador de UVtools prepara archivos para impresoras de resina. Ejecuta `UVtoolsCmd`
contra archivos laminados, donde puede inspeccionar capas, validar un archivo, repararlo,
convertirlo entre formatos compatibles, extraer miniaturas e informar sobre las
propiedades del archivo o los problemas detectados. Este trabajo se realiza antes de
entregar un archivo a un adaptador de impresora.

El envoltorio mantiene UVtools como un ejecutable externo. Su API expone tanto la ruta
de argumentos sin procesar como operaciones con nombre para la conversión, inspección,
comparación, extracción de miniaturas y generación de informes de problemas. Devuelve
al llamador la salida estándar, el error estándar, el estado de salida y el estado del
adaptador del proceso hijo.

UVtools debe estar instalado en el host. El envoltorio proporciona el límite del proceso:
el tiempo de espera del comando, el directorio de trabajo, los límites de salida y la
captura del resultado.

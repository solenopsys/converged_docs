# SQLite

SQLite es el motor de almacenamiento relacional que sustenta los envoltorios nativos de bases de datos.
Almacena una base de datos en un archivo local y ejecuta SQL en el proceso que realiza la llamada, lo que
permite que un servicio de Converged mantenga sus registros, índices y transacciones cerca del código que
los utiliza.

La misma conexión de SQLite también sirve de base para tablas especializadas. Stanchion
añade tablas virtuales columnares para lecturas analíticas; `sqlite-vec` añade tablas vectoriales y consultas
de distancia. Las tablas ordinarias y esas extensiones pueden compartir una base de datos y participar en
el mismo flujo de trabajo a nivel de aplicación.

Este envoltorio es el límite nativo de SQLite: proporciona la biblioteca y la ruta de carga de extensiones
utilizadas por la implementación del almacén de nivel superior.

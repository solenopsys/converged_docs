# sqlite-vec

`sqlite-vec` incorpora columnas vectoriales y consultas de vecinos más cercanos en los almacenes SQLite utilizados por Converged. Una tabla vectorial puede mantener las incrustaciones junto a los campos que identifican y describen el objeto de origen, de modo que una solicitud de búsqueda no tenga que salir del almacén simplemente para clasificar registros similares.

La extensión proporciona tablas virtuales `vec0` para vectores de tipo float, int8 y binarios. Las consultas devuelven las filas ordenadas por distancia; los metadatos, las columnas auxiliares y las claves de partición siguen estando disponibles para la misma consulta SQLite. Esto resulta útil para las rutas de búsqueda semántica y recuperación de la plataforma, donde el filtrado y la clasificación forman parte de una sola operación.

El envoltorio compila la extensión C original como un artefacto nativo. SQLite la carga en el proceso que posee la base de datos; no hay ningún servicio independiente de búsqueda vectorial en esta integración.

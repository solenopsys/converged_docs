# Stanchion

Stanchion añade tablas columnares a SQLite. Se utiliza cuando un almacén Converged
necesita leer un pequeño conjunto de campos en muchos registros: mediciones,
historial de eventos, registros y otros datos orientados a anexos. Una tabla
normal de SQLite mantiene unida cada fila; una tabla de Stanchion mantiene cada
columna en sus propios segmentos, por lo que una consulta solo lee las columnas
que menciona.

Stanchion se expone mediante la interfaz de tablas virtuales de SQLite. Una tabla se
declara con `USING stanchion` y una `SORT KEY`; la clave de ordenación define el
orden físico de los registros y permite a la extensión omitir grupos de filas que
no pueden coincidir con un predicado. Los valores se almacenan en búfer como
inserciones pendientes y luego se escriben en segmentos de columnas utilizando
las codificaciones seleccionadas por la extensión.

El envoltorio compila la extensión para el entorno de ejecución nativo de SQLite. Stanchion sigue siendo
software alfa: su formato en disco y las operaciones de tabla compatibles aún no
están definidos.
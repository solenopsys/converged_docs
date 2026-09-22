# LMDBX

LMDBX es el almacén de clave-valor ordenado que se utiliza cuando Converged necesita acceso directo a los bytes en lugar de SQL. El envoltorio abre un entorno en disco y expone operaciones de inserción, consulta, eliminación, transacciones y cursores mediante APIs de Zig y C. Los cursores hacen que los escaneos por rango y la iteración ordenada formen parte de la misma primitiva de almacenamiento que las búsquedas puntuales.

libmdbx almacena sus árboles B+ en archivos mapeados en memoria y utiliza MVCC para los lectores. Las transacciones de lectura ven una instantánea estable mientras un escritor confirma los cambios. Este modelo es adecuado para índices y estados de servicio que se leen con frecuencia y se actualizan en transacciones breves.

El envoltorio enlaza libmdbx estáticamente y produce bibliotecas compartidas nativas para los destinos compatibles. Es la capa FFI alrededor del motor, no un proceso de base de datos independiente.

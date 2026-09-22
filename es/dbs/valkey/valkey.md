# Valkey

Valkey proporciona a Converged un servicio de valores clave en memoria. Se utiliza para
datos que se benefician de los comandos y la semántica de expiración de Valkey: valores
en caché, contadores, estados de coordinación de corta duración y otros valores
compartidos que deben leerse o modificarse rápidamente.

El envoltorio compila el servidor incluido como una biblioteca nativa y lo inicia en
su propio hilo. El servidor escucha en la dirección local y el puerto configurados;
a continuación, el envoltorio se comunica con él mediante libvalkey. Su API de C
inicia y detiene el servidor, comprueba su disponibilidad, informa del uso de memoria
y ejecuta las operaciones de valores clave compatibles.

Esta configuración integrada deshabilita las instantáneas y AOF, utiliza una única
base de datos lógica y aplica la política de desalojo `allkeys-lru` dentro del límite
de memoria configurado. Estos ajustes hacen explícito el ciclo de vida en lugar de
heredarlo de una instalación externa de Valkey.

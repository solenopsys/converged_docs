## Seguridad

Converged parte de la idea de que los datos de producción no deben colocarse en un montón compartido. Pedidos, archivos de clientes, parámetros tecnológicos, pagos, mensajes y telemetría de equipos deben separarse por workspaces y zonas de responsabilidad.

Arquitectónicamente, esto se sostiene mediante aislamiento de datos. Los microservicios poseen sus almacenes, y los workspaces pueden tener directorios, claves, archivos y límites de acceso separados. Esto simplifica exportación, migración self-hosted, backups y auditoría.

Los derechos de acceso se aplican no solo a personas, sino también a agentes de IA. Si un modelo lanza una acción, lee datos o llama un workflow, debe hacerlo dentro de su perfil de permisos. Las acciones se registran, por lo que se puede reconstruir quién o qué agente inició un paso, qué datos fueron afectados y cómo terminó el escenario.

Los despliegues self-hosted y private dan al cliente control completo sobre la infraestructura: red, secretos, API keys, backups y ubicación física de los datos. El modo cloud es más sencillo operativamente, pero no debe convertirse en vendor lock-in: los datos deben seguir siendo portables y los escenarios reproducibles en otra instalación.

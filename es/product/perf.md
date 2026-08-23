## Rendimiento

Converged está diseñado para plantas de producción que no siempre tienen un gran parque de servidores. Por eso el sistema evita peso innecesario: Bun reduce el overhead de procesos backend, Runtime permanece stateless y los microservicios pueden agruparse por tipo de carga en lugar de ejecutar cientos de contenedores separados.

El rendimiento se logra por arquitectura, no por un solo truco. Los datos no pasan por capas innecesarias, los servicios poseen sus almacenes, Runtime paraleliza workflows y tareas cron, y los adaptadores nativos se usan donde HTTP o una capa JS normal añadirían demasiado overhead.

Una instalación compacta puede funcionar en un servidor pequeño o single-board computer si la carga corresponde al tamaño del taller. Al crecer, se pueden separar Runtime, microservicios y grupos de storage para usar más núcleos CPU, aislar tareas pesadas y evitar que un cuello de botella detenga todo el sistema.

La plataforma no promete rendimiento infinito “out of the box”. Los cuellos de botella dependen del equipo, volumen de archivos, número de pedidos, proveedores de IA e integraciones. La arquitectura de Converged permite empezar de forma compacta y escalar solo las partes que realmente se calientan.

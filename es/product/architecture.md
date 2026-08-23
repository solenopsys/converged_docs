## Arquitectura

Converged está diseñado como una plataforma modular, pero no como una colección caótica de microservicios. La separación es simple: la interfaz muestra datos y lanza acciones, Runtime ejecuta procesos, los microservicios poseen datos y los adaptadores conectan equipos y sistemas externos.

```text
Usuario / cliente
        ↓
UI y micro-frontends
        ↓
Runtime: workflows, cron, integraciones, acciones de IA
        ↓
Microservicios: APIs tipadas y datos propios
        ↓
Storage / Behemoth / archivos / SQL / KV / métricas
        ↓
Equipos, mensajeros, pagos y servicios externos
```

Los microservicios se mantienen deliberadamente delgados. Cada servicio responde por su área de datos, validación y API tipada. No debe conocer la lógica interna de servicios vecinos ni convertirse en un centro oculto de procesos de negocio. Esto reduce el acoplamiento y simplifica el mantenimiento.

Toda la lógica transversal se traslada a Runtime. Si el sistema debe aceptar un pedido, consultar varios servicios, crear una tarea, enviar una notificación, esperar un evento y actualizar un estado, eso se ejecuta en un workflow. Runtime no guarda estado persistente por sí mismo: escribe historial, variables y resultados a través de los servicios que poseen sus almacenes.

El almacenamiento se construye alrededor del aislamiento. En lugar de una base común, cada dominio obtiene sus propios límites de datos: SQL, key-value, archivos, datos columnares, índices vectoriales o relaciones de grafo donde sea necesario. Este enfoque ayuda a mover workspaces, limitar el acceso y evitar una base compartida donde se mezclen datos de distintos clientes.

El frontend también es modular. La shell común carga micro-frontends independientes mediante import map, por lo que partes concretas de la interfaz pueden evolucionar sin recompilar todo el producto. Para el usuario sigue siendo un solo sistema; para el desarrollo, un conjunto de zonas de responsabilidad claras.

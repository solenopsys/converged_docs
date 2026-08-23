## Tecnologías

La parte servidor de Converged está construida sobre **Bun** y **Elysia**. Bun arranca JavaScript y TypeScript rápidamente, usa memoria de forma eficiente y encaja bien en despliegues edge compactos. Elysia se utiliza como capa HTTP para plugins backend y microservicios.

Los contratos entre servicios se describen con tipos. NRPC vincula interfaces TypeScript con implementaciones y genera paquetes cliente, para que frontend, Runtime y backend trabajen con los mismos contratos en lugar de APIs de texto desconectadas.

El almacenamiento de datos usa un conjunto de stores ligeros para distintas tareas: SQL, key-value, archivos, datos columnares, índices vectoriales y relaciones de grafo. La capa nativa Behemoth y los adaptadores Zig cubren tareas donde importan el bajo overhead, el acceso a equipos, Unix sockets o FFI.

El frontend está construido como una plataforma React con micro-frontends. La shell común carga módulos UI separados, y los escenarios de producto pueden evolucionar de forma independiente. Esto es importante para una plataforma con muchas soluciones: la interfaz no debe convertirse en un monolito pesado.

La orquestación y la entrega se construyen alrededor de k3s, Helm y perfiles de configuración. El mismo conjunto de componentes puede ensamblarse en un perfil mono compacto o separarse por grupos para producción.

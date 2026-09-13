## El registro de módulos

El registro no es un documento independiente ni una base de datos. Es el propio árbol de fuentes.

```text
modules/
├── microservices/<domain>/ms-<name>    un dominio de datos y su API
├── surfaces/<domain>/sf-<name>   una pantalla montada en tiempo de ejecución
├── workflows/wf-<name>                 un proceso para el entorno de ejecución DAG
├── types/<domain>/                     contratos NRPC
└── solutions/                          qué módulos se distribuyen juntos
```

Un módulo existe porque existe su directorio. Pertenece a un dominio porque se encuentra en la carpeta de ese dominio. Pertenece a una solución porque `solutions/solutions.json` lo nombra. No hay un cuarto lugar donde haya que repetir nada de esto; por eso la página del ecosistema del sitio se genera recorriendo el árbol en lugar de editar una lista.

El propósito de un módulo se toma de su `README.md`: el primer párrafo bajo `## Purpose` (para las superficies, `## UI Purpose`) y el párrafo bajo el encabezado de los límites de responsabilidad. Esos dos párrafos son el contrato del módulo en lenguaje sencillo, y todos los módulos deben proporcionarlos.

Una capa de producto sobre la base —`club`, por ejemplo— se estructura de la misma manera y puede omitir el nivel de dominio: sus módulos se encuentran directamente en `modules/microservices/ms-<name>`. La compilación entiende ambas estructuras.

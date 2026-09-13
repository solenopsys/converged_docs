## Añadir un módulo

Los pasos son los mismos para la plataforma base y para una capa de producto.

1. **Crea el directorio** según la convención: `modules/microservices/<domain>/ms-<name>` para un servicio, `modules/surfaces/<domain>/sf-<name>` para una pantalla, `modules/workflows/wf-<name>` para un proceso.
2. **Declara el contrato** en `modules/types/<domain>/` y genera los clientes con `bun run gen`. El cliente aparece como un paquete `g-<name>`, utilizable desde el navegador, desde otro proceso en el bus y desde dentro de un flujo de trabajo.
3. **Escribe el README** con una sección `## Purpose` y una sección sobre los límites de responsabilidad. El primer párrafo de cada una termina en el registro del sitio; escríbelos para un lector, no para ti.
4. **Añade el módulo a una solución** si no se distribuye por sí solo: incluye su nombre corto en `modules/solutions/solutions.json` y declara sus dependencias.
5. **Reconstruye la documentación**: `bun run build:doc` en la raíz del repositorio. El módulo aparece en el registro y los contadores de la página del ecosistema se vuelven a calcular.

Lo que no tienes que hacer: editar las listas de módulos en los datos del sitio, repetir la descripción en la página de inicio ni registrar el módulo en ningún otro lugar. La generación funciona en un solo sentido: de las fuentes a los datos, nunca al contrario. Todo lo que está bajo `data/` se sobrescribe con la siguiente compilación.

Lo que la revisión exige a un módulo: que no acceda al almacenamiento de otro módulo, que no evite el bus mediante llamadas directas, que declare únicamente los permisos que realmente utiliza y que no amplíe silenciosamente su área de responsabilidad.

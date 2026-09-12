# Interfaz de línea de comandos convergente

La CLI convergente es un motor de comandos orientado a los operadores. Proporciona una única
superficie de comandos coherente para diagnósticos de la plataforma, automatización, almacenamiento y
operaciones de dominio, al tiempo que permite que cada capacidad permanezca en su propio módulo
de comandos.

## Superficie de comandos modular

El núcleo de la CLI no contiene un registro fijo de comandos de negocio. Al iniciarse,
lee uno o más directorios pasados mediante `--commands` y carga el módulo TypeScript
seleccionado para cada sección de comandos. Un módulo exporta una fábrica
que devuelve un procesador; el procesador declara sus comandos y enruta cada
nombre de comando a un controlador.

```text
bun cli <section> <command> [param]
          |          |
          |          +-> command handler
          v
  command module -> processor -> generated NRPC client
```

Esto hace que la CLI sea extensible sin cambiar su tiempo de ejecución. Una solución o
producto puede añadir un directorio de comandos, y un nuevo módulo `<section>.ts` se convierte en una
nueva sección de la CLI. El núcleo carga únicamente la sección solicitada para su ejecución, por lo que un
módulo opcional o defectuoso no puede impedir que se ejecuten comandos no relacionados.

`BaseCommandProcessor` proporciona el mapa de comandos común, la salida de ayuda, la
propagación de errores y un comportamiento de listado coherente. Los módulos se centran en sus propios
argumentos y acciones de dominio; el ejecutor se encarga de la configuración de la conexión, el ciclo de
vida, los informes, la medición del tiempo, el estado de salida y el cierre del canal.

## Un único modelo de autorización

Todos los módulos de comandos habilitados para NRPC utilizan la misma sesión de CLI y la misma ruta de autorización.
La CLI primero lee el JWT del usuario desde el archivo de sesión local y luego recurre a
`SERVICE_TOKEN` cuando no hay una sesión disponible. La sesión del usuario tiene
prioridad porque las acciones del operador pueden requerir la identidad del autor de la llamada.

El token se envía durante el handshake compartido de Fujin WebSocket y también se
proporciona a la configuración del cliente NRPC. Si se rechaza una sesión almacenada, el
ejecutor la elimina de la conexión activa y reintenta una vez con el token de servicio cuando este está configurado.
Los errores de autenticación se informan de manera uniforme,
con indicaciones para volver a iniciar sesión, en lugar de dejar que cada módulo de comandos
gestione por sí mismo el estado del token.

La autorización sigue siendo aplicada por el servicio receptor. La CLI transporta
las credenciales del autor de la llamada y el ámbito del espacio de trabajo; no interpreta los permisos
ni concede acceso localmente. Un comando puede omitir el canal WebSocket únicamente
cuando se comunica deliberadamente con un endpoint que no es NRPC, como una operación de diagnóstico directa.

## Integración con NRPC

Los módulos de comandos crean clientes a partir de paquetes `g-<service>` generados y les pasan
la configuración compartida `createCliNrpcClientConfig`. NRPC serializa la
llamada al método tipado en una solicitud WebSocket, dirigida a un destino lógico de Fujin
y a un servicio. Fujin la reenvía al par de tiempo de ejecución activo, y el servicio
aplica su política de acceso normal antes de ejecutar el método.

El mismo canal admite métodos ordinarios de solicitud-respuesta y métodos de transmisión.
Los identificadores de solicitud, los plazos, el orden de las respuestas y la gestión de fallos de conexión
se centralizan en el canal de la CLI, por lo que cada módulo obtiene el mismo comportamiento sin
reimplementar el código del protocolo.

## Límite de responsabilidades

La CLI se encarga del descubrimiento de comandos, el ciclo de vida de la ejecución de comandos, la selección
de la sesión local y el canal común de cliente NRPC/WebSocket. No se encarga de la lógica de
negocio del dominio, las decisiones de permisos, la implementación del servicio ni el enrutamiento de Fujin.
Esas responsabilidades permanecen en los módulos de comandos, los servicios backend y la
infraestructura de tiempo de ejecución que recibe la llamada.

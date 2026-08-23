# Product

- [Plataforma Converged AI](#plataforma-converged-ai)
- [Qué hace Converged](#qué-hace-converged)
- [Sistema de soluciones](#sistema-de-soluciones)
- [Equipos y taller](#equipos-y-taller)
- [Procesos](#procesos)
- [Capa de IA](#capa-de-ia)
- [Arquitectura](#arquitectura)
- [Despliegue](#despliegue)
- [Tecnologías](#tecnologías)
- [Rendimiento](#rendimiento)
- [Seguridad](#seguridad)
- [Licenciamiento](#licenciamiento)
- [Comunidad](#comunidad)
- [Código fuente](#código-fuente)

## Plataforma Converged AI

**Converged AI** es una plataforma open-source para empresas manufactureras: bureaus de impresión 3D, talleres CNC, laboratorios de I+D y redes de pequeños talleres.

Su tarea es asumir todo lo que ocurre alrededor de la producción: solicitudes, archivos, estimaciones, colas, estados de pedidos, comunicación con clientes, equipos, pagos, entrega y ventas recurrentes. Las máquinas siguen fabricando piezas, el equipo sigue tomando decisiones de ingeniería, y Converged conecta todo en un sistema gestionable.

La plataforma incluye **17 soluciones** agrupadas en cuatro áreas: pedidos y clientes, producción e inventario, dinero y rentabilidad, equipo y responsabilidad. No son “módulos por tener módulos”, sino escenarios listos para problemas concretos del taller.

![Panel de Converged AI](/dashboard_ru.png)

## Qué hace Converged

### Qué hace Converged

Una empresa manufacturera tiene dos capas de trabajo. La primera es fabricar la pieza, ensamblar el producto y completar el pedido. La segunda es todo lo que debe ocurrir antes, durante y después de la producción: aceptar una solicitud, no perder el archivo, acordar el precio, poner el trabajo en cola, avisar al cliente, entender la carga de las máquinas, detectar retrasos y cobrar.

Converged cubre esa segunda capa. Es un circuito digital de control que conecta el sitio web, las solicitudes de clientes, las tareas internas, el equipo, el inventario, los pagos, las notificaciones y la analítica. El propietario ve no un conjunto de herramientas desconectadas, sino una imagen viva del negocio: qué entró, qué fue aceptado, qué está en cola, qué está listo, dónde hay riesgo de retraso y dónde se pierde margen.

La plataforma es especialmente útil cuando la producción ya funciona, pero la gestión depende de chats, hojas de cálculo, memoria de empleados y control manual. Converged no obliga a implantar de inmediato un ERP o MES pesado. Empieza con procesos concretos y construye gradualmente un sistema unificado alrededor de ellos.

En un escenario típico, el cliente deja una solicitud a través del sitio, un formulario, un mensajero o un operador. Converged guarda la solicitud, adjunta archivos, crea un pedido, ayuda a estimar el precio, coloca el trabajo en la cola, sigue la ejecución y mantiene informado al cliente. Un operador puede preguntar el estado en la interfaz o mediante el chat de IA, y el sistema responde con datos reales, no con suposiciones.

Como resultado, el taller depende menos de la coordinación manual. Las personas se concentran en la producción y en decisiones que realmente requieren experiencia, mientras la plataforma se encarga del enrutamiento, el control de plazos, los mensajes repetitivos, la recopilación de estados y la preparación de acciones.

## Sistema de soluciones

### Sistema de soluciones

Converged no se vende como una plataforma vacía donde el cliente primero debe inventar la arquitectura y ensamblar módulos. La unidad básica de valor es una **solución**: un escenario de trabajo listo que cierra un problema claro del negocio.

La plataforma incluye **17 soluciones** agrupadas en cuatro áreas:

- **Pedidos y clientes** — solicitudes entrantes, vitrina de servicios, historial del cliente, estados, comunicación y ventas recurrentes.
- **Producción e inventario** — carga de equipos, colas, materiales, control de calidad, fallos y envíos.
- **Dinero y rentabilidad** — coste, margen, pagos, cuentas por cobrar, precios y escenarios de crecimiento.
- **Equipo y responsabilidad** — zonas de responsabilidad, turnos, estándares, base de conocimiento e incorporación.

Una solución dentro de Converged no es solo una pantalla de interfaz. Normalmente incluye un modelo de datos, workflow, roles, notificaciones, acciones de agente de IA e integraciones con equipos o servicios externos. El propietario no elige una “función”, sino un problema: acelerar la atención de solicitudes, ver la cola de máquinas, entender la rentabilidad de pedidos o ordenar los turnos.

La descripción detallada de todas las soluciones debe vivir en una sección separada. En la documentación del producto, lo importante es fijar el principio: Converged AI es la plataforma, y las soluciones son escenarios aplicados que funcionan dentro de ella y van cerrando distintas zonas del negocio manufacturero.

## Equipos y taller

### Equipos y taller

Converged no sustituye el firmware de la máquina ni intenta controlar la producción a ciegas. Se conecta por encima del equipo, lee telemetría, vincula el estado de las máquinas con los pedidos y muestra lo que realmente ocurre en el taller.

La plataforma está pensada para distintos tipos de equipo: impresoras 3D Bambu Lab, Marlin y Klipper, máquinas CNC, células robóticas y adaptadores especializados. Cuando es posible, Converged recibe estados, errores, progreso de ejecución, temperatura, colas de tareas y otros datos técnicos. Cuando el control directo es arriesgado o no está disponible, el sistema sigue siendo una capa de observación y coordinación.

Para el propietario, esto significa algo simple: el equipo deja de ser un conjunto de ventanas separadas. Se ve qué máquinas están ocupadas, dónde hay inactividad, qué se retrasa, qué pedido está ligado a una operación concreta y dónde debe intervenir un operador. A medida que crece el parque, esta visibilidad se vuelve más importante que cambiar manualmente entre interfaces separadas de impresoras o máquinas.

Converged también conecta el equipo con el proceso de negocio. Una tarea no solo “se imprime” o “se fresa”: está en el contexto de un pedido, plazo, cliente, material, pago y siguiente paso. El taller se convierte en parte del sistema común, no en una isla separada.

## Procesos

### Procesos

El principal problema de un taller que crece rara vez es la falta de un botón más. Con más frecuencia, los procesos viven en la cabeza de las personas: quién debe responder al cliente, cuándo calcular el precio, quién revisa el archivo, cuándo iniciar la producción, a quién avisar si hay retraso y qué hacer después del envío.

En Converged, estas cadenas se describen como workflows. Un proceso típico puede ir desde la solicitud hasta la estimación, aprobación, puesta en cola, producción, control de calidad, pago, entrega y notificaciones. El usuario normalmente no construye un grafo desde cero: los escenarios listos vienen con las soluciones, y la configuración se reduce a reglas, roles, plazos, integraciones y notificaciones.

Técnicamente, la ejecución se traslada a la capa Runtime. Esta ejecuta workflows, tareas cron, pasos de integración y lógica de negocio, permaneciendo stateless: los datos persistentes quedan en los microservicios, y Runtime responde por ejecutar las cadenas. Así la lógica de negocio no queda dispersa por decenas de servicios y existe un lugar claro donde viven las reglas del proceso.

Para implantaciones complejas, los workflows pueden ampliarse. Un desarrollador describe escenarios como clases TypeScript tipadas, y los agentes de IA pueden lanzar acciones permitidas dentro de esos escenarios. Pero para un usuario normal, el objetivo es otro: no construir un editor, sino activar un proceso listo y obtener un resultado gestionado.

## Capa de IA

### Capa de IA

La IA en Converged no es un chat separado añadido por apariencia. Es una capa de control sobre los datos, la interfaz y los procesos. El usuario puede preguntar qué ocurre con un pedido, pedir una respuesta para el cliente, encontrar un retraso, lanzar un workflow permitido o recopilar un resumen de carga de máquinas.

El modelo recibe contexto de la plataforma: solicitudes, estados, archivos, telemetría, historial del cliente, derechos de acceso y tareas actuales. Por eso la respuesta se basa en datos de la empresa, no en razonamientos genéricos. Si hace falta una acción, la IA no evita el sistema directamente: llama funciones, microservicios o workflows permitidos a través de una capa controlada.

Los proveedores de modelos se conectan mediante adaptadores. Una misma instalación puede usar GPT, Claude, DeepSeek, Mistral, Gemini u otros motores si encajan con la tarea y la política del cliente. Un modelo puede comunicarse con clientes, otro analizar requisitos técnicos y otro revisar documentos o estados de producción.

El principio clave es el control. La IA tiene su propio perfil de acceso, todas las acciones se registran y las operaciones críticas se ejecutan con los mismos derechos y políticas que las acciones humanas. Esto permite confiar la rutina a los agentes sin darles poder incontrolado sobre la producción.

## Arquitectura

### Arquitectura

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

## Despliegue

### Despliegue

Converged está preparado para varios escenarios de instalación: desde un pequeño taller hasta un despliegue de producción en la infraestructura de una empresa. La plataforma base se despliega sobre **k3s**, una distribución ligera de Kubernetes adecuada para dispositivos edge, servidores locales y entornos cloud.

Hay dos perfiles principales:

- **Mono** — UI, Runtime, microservicios, storage y cache se empaquetan de forma compacta. Es el modo para desarrollo, prototipos, demostraciones e instalaciones pequeñas donde importa más la simplicidad de arranque.
- **Multi** — UI, grupos de Runtime, grupos de microservicios por dominio, storage y cache se separan. Es el perfil estándar de producción cuando se necesitan aislamiento, escalado y control más preciso de la carga.

Ambos perfiles usan el mismo código. Solo cambian la topología de contenedores y la configuración. Una empresa puede empezar con una instalación compacta y después mover el mismo sistema a una infraestructura más seria sin reescribir el producto.

En escenarios self-hosted, el cliente controla instalación, red, backups, actualizaciones y ubicación física de los datos. Esto encaja con empresas que tienen requisitos internos de seguridad o quieren mantener la producción completamente de su lado. La entrega cloud elimina el trabajo operativo: la plataforma se despliega y actualiza por el equipo del servicio, mientras el cliente recibe un entorno listo.

También es posible un enfoque híbrido: los datos sensibles y el equipo permanecen localmente, mientras la nube se usa para actualizaciones, acceso externo, coordinación de equipos distribuidos o funciones de IA concretas. El principio importante es no atar al cliente a un único modelo de entrega.

## Tecnologías

### Tecnologías

La parte servidor de Converged está construida sobre **Bun** y **Elysia**. Bun arranca JavaScript y TypeScript rápidamente, usa memoria de forma eficiente y encaja bien en despliegues edge compactos. Elysia se utiliza como capa HTTP para plugins backend y microservicios.

Los contratos entre servicios se describen con tipos. NRPC vincula interfaces TypeScript con implementaciones y genera paquetes cliente, para que frontend, Runtime y backend trabajen con los mismos contratos en lugar de APIs de texto desconectadas.

El almacenamiento de datos usa un conjunto de stores ligeros para distintas tareas: SQL, key-value, archivos, datos columnares, índices vectoriales y relaciones de grafo. La capa nativa Behemoth y los adaptadores Zig cubren tareas donde importan el bajo overhead, el acceso a equipos, Unix sockets o FFI.

El frontend está construido como una plataforma React con micro-frontends. La shell común carga módulos UI separados, y los escenarios de producto pueden evolucionar de forma independiente. Esto es importante para una plataforma con muchas soluciones: la interfaz no debe convertirse en un monolito pesado.

La orquestación y la entrega se construyen alrededor de k3s, Helm y perfiles de configuración. El mismo conjunto de componentes puede ensamblarse en un perfil mono compacto o separarse por grupos para producción.

## Rendimiento

### Rendimiento

Converged está diseñado para plantas de producción que no siempre tienen un gran parque de servidores. Por eso el sistema evita peso innecesario: Bun reduce el overhead de procesos backend, Runtime permanece stateless y los microservicios pueden agruparse por tipo de carga en lugar de ejecutar cientos de contenedores separados.

El rendimiento se logra por arquitectura, no por un solo truco. Los datos no pasan por capas innecesarias, los servicios poseen sus almacenes, Runtime paraleliza workflows y tareas cron, y los adaptadores nativos se usan donde HTTP o una capa JS normal añadirían demasiado overhead.

Una instalación compacta puede funcionar en un servidor pequeño o single-board computer si la carga corresponde al tamaño del taller. Al crecer, se pueden separar Runtime, microservicios y grupos de storage para usar más núcleos CPU, aislar tareas pesadas y evitar que un cuello de botella detenga todo el sistema.

La plataforma no promete rendimiento infinito “out of the box”. Los cuellos de botella dependen del equipo, volumen de archivos, número de pedidos, proveedores de IA e integraciones. La arquitectura de Converged permite empezar de forma compacta y escalar solo las partes que realmente se calientan.

## Seguridad

### Seguridad

Converged parte de la idea de que los datos de producción no deben colocarse en un montón compartido. Pedidos, archivos de clientes, parámetros tecnológicos, pagos, mensajes y telemetría de equipos deben separarse por workspaces y zonas de responsabilidad.

Arquitectónicamente, esto se sostiene mediante aislamiento de datos. Los microservicios poseen sus almacenes, y los workspaces pueden tener directorios, claves, archivos y límites de acceso separados. Esto simplifica exportación, migración self-hosted, backups y auditoría.

Los derechos de acceso se aplican no solo a personas, sino también a agentes de IA. Si un modelo lanza una acción, lee datos o llama un workflow, debe hacerlo dentro de su perfil de permisos. Las acciones se registran, por lo que se puede reconstruir quién o qué agente inició un paso, qué datos fueron afectados y cómo terminó el escenario.

Los despliegues self-hosted y private dan al cliente control completo sobre la infraestructura: red, secretos, API keys, backups y ubicación física de los datos. El modo cloud es más sencillo operativamente, pero no debe convertirse en vendor lock-in: los datos deben seguir siendo portables y los escenarios reproducibles en otra instalación.

## Licenciamiento

### Licenciamiento

Converged se distribuye bajo **AGPL-3.0**. Es una licencia copyleft para software de red: si modificas la plataforma y das acceso a ella a través de una red, los cambios deben publicarse según los términos de la licencia.

Para los usuarios, esto significa que la versión self-hosted puede desplegarse sin comprar una licencia por el código en sí. Este camino encaja con empresas que necesitan control, instalación local, auditoría o experimentos en su propio hardware. La responsabilidad operativa queda en el dueño de la instalación: actualizaciones, backups, monitorización, seguridad y disponibilidad.

La entrega cloud no es la venta de código cerrado, sino un servicio alrededor de una plataforma open-source. El cliente paga por arranque rápido, soporte, actualizaciones, backups, monitorización, infraestructura y operación predecible. Para muchos talleres, esto es más barato que crear competencias DevOps internamente.

Este equilibrio es importante para la confianza: el núcleo permanece abierto, la comunidad puede revisar y mejorar la plataforma, y el modelo comercial se construye alrededor de implantación, soporte y entrega controlada de valor.

## Comunidad

### Comunidad

Converged está pensado como una plataforma manufacturera abierta, no como una caja SaaS cerrada. El núcleo base está disponible bajo una licencia open-source, y alrededor pueden aparecer integraciones, microservicios, micro-frontends, workflows y soluciones aplicadas.

Esto importa en el mercado manufacturero: distintos talleres tienen distintos equipos, materiales, estándares de calidad y cadenas de suministro. Un sistema cerrado alcanza rápido los límites de un proveedor concreto. Una arquitectura abierta permite añadir adaptadores y escenarios para condiciones reales.

Una extensión puede ser simple: un nuevo adaptador de equipo, integración con un servicio de pago, importación desde un sitio antiguo, un módulo UI separado o un workflow para una industria concreta. Si la extensión es útil para otros participantes, puede entrar en el catálogo de soluciones o usarse como implantación privada.

Abierto no significa sin control. Las extensiones deben pasar revisión técnica, respetar los límites arquitectónicos y no recibir acceso a datos más amplio del necesario. La confianza en el ecosistema se construye sobre código fuente, reproducibilidad y un modelo claro de permisos.

## Código fuente

### Código fuente

El proyecto se desarrolla abiertamente. El código fuente, la arquitectura actual y los materiales de trabajo están disponibles en el repositorio:

[https://github.com/solenopsys/converged](https://github.com/solenopsys/converged)

El repositorio no es útil solo para desarrolladores. Permite entender cómo están organizados los microservicios, Runtime, micro-frontends, generación de contratos, perfiles de despliegue y adaptadores de hardware. Para empresas que evalúan self-hosted o despliegue privado, esto es parte importante de la revisión: la plataforma no es una caja cerrada.

## Arquitectura

Converged está construido como un entorno de ejecución modular en el que la interfaz, la lógica de negocio y la infraestructura están separadas, aunque operan como un único sistema.

A nivel de usuario, el sistema consta de **Superficies**, que organizan el contexto de trabajo, y **Proyecciones** — pantallas individuales diseñadas para resolver tareas específicas del usuario.

La lógica de negocio se implementa en **TypeScript** mediante varios tipos de **Servicios**: Repositorios, Lambdas y Entornos de ejecución. Los procesos más complejos se ensamblan en **Flujos de trabajo**, que se ejecutan mediante el motor de procesamiento DAG Centimanus.

En la base del sistema se encuentran las **Apps**. Son entornos de ejecución de infraestructura con un núcleo compacto en Zig en el que se ejecutan scripts de TypeScript. Las Apps proporcionan las capacidades fundamentales sobre las que operan los Servicios, los Flujos de trabajo y la UI.

```text
Usuario
  ↓
Superficies
  └── Proyecciones
        ↓
Servicios — TypeScript
  ├── Repositorios
  ├── Lambdas
  └── Entornos de ejecución
        ↓
Flujos de trabajo
        ↓
Apps — Zig + TypeScript
  ├── Fujin
  ├── Centimanus
  ├── Resonus
  ├── Behemoth
  ├── Ptah
  └── Cruller
        ↓
Kubernetes
  ↓
Edge / Servidor / Clúster
```

### Superficies y Proyecciones

Una **Superficie** es un espacio de trabajo del usuario organizado en torno a un contexto de trabajo específico. Reúne los datos, las acciones y las vistas necesarias para trabajar dentro de un área determinada.

Una Superficie no tiene que corresponder a un único Servicio. Puede combinar datos y acciones de varios Repositorios, Lambdas, Entornos de ejecución y Flujos de trabajo.

Una **Proyección** es una pantalla individual dentro de una Superficie, diseñada para realizar una función específica. Presenta los datos de una forma conveniente para el usuario y proporciona las acciones necesarias.

Por tanto, la interfaz se organiza en torno a **con qué está trabajando el usuario**, en lugar de hacerlo alrededor de la estructura interna de los Servicios.

### Servicios

La lógica de negocio de Converged está escrita en TypeScript y dividida en varios tipos de Servicios.

Los **Repositorios** encapsulan el acceso a los datos. Proporcionan una interfaz para leer, modificar y consultar datos, ocultando el mecanismo de almacenamiento subyacente.

Las **Lambdas** son funciones sin estado diseñadas para operaciones individuales, como el procesamiento y la transformación de datos, el cálculo, la validación o la actuación como puertas de enlace hacia APIs externas.

Los **Entornos de ejecución** proporcionan entornos de ejecución especializados para lógica que requiere su propio contexto de ejecución.

Los Servicios son los bloques de construcción del sistema. No necesitan conocer los procesos de negocio en los que se utilizarán y pueden ser reutilizados por distintas Superficies y Flujos de trabajo.

### Flujos de trabajo

Un **Flujo de trabajo** combina Servicios en un proceso de negocio completo.

En lugar de conectar Servicios mediante llamadas directas, un Flujo de trabajo define qué operaciones deben realizarse, en qué orden, qué pasos pueden ejecutarse en paralelo, dónde debe esperar el sistema un evento y qué debe ocurrir cuando una operación falla.

Por ejemplo:

```text
Pedido
  ↓
Pago
  ↓
Corte
  ↓
Producción
  ↓
Entrega
```

Un Flujo de trabajo puede utilizar Repositorios para operaciones de datos, Lambdas para operaciones individuales y Entornos de ejecución o Apps para tareas especializadas.

### Centimanus

**Centimanus es el motor DAG que ejecuta los Flujos de trabajo.**

Un Flujo de trabajo se representa como un grafo de operaciones, mientras que Centimanus gestiona su ejecución: las dependencias entre pasos, los reintentos, la espera de eventos, las operaciones paralelas y la compensación en caso de fallo.

Cada ejecución produce un registro de auditoría que muestra qué se inició, qué se completó, qué operaciones se reintentaron y por qué ocurrió un fallo.

Esto permite crear procesos resilientes y de larga duración que conservan el estado de ejecución y pueden continuar después de un reinicio.

Los Servicios permanecen independientes porque no necesitan conectarse mediante cadenas de llamadas directas para implementar un proceso de negocio concreto.

### Apps

**Las Apps son la base de infraestructura de Converged.**

Una App es un entorno de ejecución virtual ligero. Su núcleo del sistema está escrito en **Zig**, mientras que la lógica mutable se ejecuta como **scripts de TypeScript**.

Esta separación mantiene la infraestructura crítica en un núcleo compacto y de alto rendimiento, al tiempo que conserva la flexibilidad de TypeScript para la lógica y la configuración de la aplicación.

Las Apps proporcionan las capacidades de infraestructura utilizadas por el resto del sistema:

* **Fujin** — tejido de comunicación para comandos, eventos, WebSockets y telemetría de máquinas.
* **Centimanus** — procesamiento DAG y ejecución de Flujos de trabajo.
* **Resonus** — puerta de enlace en tiempo real para voz, medios, transcripción y proveedores de IA.
* **Behemoth** — almacenamiento múltiple aislado para diferentes tipos de datos.
* **Ptah** — gestión del despliegue y de la topología de Kubernetes.
* **Cruller** — entorno de ejecución en el que se ejecutan los módulos de UI y TypeScript.

Las Apps no son otra capa de lógica de negocio. Proporcionan la **infraestructura y los entornos de ejecución** en los que opera la capa de TypeScript.

### Fujin

**Fujin es el tejido unificado para comandos, eventos y telemetría.**

Todos los componentes del sistema se comunican a través de Fujin en lugar de realizar llamadas directas entre sí. Un comando procedente de la UI, un evento de un Flujo de trabajo, una lectura de un sensor de máquina o una actualización del progreso de producción pasan por la misma capa de comunicación.

Los WebSockets envían cambios a la interfaz en tiempo real sin sondeo.

Como la comunicación pasa por una única capa, puede rastrearse, reproducirse y limitarse centralmente.

**Resultado:** los Servicios permanecen independientes, el tiempo real pasa a formar parte de la infraestructura común y los eventos del sistema se vuelven observables.

### Resonus

**Resonus es una interfaz unificada en tiempo real para voz, medios e IA.**

Combina llamadas telefónicas, flujos de audio, transcripción y adaptadores de proveedores de IA dentro de una única capa.

Una conversación puede pasar de una llamada telefónica a la transcripción y después al análisis de IA sin pasar entre sistemas separados. Los medios pueden asociarse directamente con pedidos, equipos y eventos.

Los adaptadores de proveedores aíslan el sistema de los proveedores individuales de voz e IA.

**Resultado:** la voz, los medios y la IA pasan a formar parte del entorno común de Flujos de trabajo, mientras que los proveedores pueden sustituirse sin reestructurar la lógica de la aplicación.

### Behemoth

**Behemoth es el sistema unificado de almacenamiento múltiple para los datos de Converged.**

A los distintos tipos de datos se les proporciona un almacenamiento adecuado: SQL para pedidos y clientes, archivos para modelos y documentos, vectores para búsquedas de IA, caché para el estado activo y otros tipos de almacenamiento especializado cuando sea necesario.

El aislamiento es estructural: los datos de distintos espacios de trabajo no se mezclan y pueden escalarse, respaldarse y trasladarse de forma independiente.

El mismo modelo funciona en despliegues Edge, de Servidor y de Clúster. En un dispositivo Edge pequeño, todos los dominios de almacenamiento pueden residir en un único nodo; en un Clúster, pueden distribuirse entre hardware de almacenamiento especializado.

**Resultado:** los datos quedan aislados por diseño, mientras que la infraestructura de almacenamiento puede crecer con la instalación sin cambiar la capa de aplicación.

### Ptah

**Ptah es el orquestador de despliegue de Converged sobre Kubernetes.**

Gestiona la ubicación de Apps, contenedores y datos según la topología de despliegue: Edge, Servidor o Clúster.

El núcleo de Ptah está escrito en Zig, mientras que las reglas de gestión se implementan como scripts de TypeScript. Esto permite modificar la lógica de ubicación, orden de lanzamiento, conmutación por error y distribución de datos sin reconstruir el núcleo.

El mismo mecanismo se utiliza para distintos tipos de instalación, desde un único nodo Edge hasta un clúster distribuido.

**Resultado:** todo el sistema se gestiona mediante una capa de despliegue unificada, mientras que la lógica de despliegue sigue siendo dinámica y modificable.

### Cruller

**Cruller es el entorno de ejecución para la UI y los módulos de TypeScript.**

Proporciona el entorno en el que se ejecuta la lógica TypeScript de Converged, incluidos la UI y los módulos de aplicación.

Cruller conecta la capa dinámica de TypeScript con las capacidades de infraestructura proporcionadas por las Apps, permitiendo que la capa de aplicación evolucione sin modificar el núcleo de bajo nivel.

### Kubernetes y topología

Todas las Apps y los componentes relacionados se despliegan mediante **Kubernetes**.

Converged utiliza el mismo modelo arquitectónico independientemente de la escala de instalación:

```text
Edge
  → nodo único

Servidor
  → servidor único con mayores recursos

Clúster
  → múltiples nodos y almacenamiento distribuido
```

La topología física cambia, pero el modelo de aplicación no. Los Servicios, Flujos de trabajo, Superficies y Proyecciones operan de la misma manera tanto si el sistema se ejecuta en un dispositivo Edge como si lo hace en un clúster completo.

### Modelo unificado

Las distintas partes de Converged se organizan en torno a responsabilidades diferentes:

**Superficie** — contexto de trabajo del usuario.
**Proyección** — una función específica y su representación visual.
**Repositorio** — acceso a los datos.
**Lambda** — una operación individual sin estado.
**Entorno de ejecución** — un entorno de ejecución especializado.
**Flujo de trabajo** — un proceso de negocio que combina Servicios.
**Apps** — entornos de ejecución de infraestructura con un núcleo en Zig y TypeScript en su interior.
**Fujin** — comunicación y eventos.
**Centimanus** — ejecución de Flujos de trabajo.
**Resonus** — voz, medios e IA en tiempo real.
**Behemoth** — almacenamiento.
**Ptah** — despliegue y gestión de Kubernetes.
**Cruller** — entorno de ejecución para la UI y TypeScript.

El principio central de Converged es **separar el contexto del usuario, la lógica de la aplicación y la infraestructura sin obligarlos a encajar en la misma estructura**.

Una Superficie puede combinar varios Servicios. Un Flujo de trabajo puede combinar varias operaciones. Y varios Flujos de trabajo y Servicios pueden utilizar las mismas Apps subyacentes.

El resultado es un sistema que permanece modular en el nivel de la lógica de negocio, compacto en el nivel de la infraestructura y unificado desde la perspectiva del usuario.
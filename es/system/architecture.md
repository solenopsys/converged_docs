# Arquitectura del sistema

Converged es una capa operativa modular para empresas de fabricación. Sus
interfaces de usuario, servicios de dominio, motor de flujos de trabajo,
almacenamiento, puerta de enlace multimedia y procesadores industriales forman
un solo sistema sin convertirse en una sola aplicación.

La arquitectura separa tres tipos de trabajo:

- los módulos de dominio son propietarios de los datos empresariales y las capacidades orientadas al usuario;
- los servicios nativos del entorno de ejecución transportan mensajes, ejecutan flujos de trabajo, almacenan datos y gestionan medios en tiempo real;
- el plano de control decide qué partes se ejecutan para cada plataforma y arrendatario.

## Un bus de mensajes

Los componentes del entorno de ejecución se comunican mediante Fujin. Cada proceso abre una conexión, registra un destino y envía mensajes a destinos lógicos. El emisor no necesita conocer la dirección ni la ubicación de despliegue del receptor.

```text
clientes de navegador y móviles
          |
          v
          bus de mensajes Fujin
       /     |      |      \
      ui     ms  Centimanus Resonus
              \      |      /
               \  Behemoth /
```

Esto elimina el grafo de llamadas HTTP y la malla de servicios de la capa de aplicación. El enrutamiento, la correlación de solicitudes y el contexto de arrendatario confiable viajan en el sobre de mensajes común. A continuación, el proceso receptor selecciona el servicio o controlador solicitado dentro de su propio límite.

## Entorno de ejecución principal

| Componente | Responsabilidad |
| --- | --- |
| Fujin | Conecta a los pares del entorno de ejecución y enruta los mensajes al propietario activo de un destino. |
| Behemoth | Proporciona almacenamiento SQL, clave-valor, columnar, vectorial, de grafos y de archivos aislado. |
| Centimanus | Ejecuta flujos de trabajo empresariales de varios pasos como grafos reproducibles. |
| Resonus | Gestiona medios en tiempo real, llamadas, transcripción y sesiones de IA. |
| Ptah | Concilia la plataforma, las soluciones y los arrendatarios deseados con los recursos de Kubernetes. |

Los componentes son deliberadamente limitados. Fujin no entiende los servicios empresariales. Behemoth no orquesta operaciones empresariales. Centimanus no es propietario de los datos de dominio. Resonus no decide la identidad del arrendatario. Ptah crea y configura cargas de trabajo, pero no participa en la mensajería del entorno de ejecución.

## Módulos y soluciones

Las capacidades empresariales se entregan como microservicios, superficies y flujos de trabajo. Una solución es una selección declarativa de esos módulos para un escenario operativo concreto, como la gestión de pedidos, la planificación de la producción o la supervisión de equipos.

Los microservicios son propietarios de sus datos y exponen contratos tipados. No se llaman entre sí para coordinar un proceso. Las secuencias entre dominios pertenecen a los flujos de trabajo, que Centimanus ejecuta un paso duradero cada vez. Esto mantiene pequeños los módulos de dominio y permite que una solución los combine sin crear un acoplamiento oculto.

## Aislamiento de datos

Cada microservicio tiene su propia raíz física de almacenamiento. Behemoth puede servir muchas raíces desde un mismo proceso, pero conserva sus límites de propiedad y se niega a crear datos fuera de los montajes configurados.

El mismo modelo se adapta a distintos perfiles de despliegue:

- una instalación periférica puede ejecutar una instancia de Behemoth para la plataforma;
- una instalación más grande puede dividir los ámbitos entre fragmentos de almacenamiento;
- una instalación en la nube puede ejecutar una instancia de almacenamiento aislada por arrendatario.

Cambiar la topología no cambia el código de la aplicación, porque los pares siguen dirigiéndose a destinos lógicos y a límites de almacenamiento.

## Plano de control

Ptah es el plano de control y no está conectado a Fujin. Observa los recursos declarados de Plataforma, Solución y Arrendatario, calcula las cargas de trabajo deseadas y las concilia con Kubernetes.

```text
Plataforma + Soluciones + Arrendatarios
              |
              v
             Ptah
              |
              v
Despliegues, servicios, volúmenes, configuración y rutas
```

Esta separación permite que el entorno de ejecución se concentre en el tráfico empresarial mientras el modelo de despliegue gestiona la ubicación, la topología de almacenamiento, las rutas de los arrendatarios y el ciclo de vida. Por tanto, las mismas imágenes de aplicación pueden ejecutarse en un clúster periférico compacto o en un entorno de nube multiarrendatario.

## Contexto confiable

El ámbito del arrendatario se establece en el extremo de la plataforma y se transporta en el sobre de mensajes. Los servicios del entorno de ejecución consumen ese contexto confiable en lugar de derivar el arrendatario de las cargas útiles de la aplicación. La ubicación del almacenamiento, las llamadas a servicios y las sesiones multimedia conservan el mismo límite de ámbito.

En conjunto, la mensajería lógica, el almacenamiento aislado, los flujos de trabajo reproducibles y un plano de control separado permiten que Converged siga siendo modular sin trasladar la complejidad de los sistemas distribuidos a cada módulo empresarial.

## Tecnologías

Converged está construido sobre una base compacta de sistemas diseñada para ofrecer un alto rendimiento y un uso eficiente de los recursos en entornos Kubernetes de cualquier escala, desde un solo microordenador hasta un clúster distribuido.

En el núcleo de la infraestructura se encuentra **Zig**, un lenguaje moderno, extremadamente rápido y sencillo para la programación de sistemas. Zig se utiliza para los elementos de infraestructura en los que son importantes el rendimiento, la eficiencia de los recursos, el acceso al hardware y el control de bajo nivel.

**Cruller** proporciona el entorno de ejecución para TypeScript y JavaScript. Es un runtime especializado derivado de Bun y adaptado a la arquitectura y los requisitos de Converged.

**Behemoth** proporciona una capa de datos unificada compatible con distintos modelos de almacenamiento, incluidos SQL, datos clave-valor, archivos, vectores y otras estructuras de datos especializadas. El almacenamiento puede distribuirse y escalarse según los requisitos de cada implementación.

**Fujin** proporciona la capa de comunicación, conectando Services, interfaces, eventos y equipos mediante una infraestructura unificada de comunicación en tiempo real. **Centimanus** ejecuta Workflows y gestiona sus dependencias, ejecución paralela, eventos, reintentos y operaciones de larga duración.

Converged siempre se ejecuta en **Kubernetes**. El entorno base es **k3s**, una distribución ligera de Kubernetes que hace práctico el mismo modelo de implementación incluso en pequeños dispositivos edge, como Raspberry Pi. En una sola máquina, Converged se ejecuta como un clúster compacto de un solo nodo; cuando es necesario, el mismo clúster puede distribuirse entre varias máquinas.

Esto proporciona una base tecnológica coherente en toda la infraestructura, desde un pequeño dispositivo edge hasta un clúster distribuido en la nube.

## Despliegue

Converged admite varios escenarios de despliegue, desde dispositivos edge compactos y servidores locales hasta infraestructura en la nube que presta servicio a muchas empresas independientes. La plataforma base se ejecuta en **k3s**, una distribución ligera de Kubernetes adecuada para microordenadores, infraestructura local y clústeres en la nube.

Hay tres perfiles principales de despliegue:

* **Mono** — la UI, los Servicios, el almacenamiento y la caché se ejecutan en una configuración compacta en una sola máquina. Es especialmente adecuado para **microordenadores como Raspberry Pi y Orange Pi**, dispositivos edge, pequeños servidores locales, desarrollo, prototipos y demostraciones.
* **Multi** — el sistema se distribuye entre varias máquinas en un clúster de Kubernetes. La UI, los grupos de Servicios, el almacenamiento y la caché pueden desplegarse y escalarse de forma independiente. Este perfil es adecuado para entornos de producción en los que se requieren mayor capacidad, tolerancia a fallos y un control más preciso de los recursos.
* **Cloud** — varias empresas operan dentro del **mismo clúster de Kubernetes** mediante una arquitectura multiinquilino. Cada **inquilino** tiene un entorno aislado con sus propios datos, configuración y recursos, mientras que la infraestructura subyacente del clúster se comparte. Esto permite atender eficientemente a muchas empresas sin requerir un clúster separado para cada cliente.

Los tres perfiles utilizan la misma base de código. Solo cambian la topología y la configuración del despliegue. Por tanto, un sistema puede comenzar como una instalación Mono compacta en un microordenador, pasar a un clúster Multi a medida que crecen los requisitos o ejecutarse como un servicio Cloud compartido por muchas empresas independientes.

En un despliegue **autogestionado**, la empresa controla la instalación, la red, las copias de seguridad, las actualizaciones y la ubicación física de sus datos. Esto es adecuado para organizaciones que necesitan un control total sobre su infraestructura.

En **Cloud**, la infraestructura se opera de forma centralizada. Varias empresas comparten el mismo clúster, pero permanecen aisladas en el nivel de inquilino, incluidos sus datos, configuración y recursos asignados.

También es posible un despliegue **híbrido**: los datos sensibles y los equipos pueden permanecer localmente, mientras que la nube se utiliza para actualizaciones, acceso externo, equipos distribuidos o determinadas capacidades de IA.

El principio clave es que **Converged no limita la plataforma a un único modelo de despliegue**. El mismo sistema puede ejecutarse en un microordenador pequeño, en un clúster compuesto por varias máquinas o como un servicio Cloud multiinquilino.
## Despliegue

Converged está preparado para varios escenarios de instalación: desde un pequeño taller hasta un despliegue de producción en la infraestructura de una empresa. La plataforma base se despliega sobre **k3s**, una distribución ligera de Kubernetes adecuada para dispositivos edge, servidores locales y entornos cloud.

Hay dos perfiles principales:

- **Mono** — UI, Runtime, microservicios, storage y cache se empaquetan de forma compacta. Es el modo para desarrollo, prototipos, demostraciones e instalaciones pequeñas donde importa más la simplicidad de arranque.
- **Multi** — UI, grupos de Runtime, grupos de microservicios por dominio, storage y cache se separan. Es el perfil estándar de producción cuando se necesitan aislamiento, escalado y control más preciso de la carga.

Ambos perfiles usan el mismo código. Solo cambian la topología de contenedores y la configuración. Una empresa puede empezar con una instalación compacta y después mover el mismo sistema a una infraestructura más seria sin reescribir el producto.

En escenarios self-hosted, el cliente controla instalación, red, backups, actualizaciones y ubicación física de los datos. Esto encaja con empresas que tienen requisitos internos de seguridad o quieren mantener la producción completamente de su lado. La entrega cloud elimina el trabajo operativo: la plataforma se despliega y actualiza por el equipo del servicio, mientras el cliente recibe un entorno listo.

También es posible un enfoque híbrido: los datos sensibles y el equipo permanecen localmente, mientras la nube se usa para actualizaciones, acceso externo, coordinación de equipos distribuidos o funciones de IA concretas. El principio importante es no atar al cliente a un único modelo de entrega.

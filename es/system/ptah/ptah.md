# Plano de control de Ptah

Ptah convierte una descripción de plataforma Converged en recursos de Kubernetes en ejecución.
Es el plano de control del sistema: decide qué debe existir para una plataforma,
qué soluciones están activas y cómo se colocan las cargas de trabajo y el almacenamiento
de los tenants.

## Modelo de plataforma deseado

El modelo de despliegue tiene tres capas:

| Recurso | Significado |
| --- | --- |
| Plataforma | Entorno de ejecución compartido, enrutamiento, perfil de almacenamiento, aplicaciones y mapa de módulos. |
| Solución | Conjunto de módulos de negocio, flujos de trabajo y procesadores añadidos a una plataforma. |
| Tenant | Sitio aislado con su propio ámbito, rutas y, cuando es necesario, fragmento de almacenamiento. |

Ptah observa estos recursos y produce el conjunto completo deseado de
despliegues, servicios, volúmenes, configuración y rutas. Kubernetes entonces
hace converger el clúster con esa descripción.

```text
Plataforma + Solución + Tenant
              |
              v
             Ptah
              |
              v
Cargas de trabajo, almacenamiento y rutas de Kubernetes
```

## Política y mecanismo

Ptah separa los mecanismos del clúster de la política del producto. El controlador nativo
observa Kubernetes, aplica recursos, registra el estado y elimina objetos obsoletos. Una capa de política pura convierte los datos observados de la plataforma en un resultado
​​deseado sin realizar llamadas de red ni modificar el clúster por sí misma.

Por lo tanto, la misma política puede evaluarse antes del despliegue. Esto hace
que las decisiones de colocación y ciclo de vida sean inspeccionables sin
reproducirlas en un segundo generador de configuración.

## Perfiles de despliegue

Los perfiles cambian la colocación del almacenamiento sin cambiar las imágenes de las aplicaciones:

- `mono` ejecuta una instancia de almacenamiento para una plataforma compacta;
- `multi` divide los ámbitos entre fragmentos de almacenamiento;
- `cloud` proporciona a cada tenant una instancia de almacenamiento aislada y un límite de rutas.

La regla de propiedad de los volúmenes sigue siendo la misma en todos los perfiles: cada microservicio
tiene su propio volumen de almacenamiento. Ptah decide qué instancia de Behemoth monta esos
volúmenes y publica la asignación de ámbito a almacenamiento que utilizan las cargas de trabajo sin estado.

## Módulos y despliegue gradual

Las soluciones nombran módulos en lugar de integrar sus bytes. Ptah distribuye un
mapa de módulos direccionado por contenido y sirve contenido de módulos inmutable mediante una
caché compartida. Los consumidores reciben el resumen exacto que deben cargar.

Cuando cambia el resumen seleccionado, la descripción de la carga de trabajo cambia con él y
Kubernetes realiza el despliegue gradual. Por lo tanto, un pod en ejecución registra el contenido
preciso del módulo con el que se inició, y revertir significa seleccionar de nuevo el resumen anterior.

## Reconciliación segura

Ptah aplica un conjunto completo deseado y depura los recursos que ya no le pertenecen.
Los recursos que contienen datos se conservan a menos que se solicite explícitamente su eliminación.
Una entrada incompleta o un fallo de política suprime la depuración, evitando que un problema temporal
de dependencias se interprete como una solicitud para eliminar la plataforma.

## Lugar en el sistema

Ptah no es un par en el bus de mensajes de Fujin ni procesa tráfico empresarial. Crea y configura los pares, el almacenamiento y las rutas que componen el entorno de ejecución. Una vez que están en ejecución, Fujin, Behemoth, Centimanus y Resonus realizan su trabajo de forma independiente del plano de control.

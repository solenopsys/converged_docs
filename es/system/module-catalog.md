# Catálogo de módulos

Este índice se genera a partir del registro de módulos de Converged. Cada entrada enlaza a la documentación propia de ese módulo; las dependencias se toman de su manifiesto de paquete del espacio de trabajo, y la pertenencia a soluciones proviene de `modules/solutions`.

## Acceso y seguridad

### [lm-secrets](/en/docs/modules/lm-secrets)

Proporciona el contrato de servicio para almacenar, recuperar y eliminar valores de secretos con nombre.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [rp-access](/en/docs/modules/rp-access)

rp-access es un repositorio en el dominio de seguridad. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `security`

### [rp-auth](/en/docs/modules/rp-auth)

rp-auth es un repositorio en el dominio de seguridad. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `security`

### [rp-environment](/en/docs/modules/rp-environment)

Almacena y recupera la configuración de entorno asociada a los usuarios de la plataforma.

- Dependencias directas: ninguna
- Soluciones: `security`

### [rp-identity](/en/docs/modules/rp-identity)

rp-identity es un repositorio en el dominio de seguridad. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `security`

### [rp-oauth](/en/docs/modules/rp-oauth)

rp-oauth es un repositorio en el dominio de seguridad. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [sf-auth](/en/docs/modules/sf-auth)

sf-auth es una superficie en el dominio de seguridad. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `security`

### [sf-secrets](/en/docs/modules/sf-secrets)

Proporciona la interfaz de administración para crear, ver, actualizar y eliminar registros de secretos con nombre.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [sf-team](/en/docs/modules/sf-team)

sf-team es una superficie en el dominio de seguridad. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `production`

## IA y agentes

### [rp-assistant](/en/docs/modules/rp-assistant)

rp-assistant es un repositorio en el dominio de IA. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `ai`

### [rp-contexts](/en/docs/modules/rp-contexts)

Proporciona el almacenamiento y la recuperación de contextos de IA con nombre, incluidas sus variantes de idioma.

- Dependencias directas: ninguna
- Soluciones: `ai`

### [sf-assistants](/en/docs/modules/sf-assistants)

sf-assistants es una superficie en el dominio de IA. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: `sf-requests`
- Soluciones: `ai`

### [sf-contexts](/en/docs/modules/sf-contexts)

Proporciona el espacio de trabajo de IA para enumerar, editar y guardar contextos con nombre en varios idiomas.

- Dependencias directas: ninguna
- Soluciones: `ai`

## Analítica y telemetría

### [rp-counters](/en/docs/modules/rp-counters)

Almacena configuraciones externas de contadores de analítica por inquilino (ids de seguimiento, fragmentos head) para inyección SSR.

- Dependencias directas: ninguna
- Soluciones: `analitycs`

### [rp-dashboard](/en/docs/modules/rp-dashboard)

Almacena fijaciones de indicadores del panel personal: qué widgets fijó un usuario, su orden y metadatos de visualización.

- Dependencias directas: ninguna
- Soluciones: `analitycs`

### [rp-logs](/en/docs/modules/rp-logs)

rp-logs es un repositorio en el dominio de analítica. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `analitycs`

### [rp-telemetry](/en/docs/modules/rp-telemetry)

rp-telemetry es un repositorio en el dominio de analítica. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `analitycs`

### [rp-usage](/en/docs/modules/rp-usage)

rp-usage es un repositorio en el dominio de analítica. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `analitycs`

### [sf-dasboards](/en/docs/modules/sf-dasboards)

sf-dasboards es una superficie en el dominio de analítica. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `analitycs`

### [sf-logs](/en/docs/modules/sf-logs)

sf-logs es una superficie en el dominio de analítica. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `analitycs`

### [sf-telemetry](/en/docs/modules/sf-telemetry)

sf-telemetry es una superficie en el dominio de analítica. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `analitycs`

### [sf-usage](/en/docs/modules/sf-usage)

sf-usage es una superficie en el dominio de analítica. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `analitycs`

## Automatización y orquestación

### [lm-kubernetes](/en/docs/modules/lm-kubernetes)

Integra la automatización de la plataforma con recursos de Kubernetes mediante un cliente dedicado y un contrato de servicio.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [rp-dag](/en/docs/modules/rp-dag)

rp-dag es un repositorio en el dominio de automatización. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `automation`, `requests`

### [rp-sheduller](/en/docs/modules/rp-sheduller)

rp-sheduller es un repositorio en el dominio de automatización. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `automation`

### [rp-webhooks](/en/docs/modules/rp-webhooks)

rp-webhooks es un repositorio en el dominio de automatización. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `automation`

### [sf-automation](/en/docs/modules/sf-automation)

sf-automation es una superficie en el dominio de automatización. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `automation`

## Dominio empresarial

### [rp-billing](/en/docs/modules/rp-billing)

rp-billing es un repositorio en el dominio empresarial. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `billing`

### [rp-equipment](/en/docs/modules/rp-equipment)

rp-equipment es un repositorio en el dominio empresarial. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `production`

### [rp-events](/en/docs/modules/rp-events)

Proporciona la creación, el almacenamiento y la recuperación de eventos empresariales.

- Dependencias directas: ninguna
- Soluciones: `production`

### [rp-finance](/en/docs/modules/rp-finance)

Proporciona operaciones financieras para transacciones, resúmenes de períodos, flujo de caja, cuentas por cobrar y cuentas por pagar.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [rp-invoices](/en/docs/modules/rp-invoices)

rp-invoices es un repositorio en el dominio empresarial. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `billing`

### [rp-metering](/en/docs/modules/rp-metering)

rp-metering es un repositorio en el dominio empresarial. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `billing`

### [rp-orders](/en/docs/modules/rp-orders)

Proporciona el contrato de servicio para crear, actualizar, enumerar y realizar el seguimiento de pedidos empresariales.

- Dependencias directas: ninguna
- Soluciones: `production`

### [rp-requests](/en/docs/modules/rp-requests)

rp-requests es un repositorio en el dominio empresarial. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `requests`

### [rp-reviews](/en/docs/modules/rp-reviews)

rp-reviews es un repositorio en el dominio empresarial. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `production`

### [rp-sales](/en/docs/modules/rp-sales)

rp-sales es un repositorio en el dominio empresarial. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [rp-staff](/en/docs/modules/rp-staff)

rp-staff es un repositorio en el dominio empresarial. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `production`

### [sf-equipment](/en/docs/modules/sf-equipment)

sf-equipment es una superficie en el dominio empresarial. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `production`

### [sf-orders](/en/docs/modules/sf-orders)

Proporciona la interfaz de ventas para listas de pedidos y solicitudes, detalles de pedidos, filtrado por estado y paneles operativos.

- Dependencias directas: ninguna
- Soluciones: `production`

### [sf-requests](/en/docs/modules/sf-requests)

sf-requests es una superficie en el dominio empresarial. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `requests`

### [sf-reviews](/en/docs/modules/sf-reviews)

sf-reviews es una superficie en el dominio empresarial. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `production`

## Comunicaciones

### [rp-calls](/en/docs/modules/rp-calls)

rp-calls es un repositorio en el dominio de comunicaciones. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `ai`

### [rp-chats](/en/docs/modules/rp-chats)

rp-chats es un repositorio en el dominio de comunicaciones. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `communications`

### [rp-community](/en/docs/modules/rp-community)

rp-community es un repositorio en el dominio de comunicaciones. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `communications`

### [rp-notify](/en/docs/modules/rp-notify)

rp-notify es un repositorio en el dominio de comunicaciones. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `security`

### [rp-resonus](/en/docs/modules/rp-resonus)

Proporciona la configuración de comunicación para números de teléfono gestionados y ajustes de puerta de enlace LLM.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [rp-support](/en/docs/modules/rp-support)

rp-support es un repositorio en el dominio de comunicaciones. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `communications`

### [rp-threads](/en/docs/modules/rp-threads)

rp-threads es un repositorio en el dominio de comunicaciones. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `ai`, `communications`

### [sf-calls](/en/docs/modules/sf-calls)

sf-calls es una superficie en el dominio de comunicaciones. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `ai`

### [sf-chats](/en/docs/modules/sf-chats)

sf-chats es una superficie en el dominio de comunicaciones. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `communications`

### [sf-community](/en/docs/modules/sf-community)

sf-community es una superficie en el dominio de comunicaciones. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `communications`

### [sf-support](/en/docs/modules/sf-support)

sf-support es una superficie en el dominio de comunicaciones. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `communications`

### [sf-threads](/en/docs/modules/sf-threads)

sf-threads es una superficie en el dominio de comunicaciones. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `ai`, `communications`

## Contenido y documentos

### [rp-classifier](/en/docs/modules/rp-classifier)

rp-classifier es un repositorio en el dominio de contenido. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [rp-galery](/en/docs/modules/rp-galery)

rp-galery es un repositorio en el dominio de contenido. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `content`

### [rp-markdown](/en/docs/modules/rp-markdown)

rp-markdown es un repositorio en el dominio de contenido. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `content`

### [rp-scripts](/en/docs/modules/rp-scripts)

Proporciona operaciones de almacenamiento para archivos de script, incluidas la lectura, el guardado, el cálculo de hash y la eliminación.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [rp-static](/en/docs/modules/rp-static)

Proporciona el contrato de servicio para contenido estático y metadatos de caché SSR.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [rp-struct](/en/docs/modules/rp-struct)

rp-struct es un repositorio en el dominio de contenido. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `content`

### [sf-classifier](/en/docs/modules/sf-classifier)

Proporciona la interfaz del clasificador para navegar por entidades, asignaciones y estructuras de árbol.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [sf-docs](/en/docs/modules/sf-docs)

sf-docs es una superficie en el dominio de contenido. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [sf-galery](/en/docs/modules/sf-galery)

sf-galery es una superficie en el dominio de contenido. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [sf-landing](/en/docs/modules/sf-landing)

sf-landing es una superficie en el dominio de contenido. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [sf-markdown](/en/docs/modules/sf-markdown)

sf-markdown es una superficie en el dominio de contenido. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [sf-static](/en/docs/modules/sf-static)

Proporciona la interfaz de operaciones para inspeccionar y borrar entradas estáticas de caché SSR.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [sf-struct](/en/docs/modules/sf-struct)

sf-struct es una superficie en el dominio de contenido. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

## Archivos y almacenamiento

### [lm-compressors](/en/docs/modules/lm-compressors)

lm-compressors es una lambda en el dominio de datos. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `requests`

### [rp-dumps](/en/docs/modules/rp-dumps)

rp-dumps es un repositorio en el dominio de datos. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [rp-files](/en/docs/modules/rp-files)

rp-files es un repositorio en el dominio de datos. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `communications`, `requests`

### [rp-store](/en/docs/modules/rp-store)

rp-store es un repositorio en el dominio de datos. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `requests`

### [sf-dumps](/en/docs/modules/sf-dumps)

sf-dumps es una superficie en el dominio de datos. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [sf-files](/en/docs/modules/sf-files)

sf-files es una superficie en el dominio de datos. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `requests`

## Proveedores de entrega de mensajes

### [lm-lemonsqueezy](/en/docs/modules/lm-lemonsqueezy)

lm-lemonsqueezy es una lambda en el dominio de proveedores. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `billing`

### [lm-push](/en/docs/modules/lm-push)

lm-push es una lambda en el dominio de proveedores. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [lm-ses](/en/docs/modules/lm-ses)

lm-ses es una lambda en el dominio de proveedores. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `security`

### [lm-sms](/en/docs/modules/lm-sms)

lm-sms es una lambda en el dominio de proveedores. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [lm-smtp](/en/docs/modules/lm-smtp)

lm-smtp es una lambda en el dominio de proveedores. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

## Conversión de modelos

### [lm-modelconvertor](/en/docs/modules/lm-modelconvertor)

lm-modelconvertor es una lambda en el dominio de convertidores. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `requests`

## Flujos de trabajo

### [wf-dialogue-summary](/en/docs/modules/wf-dialogue-summary)

Resume diálogos de chat y llamadas no procesados con un LLM y luego almacena títulos, descripciones y clasificación de ruido.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [wf-equipment-incident](/en/docs/modules/wf-equipment-incident)

wf-equipment-incident es un flujo de trabajo en el dominio de plataforma. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `production`

### [wf-file-analyze](/en/docs/modules/wf-file-analyze)

Analiza un archivo almacenado no comprimido, generando vistas previas de modelos y estimaciones CNC o de impresión 3D cuando es compatible.

- Dependencias directas: ninguna
- Soluciones: `requests`

### [wf-file-unpack](/en/docs/modules/wf-file-unpack)

Expande un archivo comprimido subido en una colección de archivos almacenados para su análisis posterior.

- Dependencias directas: ninguna
- Soluciones: `requests`

### [wf-files-analyze](/en/docs/modules/wf-files-analyze)

wf-files-analyze es un flujo de trabajo en el dominio de plataforma. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `requests`

### [wf-files-process](/en/docs/modules/wf-files-process)

Procesa archivos subidos por lotes: expande archivos comprimidos, identifica archivos de modelos y crea a partir de ellos una solicitud de fabricación.

- Dependencias directas: ninguna
- Soluciones: `requests`

### [wf-order-review-followup](/en/docs/modules/wf-order-review-followup)

wf-order-review-followup es un flujo de trabajo en el dominio de plataforma. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `production`

### [wf-order-review-request](/en/docs/modules/wf-order-review-request)

wf-order-review-request es un flujo de trabajo en el dominio de plataforma. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `production`

### [wf-payment-settle](/en/docs/modules/wf-payment-settle)

wf-payment-settle es un flujo de trabajo en el dominio de plataforma. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `billing`

### [wf-request-analyze](/en/docs/modules/wf-request-analyze)

wf-request-analyze es un flujo de trabajo en el dominio de plataforma. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `requests`

### [wf-request-to-order](/en/docs/modules/wf-request-to-order)

wf-request-to-order es un flujo de trabajo en el dominio de plataforma. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `production`

### [wf-sales-import](/en/docs/modules/wf-sales-import)

wf-sales-import es un flujo de trabajo en el dominio de plataforma. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [wf-sales-review-outreach](/en/docs/modules/wf-sales-review-outreach)

wf-sales-review-outreach es un flujo de trabajo en el dominio de plataforma. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: ninguna

### [wf-team-invite](/en/docs/modules/wf-team-invite)

wf-team-invite es un flujo de trabajo en el dominio de plataforma. Su propósito detallado se mantiene con el código fuente del módulo.

- Dependencias directas: ninguna
- Soluciones: `production`

## Dependencias de soluciones

- `ai`: `security`
- `analitycs`: `security`
- `automation`: `security`
- `billing`: `security`
- `communications`: `security`
- `content`: `security`
- `production`: `security`, `analitycs`, `requests`
- `requests`: sin dependencias de solución
- `security`: sin dependencias de solución

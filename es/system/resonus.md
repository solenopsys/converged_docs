# Resonus: medios y puerta de enlace de IA

Resonus conecta las conversaciones en tiempo real con la plataforma Converged. Gestiona
audio del navegador, llamadas telefónicas, transcripción y sesiones de IA, al tiempo que mantiene
las acciones empresariales resultantes dentro del mismo modelo de permisos y flujos de trabajo que utiliza
el resto del sistema.

## Un límite de sesión

El transporte de medios y la interacción con la IA comparten el estado de la llamada, la temporización y el contexto.
Mantenerlos en un único proceso nativo evita pasar una conversación activa por
varias puertas de enlace independientes antes de que pueda llegar a un modelo o a un operador humano.

```text
navegador o teléfono
       |
       v
    Resonus ---- sesión de IA
       |
       +-------- transferencia a una persona
       |
       +-------- servicios y flujos de trabajo de la plataforma
```

Una política de implementación elige cómo se gestiona una llamada entrante: mediante una sesión de IA,
mediante un destino humano, mediante una ruta de transferencia o mediante el rechazo. El transporte y la ejecución de medios
permanecen nativos, mientras que la política sigue siendo una pequeña capa de decisión reemplazable.

## Integración con la plataforma

Resonus utiliza los servicios de la plataforma para el contexto de las llamadas y los registros empresariales. Los fragmentos de audio
pueden pasar por la caché del entorno de ejecución antes de que el servicio propietario los almacene. Las llamadas pueden activar
flujos de trabajo u operaciones de servicio sin otorgar a la puerta de enlace la propiedad de esos dominios.

La transcripción convierte la voz en el mismo tipo de entrada estructurada disponible para
otras interfaces. Esto permite que un operador o cliente interactúe de forma natural, mientras que la acción resultante sigue
los contratos de servicio y las rutas de auditoría normales.

## Contexto de inquilino de confianza

Para el tráfico que llega a través de Fujin, Resonus acepta el ámbito del inquilino del
sobre de mensajes de confianza. No infiere un ámbito a partir de un número de teléfono, una etiqueta de usuario o una carga útil del modelo. El ámbito
se conserva durante la sesión y se reenvía a los servicios de la plataforma utilizados por esa sesión.

Las rutas de entrada que no puedan establecer un ámbito de confianza deben aislarse hasta que la
implementación las vincule a uno. Esto evita que un identificador de medios conveniente
se convierta silenciosamente en una decisión de autorización.

## Límite del proveedor

Los proveedores de IA se sitúan detrás de un límite común de sesión y política. La elección del proveedor,
la selección del modelo, la voz y el comportamiento de transferencia son decisiones de implementación,
en lugar de supuestos incorporados en todos los módulos empresariales. La puerta de enlace puede evolucionar
sus adaptadores de proveedores sin cambiar la forma en que el resto de Converged gestiona una
llamada asistida por IA.

## Lugar en el sistema

Resonus es responsable de los medios en tiempo real y de la ejecución de sesiones de IA. No es responsable de los registros
de clientes, el historial de llamadas, las definiciones de flujos de trabajo, la selección de inquilinos ni el
encaminamiento general de mensajes. Esas responsabilidades permanecen en los servicios de dominio,
Centimanus, el extremo de confianza y Fujin.

# Bus de mensajes Fujin

Fujin es el centro de comunicación del runtime Converged. Proporciona a los navegadores,
a los servicios de dominio, al almacenamiento, a los flujos de trabajo, a los servicios multimedia
y a los procesadores una forma compartida de intercambiar mensajes.

## Por qué existe

Una plataforma modular necesita que los componentes se muevan de forma independiente. Los enlaces HTTP
directos obligarían a cada servicio a conocer las direcciones, las réplicas y la topología de despliegue.
Fujin reemplaza esos enlaces por destinos lógicos: un emisor indica qué par del runtime
debería recibir un mensaje, y Fujin lo reenvía a la conexión activa
que actualmente posee ese destino.

```text
emisor -> destino lógico -> Fujin -> conexión activa -> servicio local
```

El emisor no sabe dónde se ejecuta el receptor. Un proceso puede reiniciarse o trasladarse
a otro nodo y recuperar el mismo destino sin cambiar a sus clientes.

## Modelo de enrutamiento

Fujin toma una decisión de enrutamiento: asigna un destino a una conexión. El destino
selecciona un proceso, como el runtime de la interfaz de usuario, los servicios de dominio o Centimanus. El
nombre del servicio dentro del mensaje se interpreta únicamente después de que el proceso receptor
lo recibe.

Mantener separadas esas decisiones es importante. Fujin sigue siendo un pequeño
agente de mensajes en lugar de convertirse en un registro de cada servicio empresarial, unidad de almacenamiento
o flujo de trabajo.

## Tres flujos

Fujin transporta tres tipos de tráfico que comparten un transporte, pero nada más.
La mensajería de servicios mueve solicitudes entre pares. La ingesta de registros recibe lo que
emiten los recopiladores del despliegue, lo agrupa y entrega bloques completos a los
repositorios de análisis, de modo que el almacenamiento recibe lotes en lugar de un flujo de filas
individuales. Las notificaciones de usuario son mensajes empresariales dirigidos a una persona: llegó un pedido,
terminó un trabajo, hay una carta esperando.

El tercero es el que necesita un nombre propio. `pushrouter` es un servicio que Fujin aloja en lugar de enrutar hacia él,
porque la entrega es una propiedad de las sesiones activas que Fujin ya posee: ningún otro proceso
sabe cuáles de los navegadores de una persona están conectados actualmente. Responde con cuántas sesiones
recibieron un mensaje, lo que permite a un llamador decidir si también se necesita un canal duradero,
y mantiene una ventana de reproducción acotada para que un navegador que se vuelve a conectar vea
lo que se perdió. Todo lo que deba sobrevivir a un reinicio pertenece en un repositorio,
no aquí.

Las notificaciones transportan claves de traducción en lugar de frases. El servicio que
publica una no conoce el idioma del lector, por lo que una cadena renderizada solo podría
ser correcta para uno de ellos.

## Tráfico del navegador y del clúster

Los pares nativos se conectan mediante el transporte del clúster. Los navegadores y los clientes móviles
entran a través de WebSocket y participan en el mismo modelo de mensajería. Esto proporciona
a las interfaces interactivas eventos en tiempo real sin introducir un segundo sistema de
enrutamiento de aplicaciones.

Las cargas útiles grandes permanecen fuera del canal de control del navegador. Los clientes reciben un
evento de disponibilidad y recuperan los datos mediante la ruta de contenido adecuada,
lo que mantiene la señalización en tiempo real receptiva.

## Contexto y confianza

La envoltura común de mensajes transporta datos de correlación, plazos, errores y
el ámbito de inquilino de confianza. Fujin transporta ese contexto sin derivarlo
de una carga útil empresarial ni cambiar su significado. Los servicios receptores pueden aplicar
reglas de autorización y almacenamiento contra el mismo contexto establecido en el
borde.

## Límite de responsabilidad

Fujin es responsable de la conectividad y del enrutamiento de destinos. No ejecuta lógica empresarial,
selecciona un controlador dentro de otro proceso, almacena datos de dominio ni decide la ubicación del despliegue.
Esas responsabilidades permanecen en el par del runtime que recibe el
mensaje y en Ptah como plano de control.

# Entorno de ejecución de flujos de trabajo de Centimanus

Centimanus ejecuta los procesos de varios pasos que conectan módulos de
Converged que, de otro modo, serían independientes. El enrutamiento de pedidos,
las notificaciones, las aprobaciones, el trabajo asistido por IA y las
secuencias de producción pueden evolucionar como flujos de trabajo sin trasladar
la orquestación a los servicios de dominio.

## Ejecución reproducible

Un flujo de trabajo es un programa cuyas operaciones relevantes se dividen en
nodos con nombre. Centimanus ejecuta un nodo sin terminar, registra su resultado
y después vuelve a evaluar el flujo de trabajo. Los nodos completados devuelven
sus resultados almacenados en lugar de repetir sus efectos secundarios.

```text
primera pasada:   buscar pedido -> almacenar resultado
segunda pasada:   reproducir pedido -> reservar máquina -> almacenar resultado
tercera pasada:   reproducir ambos -> notificar al operador -> completar
```

Las ramas y los bucles pueden depender de resultados anteriores, por lo que el
grafo surge del propio proceso en lugar de un diagrama estático independiente.
Los resultados registrados de los nodos hacen explícito el progreso y permiten
que la ejecución continúe desde el primer paso sin terminar.

## Por qué los flujos de trabajo están separados

Los microservicios de dominio de Converged son propietarios de los datos y de
pequeñas capacidades empresariales. No se llaman entre sí para implementar un
proceso de extremo a extremo. Esto evita cadenas ocultas en las que un cambio o
un fallo en un servicio afecta inesperadamente a muchos otros.

Centimanus es el lugar donde la coordinación entre dominios es visible. Un flujo
de trabajo puede llamar a servicios, solicitar trabajo de IA y elegir el
siguiente paso, mientras cada servicio sigue centrado en su propio límite.

## Entrega de flujos de trabajo

Las soluciones determinan qué flujos de trabajo están activos. Ptah publica esa
selección, el servicio DAG expone los descriptores seleccionados y Centimanus
carga el contenido correspondiente a través del proxy direccionado por contenido
de Ptah. Un flujo de trabajo que no forme parte de la solución activa no está
disponible para su ejecución.

Esto separa cuatro responsabilidades: selección del producto, entrega de
contenido, ejecución y observabilidad. Cada una puede cambiar sin convertir el
entorno de ejecución de flujos de trabajo en un registro de módulos o un
controlador de despliegues.

## Límite de fiabilidad

Centimanus registra los resultados de los nodos completados, pero las
operaciones externas aún deben respetar sus propias reglas de idempotencia. La
telemetría del flujo de trabajo se utiliza para obtener visibilidad; no decide
el estado de ejecución. Los datos empresariales permanecen en los servicios que
son sus propietarios, en lugar de convertirse en estado del motor de flujos de
trabajo.

## Lugar en el sistema

Centimanus recibe trabajo y llama a los servicios a través de Fujin. Utiliza el
almacenamiento de la plataforma para el progreso de los flujos de trabajo e
informa de eventos del ciclo de vida para la monitorización. No es propietario
de registros de dominio, no selecciona soluciones activas ni enruta mensajes
entre otros pares.

# Entorno de ejecución del contrato NRPC

NRPC es la capa de llamadas remotas tipadas de Converged. Convierte un contrato de
servicio de TypeScript en clientes compatibles y metadatos del servicio, de modo que un
navegador, microservicio, flujo de trabajo o entorno de ejecución nativo pueda llamar a
la misma capacidad sin mantener definiciones de API independientes basadas en cadenas.

## Por qué existe

La plataforma está compuesta por módulos desplegados de forma independiente. Llamar a un módulo
directamente mediante una dirección haría que sus clientes dependieran de dónde se ejecuta y
del transporte que utiliza. NRPC separa esas preocupaciones: un contrato nombra el
servicio y sus métodos, mientras que el entorno de ejecución entrega una llamada al proceso
que actualmente posee el destino solicitado.

Esto mantiene en un solo lugar el acuerdo entre los clientes y las implementaciones. Los
parámetros de un método, el tipo de retorno, el comportamiento de transmisión y el nivel de
acceso son conocidos por la generación de código y están disponibles para todos los clientes compatibles.

## Del contrato a la llamada

Los contratos son interfaces de TypeScript ubicadas en `modules/types/<domain>`. Ejecutar
`bun run gen` en `core/tools/nrpc` analiza esas interfaces y crea un paquete
`modules/generated/g-<service>`. El paquete contiene los metadatos del contrato,
una interfaz de servidor y fábricas de clientes con seguridad de tipos para cada entorno de ejecución.

```text
Interfaz de TypeScript
        |
        v
Generador NRPC -> paquete g-<service>
        |                    |
        |                    +-> cliente de navegador
        |                    +-> cliente de clúster
        |                    +-> cliente de RT de flujo de trabajo
        v
implementación del servicio -> backend de mensajería
```

Un servicio registra su implementación con `createMessagingBackend`. NRPC
utiliza los metadatos generados para encontrar el método solicitado, valida la forma de la llamada
en el límite del cliente, restaura los valores tipados e invoca el método de implementación
correspondiente. Un método que devuelve `AsyncIterable` se entrega como un flujo; los métodos
ordinarios producen una única respuesta.

## Rutas de entrega

NRPC conserva el mismo contrato en varios entornos de ejecución:

- Los clientes de navegador utilizan un canal WebSocket compartido para enviar solicitudes a Fujin.
- Los clientes de servicio y nativos utilizan el transporte del clúster a través de Fujin, direccionados
  a un destino de proceso lógico en lugar de a una dirección de host.
- Los clientes de flujos de trabajo utilizan el punto de entrada de RT, que realiza llamadas mediante el transporte
  de host QuickJS/Zig y permanece síncrono para una única evaluación del flujo de trabajo.

Fujin enruta una solicitud a la conexión de destino. El proceso receptor elige
el servicio y el método NRPC a partir de los metadatos de la solicitud; Fujin no necesita
entender los servicios de dominio de la plataforma. `createHttpBackend` está disponible
cuando se requiere un perímetro HTTP y puede registrar la misma implementación del servicio
en el entorno de ejecución de mensajería, manteniendo alineadas las llamadas HTTP e internas.

## Contexto y acceso

Las llamadas transportan datos de correlación, plazos y un contexto de espacio de trabajo o ámbito
confiable en su envoltorio. El servicio receptor se ejecuta con ese contexto, lo que
permite que el código de almacenamiento y autorización utilice el mismo límite de inquilino que se
estableció en el perímetro. Los servicios no deben derivar la identidad del espacio de trabajo a partir de una
carga útil de negocio.

El decorador `@Access` declara una clase o método como `public`, `user` o
`internal`. NRPC resuelve el nivel declarado más específico y aplica las reglas de permisos
configuradas antes de invocar la implementación. Esto convierte la política de acceso en
parte del límite del servicio, en lugar de dejarla como una convención incoherente del cliente.

## Límite de responsabilidades

NRPC se encarga de los metadatos del contrato, los clientes tipados generados, la serialización
de valores, el despacho de llamadas y los adaptadores de transporte utilizados por esas llamadas. No se encarga de
las reglas de negocio, el descubrimiento de servicios, la ubicación de despliegues, la persistencia de dominio ni
el enrutamiento del bus de mensajes. Esas responsabilidades permanecen, respectivamente, en el servicio,
el plano de control de despliegue, la capa de almacenamiento y Fujin.

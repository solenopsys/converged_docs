## Procesos

### Arquitectura sin una red de dependencias

Converged es una plataforma abierta en la que la comunidad puede crear, conectar y actualizar continuamente miles de Servicios, módulos y Flujos de trabajo. Estos componentes evolucionan de forma independiente, aunque deben seguir funcionando juntos con precisión.

En las arquitecturas de servicios tradicionales, esto crea un problema grave a medida que el sistema crece: cada componente nuevo puede introducir nuevas conexiones con los componentes existentes. Las llamadas directas, las cadenas de dependencias, la malla de servicios, el enrutamiento y la gestión de fallos crean gradualmente una capa separada de complejidad creciente. Cuando miles de componentes se desarrollan y actualizan de forma independiente, mantener una red de conexiones así se vuelve cada vez más difícil.

**Converged resuelve este problema desde la arquitectura: los Servicios no saben nada unos de otros y nunca se llaman directamente.** En lugar de una red de dependencias directas, el sistema utiliza dos niveles de composición: la UI combina datos, mientras que los Flujos de trabajo combinan operaciones en procesos de negocio.

### Composición de datos y procesos de negocio

En el nivel de la UI, los datos de varios Servicios pueden solicitarse en paralelo y combinarse dentro de un único contexto de usuario. Las funciones ligeras sin estado pueden recuperar datos de distintas fuentes, transformarlos y producir los datos necesarios para una Superficie o Proyección. Los propios Servicios no necesitan saber dónde ni junto a qué otros datos se utilizarán sus resultados.

Las operaciones y los procesos automatizados se gestionan mediante **Flujos de trabajo**. Un Flujo de trabajo es un escenario individual compuesto por una secuencia de scripts y operaciones. Define qué acciones deben realizarse, en qué orden, qué pasos pueden ejecutarse en paralelo, dónde debe esperar el proceso un evento y qué sucede cuando falla una operación.

La plataforma puede contener **miles de Flujos de trabajo independientes**. Cada uno puede utilizar Servicios y scripts existentes sin crear dependencias directas entre los propios Servicios.

Por ejemplo, un Flujo de trabajo puede combinar una solicitud, el cálculo del precio, la aprobación, la puesta en cola, la producción, el control de calidad, el pago y la entrega. Otro Flujo de trabajo puede utilizar los mismos Servicios para un proceso completamente diferente.

### Ejecución mediante Centimanus

**Centimanus** es el motor DAG que ejecuta los Flujos de trabajo. Gestiona las dependencias entre pasos, la ejecución en paralelo, la espera de eventos, los reintentos, la recuperación ante fallos y el estado de los procesos de larga duración.

Cada Flujo de trabajo es un escenario independiente, mientras que Centimanus proporciona un mecanismo de ejecución unificado para todos ellos. Por tanto, añadir un proceso nuevo no requiere modificar los Servicios existentes ni crear nuevas conexiones directas entre ellos.

Esto es especialmente importante para una plataforma abierta. La comunidad puede añadir nuevos Servicios, scripts y Flujos de trabajo sin crear una cascada de dependencias por todo el sistema.

**Como resultado, el número de componentes y procesos puede crecer hasta alcanzar miles sin que la complejidad de sus relaciones crezca proporcionalmente.** Los Servicios permanecen independientes, los datos se componen en el nivel de la UI y las operaciones se combinan mediante Flujos de trabajo individuales.

Esto proporciona a Converged una ventaja arquitectónica al escalar: el sistema puede expandirse mediante nuevos componentes y escenarios sin convertir su interacción en una red cada vez mayor de dependencias directas.

### Ecosistema abierto

Para los desarrolladores, las nuevas capacidades se añaden mediante Servicios, scripts sin estado y Flujos de trabajo. Los agentes de IA también pueden iniciar acciones permitidas dentro de escenarios existentes, manteniéndose dentro de reglas y restricciones definidas.

Para los usuarios habituales, esta complejidad permanece oculta. No necesitan gestionar Servicios, construir grafos ni comprender sus dependencias. Los Flujos de trabajo listos para usar se entregan con las soluciones, mientras que los usuarios pueden configurarlos mediante reglas, roles, plazos, integraciones y notificaciones.

**El usuario simplemente activa el proceso necesario y obtiene un resultado gestionado.**
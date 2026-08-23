## Procesos

El principal problema de un taller que crece rara vez es la falta de un botón más. Con más frecuencia, los procesos viven en la cabeza de las personas: quién debe responder al cliente, cuándo calcular el precio, quién revisa el archivo, cuándo iniciar la producción, a quién avisar si hay retraso y qué hacer después del envío.

En Converged, estas cadenas se describen como workflows. Un proceso típico puede ir desde la solicitud hasta la estimación, aprobación, puesta en cola, producción, control de calidad, pago, entrega y notificaciones. El usuario normalmente no construye un grafo desde cero: los escenarios listos vienen con las soluciones, y la configuración se reduce a reglas, roles, plazos, integraciones y notificaciones.

Técnicamente, la ejecución se traslada a la capa Runtime. Esta ejecuta workflows, tareas cron, pasos de integración y lógica de negocio, permaneciendo stateless: los datos persistentes quedan en los microservicios, y Runtime responde por ejecutar las cadenas. Así la lógica de negocio no queda dispersa por decenas de servicios y existe un lugar claro donde viven las reglas del proceso.

Para implantaciones complejas, los workflows pueden ampliarse. Un desarrollador describe escenarios como clases TypeScript tipadas, y los agentes de IA pueden lanzar acciones permitidas dentro de esos escenarios. Pero para un usuario normal, el objetivo es otro: no construir un editor, sino activar un proceso listo y obtener un resultado gestionado.

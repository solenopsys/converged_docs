# PARAMS

PARAMS extrae los valores que un comando necesita de la solicitud del usuario. Se ejecuta
después de que CASE haya reconocido el comando. Para "show order 4815", CASE selecciona el
comando de pedidos y PARAMS devuelve el número de pedido. La aplicación puede entonces
abrir la pantalla del pedido con ese número ya aplicado.

El comando proporciona los parámetros que acepta y, cuando corresponde, los
valores disponibles que se pueden mencionar en el texto. PARAMS utiliza el modelo
ONNX GLiNER2 para encontrar valores en la solicitud y asociarlos con esos parámetros. El mismo
mecanismo gestiona tanto un valor directo, como un número de pedido, como una opción
con nombre, como un cliente, un estado o un elemento de equipamiento.

Juntos, CASE y PARAMS convierten una solicitud en un comando y sus argumentos.
La aplicación recibe ambas partes y realiza la navegación o la acción habitual.

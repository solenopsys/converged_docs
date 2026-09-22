# RyuGraph

RyuGraph proporciona el almacén de grafos para datos cuyo significado se encuentra en las conexiones entre los registros: dependencias, propiedad, topología, linaje y modelos similares con un gran número de relaciones. Es un motor de grafos de propiedades integrado con consultas Cypher, por lo que un recorrido y las uniones que requiere se ejecutan en el proceso nativo en lugar de reconstruirse en el código de la aplicación.

El motor almacena los datos del grafo en el disco y ejecuta consultas analíticas de grafos mediante almacenamiento columnar, estructuras de adyacencia comprimidas y procesamiento vectorizado de consultas. Converged utiliza el envoltorio para poner este motor a disposición como una biblioteca compartida nativa junto con sus demás componentes de almacenamiento.

La compilación omite intencionadamente los enlaces de lenguaje ascendentes, los ejemplos, el shell y los destinos de referencia de rendimiento. El artefacto resultante contiene el motor de grafos y la ABI requerida por la plataforma.

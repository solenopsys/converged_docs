# RyuGraph

O RyuGraph fornece o armazenamento de grafos para dados cujo significado é transmitido pelas
conexões entre registros: dependências, propriedade, topologia, linhagem e
modelos semelhantes com forte dependência de relacionamentos. Ele é um mecanismo
embutido de grafos de propriedades com consultas Cypher, portanto uma travessia e
as junções necessárias são executadas no processo nativo, em vez de serem reconstruídas no
código da aplicação.

O mecanismo armazena dados de grafos no disco e executa consultas analíticas de grafos
com armazenamento colunar, estruturas de adjacência compactadas e processamento de consultas
vetorizado. O Converged usa o wrapper para disponibilizar esse mecanismo como uma
biblioteca compartilhada nativa junto com seus outros componentes de armazenamento.

A compilação omite intencionalmente as vinculações de linguagem upstream, exemplos, shell
e destinos de benchmark. O artefato resultante contém o mecanismo de grafos e
a ABI exigida pela plataforma.

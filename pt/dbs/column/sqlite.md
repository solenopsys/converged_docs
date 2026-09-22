# SQLite

SQLite é o mecanismo de armazenamento relacional por trás dos wrappers nativos de banco de dados.
Ele armazena um banco de dados em um arquivo local e executa SQL no processo que faz a chamada, o que
permite que um serviço Converged mantenha seus registros, índices e transações próximos ao
código que os utiliza.

A mesma conexão SQLite também serve de base para tabelas especializadas. O Stanchion
adiciona tabelas virtuais colunares para leituras analíticas; `sqlite-vec` adiciona tabelas
vetoriais e consultas de distância. As tabelas comuns e essas extensões podem compartilhar um
banco de dados e participar do mesmo fluxo de trabalho no nível da aplicação.

Este wrapper é a fronteira nativa do SQLite: ele fornece a biblioteca e o caminho de
carregamento de extensões usados pela implementação do armazenamento de nível superior.

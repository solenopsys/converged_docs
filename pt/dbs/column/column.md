# Stanchion

O Stanchion adiciona tabelas colunares ao SQLite. Ele é usado quando um armazenamento Converged precisa ler um pequeno conjunto de campos em muitos registros: medições, histórico de eventos, logs e outros dados orientados à anexação. Uma tabela normal do SQLite mantém uma linha unida; uma tabela Stanchion mantém cada coluna em seus próprios segmentos, portanto uma consulta lê apenas as colunas que menciona.

O Stanchion é exposto por meio da interface de tabela virtual do SQLite. Uma tabela é declarada com `USING stanchion` e uma `SORT KEY`; a chave de ordenação define a ordem física dos registros e permite que a extensão ignore grupos de linhas que não podem corresponder a um predicado. Os valores são armazenados em buffer como inserções pendentes e, em seguida, gravados em segmentos de colunas usando as codificações selecionadas pela extensão.

O wrapper compila a extensão para o runtime nativo do SQLite. O Stanchion ainda é um software alfa: seu formato em disco e as operações de tabela compatíveis ainda não estão definidos.

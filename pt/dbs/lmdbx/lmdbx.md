# LMDBX

LMDBX é o armazenamento ordenado de chave-valor usado quando o Converged precisa de acesso direto
a bytes em vez de SQL. O wrapper abre um ambiente no disco e expõe
operações de inserção, consulta, exclusão, transações e cursores por meio de APIs Zig e C. Os cursores
tornam as varreduras de intervalo e a iteração ordenada parte da mesma primitiva de armazenamento que
as consultas pontuais.

A libmdbx armazena suas árvores B+ em arquivos mapeados em memória e usa MVCC para leitores.
As transações de leitura veem um instantâneo estável enquanto um gravador confirma as alterações. Esse
modelo é adequado para índices e estados de serviço que são lidos com frequência e atualizados em
transações curtas.

O wrapper vincula estaticamente a libmdbx e produz bibliotecas compartilhadas nativas para
os destinos compatíveis. Ele é a camada FFI em torno do mecanismo, não um processo de
banco de dados separado.

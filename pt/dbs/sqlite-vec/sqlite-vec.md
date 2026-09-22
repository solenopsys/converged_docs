# sqlite-vec

`sqlite-vec` adiciona colunas vetoriais e consultas de vizinhos mais próximos aos
armazenamentos SQLite usados pelo Converged. Uma tabela vetorial pode manter os
embeddings junto aos campos que identificam e descrevem o objeto de origem, para
que uma solicitação de pesquisa não precise sair do armazenamento apenas para
classificar registros semelhantes.

A extensão fornece tabelas virtuais `vec0` para vetores float, int8 e binários.
As consultas retornam linhas ordenadas por distância; os metadados, as colunas
auxiliares e as chaves de partição continuam disponíveis para a mesma consulta
SQLite. Isso é útil para os caminhos de pesquisa semântica e recuperação da
plataforma, nos quais a filtragem e a classificação fazem parte de uma única
operação.

O wrapper compila a extensão C upstream como um artefato nativo. O SQLite a
carrega no processo que possui o banco de dados; não há um serviço separado de
pesquisa vetorial nessa integração.

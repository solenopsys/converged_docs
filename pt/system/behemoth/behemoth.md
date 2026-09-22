# Armazenamento do Behemoth

Behemoth é a base nativa de armazenamento do Converged. Ele fornece vários
modelos de dados por meio de um único runtime compacto, preservando ao mesmo
tempo um limite físico de armazenamento separado para cada microsserviço.

## Armazenamento para serviços modulares

Cada serviço de domínio é proprietário de seus dados. Ele não compartilha
tabelas ou índices com serviços não relacionados e não precisa operar uma pilha
de banco de dados separada. Behemoth atende às raízes isoladas a partir de um
processo nativo comum e encaminha cada solicitação para o armazenamento correto.

```text
serviço de pedidos  -> volume de pedidos  -> SQL e arquivos
serviço de chamadas -> volume de chamadas -> chave-valor e fragmentos de áudio
serviço de busca    -> volume de busca    -> índice vetorial
```

A separação é física, não apenas uma convenção de nomenclatura. Se uma raiz de
serviço não estiver montada e declarada, Behemoth se recusa a criar seu
armazenamento. Assim, um erro de implantação se torna visível imediatamente,
em vez de gravar dados em um sistema de arquivos temporário do contêiner.

## Vários modelos de dados

Diferentes cargas de trabalho precisam de estruturas diferentes. Behemoth
combina armazenamento relacional, de chave-valor, colunar, vetorial, de grafos
e de arquivos por trás do mesmo limite de runtime. Um serviço escolhe o
armazenamento adequado aos seus dados sem adicionar um novo produto externo de
banco de dados à plataforma.

Os mecanismos continuam especializados internamente. A camada unificada é
responsável pelo ciclo de vida, isolamento, transporte e metadados, não por
fingir que todos os modelos de dados se comportam da mesma maneira.

## Posicionamento e escalabilidade

O posicionamento do armazenamento é independente do código da aplicação. Uma
instalação de borda pode usar um único processo Behemoth. Implantações maiores
podem dividir escopos entre várias instâncias, enquanto um perfil de nuvem pode
dar a cada locatário sua própria instância de armazenamento.

Cada microsserviço mantém seu próprio volume em todos os perfis. Mover um
escopo ou um serviço para outra instância do Behemoth altera a configuração de
implantação, enquanto os chamadores continuam usando a mesma identidade lógica
de armazenamento.

## Limites de falha e recuperação

Armazenamentos pequenos pertencentes aos serviços reduzem o impacto de
corrupções, migrações e operações de backup. Um problema em um armazenamento
não exige a restauração de um banco de dados compartilhado para toda a
plataforma. Despejos e recuperações podem ser tratados no limite do serviço
afetado, e os serviços não relacionados continuam operando.

## Papel no sistema

As solicitações de armazenamento chegam ao Behemoth por meio do Fujin, como
solicitações a qualquer outro peer de runtime. Ptah fornece o layout dos
volumes e a configuração de montagem. Behemoth executa operações de
armazenamento, mas não coordena fluxos de trabalho de negócios, seleciona
locatários nem define quais serviços uma solução contém.

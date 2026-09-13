# rp-dag

## Objetivo

É responsável pelos gatilhos do fluxo de trabalho e pelo registro de execução. Não executa nada.

## Limite de responsabilidade

Duas coisas pertencem aqui, e nada mais:

- **Gatilhos** — "quando este tópico do barramento aparecer, execute aquele fluxo de trabalho". Configuração do sistema: dezenas de linhas mantidas por um operador, mantidas integralmente na memória do runtime em vez de serem consultadas.
- **O registro de execução** — uma árvore do que uma execução fez. O runtime o escreve enquanto o script é executado: um nó é aberto antes de seu corpo ser executado e fechado quando termina, de modo que uma execução em andamento mostra o nó em que está.

O catálogo de fluxos de trabalho não pertence aqui. O Ptah coloca os descritores da Solution ativa no ambiente deste serviço (`WORKFLOWS`, `WORKFLOW_DIGESTS`, `MODULE_PROXY`) e `listAvailableWorkflows` os republica para o runtime e a interface do usuário. Os bytes de origem permanecem atrás do Ptah-proxy.

## O registro é escrito pelo runtime, não por este serviço

Nada aqui escreve uma entrada de registro. O runtime a formata, coloca-a no Valkey sob uma chave que ele mesmo compõe e depois entrega as chaves — nunca as entradas. `commitLog` transforma cada chave em um local de armazenamento e informa ao storage para buscá-la; o storage lê o cache diretamente, portanto uma entrada atravessa o transporte uma única vez, como bytes que ninguém recodifica.

```text
thread do fluxo ─► fila ─► gravador de registros ─► valkey
                                             │
                                             └─ commitLog([keys]) ─► rp-dag ─► storage lê valkey
                                                                                      │
                                             ◄──── confirmado ─────────────────────────┘
                                             └─ excluir as chaves confirmadas
```

É isso que mantém o registro fora do caminho crítico do fluxo de trabalho: um nó custa ao runtime um acréscimo à fila e nada mais. Isso também significa que o registro é, por construção, de melhor esforço — uma entrada pode ser descartada sob pressão de retorno, e um lote pode ser confirmado duas vezes após uma falha. As chaves são derivadas da execução e da sequência do nó, portanto a segunda confirmação é uma regravação, não uma duplicata.

As chaves vêm do runtime por esse motivo: um número fornecido por este serviço custaria uma ida e volta por nó e não seria reproduzível após uma reinicialização.

- `dag:log:<executionId>:exec` — a execução
- `dag:log:<executionId>:n:<seq>` — um de seus nós, preenchido com zeros até seis dígitos

`commitLog` deriva o local de armazenamento da chave e recusa qualquer coisa fora do prefixo `dag:log:`, portanto uma chave é toda a autoridade que a chamada carrega.

## O registro é uma árvore

```text
exec:<id>              a execução
node:<id>:<seq>        seus nós, na ordem em que foram abertos
```

Um nó que delegou por meio de `rt.sub` carrega o id da execução filha, e a filha é uma execução comum com seus próprios nós. `executionTree` percorre esse vínculo em profundidade e retorna o resultado de forma plana, com cada linha marcada com seu `depth` — assim, um cliente renderiza a árvore recuando e nada mais. Nenhum índice de pai é necessário: o vínculo é o nó que o criou.

As sequências são preenchidas com zeros na chave, porque o armazenamento KV retorna um intervalo de prefixo em ordem lexicográfica, e essa ordem precisa ser a ordem em que os nós foram executados. O runtime usa a mesma largura ao compor a chave do cache; as duas larguras são um único contrato.

A retenção é um limite de execuções (`5000` por padrão), aplicado a cada centésima abertura. O registro é diagnóstico, não um arquivo histórico.

## As alterações nos gatilhos chegam ao runtime pelo barramento

Criar, alterar ou excluir um gatilho publica `dag.triggers.changed`. O runtime se inscreve nesse tópico juntamente com o tópico próprio dos gatilhos, portanto uma edição entra em vigor para o próximo evento em vez de aguardar o fim de um intervalo de consulta. A publicação é de melhor esforço — um barramento indisponível não deve fazer a edição de um operador falhar — e a atualização periódica do runtime continua sendo o mecanismo de segurança.

## Dependências diretas do módulo

- g-bus — para anunciar uma alteração de gatilho

## Participação na Solution

- Não incluído em uma solution predefinida

## Código-fonte

`modules/repositories/automation/rp-dag`

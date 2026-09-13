# sf-community

## Propósito

O fórum, como três abas separadas: seções, os tópicos de uma seção e a
 discussão de um tópico. Abrir uma linha abre uma aba ao lado da atual — não há
 nenhuma tela que mostre uma árvore de seções, uma tabela de tópicos e uma
 discussão ao mesmo tempo.

## Limite de responsabilidade

É responsável pela navegação do fórum e pela tela do tópico. As próprias
mensagens pertencem a `rp-threads`, que o navegador lê diretamente; os anexos
pertencem a `rp-files` por meio de uma mensagem `link`. Membros, funções e
chamados não fazem parte daqui.

## Como um tópico é criado

`createTopic` em `rp-community` gera o id do tópico e o id da discussão e
registra o autor a partir do token; esta superfície então registra a discussão e
escreve a publicação inicial em `rp-threads`. A separação é deliberada: ids que
um cliente pode escolher são ids que ele pode roubar, e um repositório chamando
outro repositório é justamente o que a arquitetura proíbe.

## Atualizações em tempo real

As respostas chegam pelo canal de negócios do Fujin (`pushrouter`) por meio da
biblioteca `threads-state`, e não por consulta periódica. Um push transporta
apenas identificadores; o texto é lido novamente de `rp-threads`, onde o
predicado de leitura é aplicado.

## Dependências diretas do módulo

- `front-core`, `g-community`, `g-threads`, `signal-channel`, `threads-state`

## Participação na solução

- `communications`

## Fonte

`modules/surfaces/communications/sf-community`

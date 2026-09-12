# Barramento de mensagens Fujin

Fujin é o centro de comunicação do runtime Converged. Ele oferece a navegadores,
serviços de domínio, armazenamento, fluxos de trabalho, serviços de mídia e
processadores uma forma compartilhada de trocar mensagens.

## Por que ele existe

Uma plataforma modular precisa que os componentes se movam de forma independente. Links HTTP diretos
fariam com que cada serviço conhecesse endereços, réplicas e a topologia de implantação.
Fujin substitui esses links por destinos lógicos: um remetente informa qual par do runtime
deveria receber uma mensagem, e Fujin a encaminha para a conexão ativa
que atualmente possui esse destino.

```text
sender -> logical target -> Fujin -> live connection -> local service
```

O remetente não sabe onde o receptor está sendo executado. Um processo pode ser reiniciado ou movido
para outro nó e reivindicar o mesmo destino sem alterar seus chamadores.

## Modelo de roteamento

Fujin toma uma decisão de roteamento: mapeia um destino para uma conexão. O destino
seleciona um processo, como o runtime da interface, os serviços de domínio ou o Centimanus. O
nome do serviço dentro da mensagem só é interpretado depois que o processo receptor
a recebe.

Manter essas decisões separadas é importante. Fujin continua sendo um pequeno
broker de mensagens, em vez de se tornar um registro de cada serviço de negócio,
unidade de armazenamento ou fluxo de trabalho.

## Três fluxos

Fujin transporta três tipos de tráfego que compartilham um transporte, mas nada mais.
A comunicação entre serviços move solicitações entre pares. A ingestão de logs recebe tudo o que
os coletores da implantação emitem, agrupa e entrega blocos inteiros aos
repositórios de análise, para que o armazenamento receba lotes em vez de um fluxo de
linhas individuais. As notificações de usuários são mensagens de negócio endereçadas a uma pessoa: um pedido
chegou, um trabalho terminou, uma carta está esperando.

O terceiro é o que precisa de um nome próprio. `pushrouter` é um serviço
hospedado pelo Fujin, em vez de ser roteado para ele, porque a entrega é uma propriedade das sessões
ativas que o Fujin já possui — nenhum outro processo sabe quais dos navegadores de uma pessoa
estão conectados no momento. Ele responde com quantas sessões uma mensagem
alcançou, o que permite ao chamador decidir se um canal durável também é
necessário, e mantém uma janela de reprodução limitada para que um navegador que se
reconecta veja o que perdeu. Tudo o que precisa sobreviver a uma reinicialização pertence a um repositório,
não aqui.

As notificações carregam chaves de tradução em vez de frases. O serviço que
publica uma não conhece o idioma do leitor, portanto uma string renderizada só
poderia estar correta para um deles.

## Tráfego do navegador e do cluster

Os pares nativos se conectam por meio do transporte do cluster. Navegadores e clientes móveis
entram por WebSocket e participam do mesmo modelo de mensagens. Isso oferece
eventos ao vivo para interfaces interativas sem introduzir um segundo sistema de
roteamento de aplicações.

Cargas grandes permanecem fora do canal de controle do navegador. Os clientes recebem um
evento de disponibilidade e recuperam os dados pelo caminho de conteúdo apropriado,
o que mantém a sinalização em tempo real responsiva.

## Contexto e confiança

O envelope comum de mensagens transporta dados de correlação, prazos, erros e
o escopo confiável do tenant. Fujin transporta esse contexto sem derivá-lo
de um payload de negócio ou alterar seu significado. Os serviços receptores podem aplicar
regras de autorização e armazenamento com base no mesmo contexto estabelecido na
borda.

## Limite de responsabilidade

Fujin é responsável pela conectividade e pelo roteamento de destinos. Ele não executa lógica de negócio,
não seleciona um manipulador dentro de outro processo, não armazena dados de domínio nem decide a
alocação da implantação. Essas responsabilidades permanecem com o par do runtime que recebe a
mensagem e com Ptah como plano de controle.

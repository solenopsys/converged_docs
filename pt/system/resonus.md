# Gateway de mídia e IA do Resonus

O Resonus conecta conversas em tempo real à plataforma Converged. Ele gerencia
áudio do navegador, chamadas telefônicas, transcrição e sessões de IA, mantendo
as ações de negócio resultantes dentro do mesmo modelo de permissões e fluxos
de trabalho usado pelo restante do sistema.

## Um único limite de sessão

O transporte de mídia e a interação com a IA compartilham o estado da chamada,
a temporização e o contexto. Mantê-los em um único processo nativo evita passar
uma conversa ao vivo por vários gateways independentes antes que ela possa
chegar a um modelo ou a um operador humano.

```text
navegador ou telefone
       |
       v
    Resonus ---- sessão de IA
       |
       +-------- transferência humana
       |
       +-------- serviços e fluxos de trabalho da plataforma
```

Uma política de implantação escolhe como uma chamada recebida é tratada: por
uma sessão de IA, por um destino humano, por um caminho de transferência ou
por rejeição. A execução do transporte e da mídia permanece nativa, enquanto a
política continua sendo uma pequena camada de decisão substituível.

## Integração com a plataforma

O Resonus usa os serviços da plataforma para o contexto da chamada e os
registros de negócio. Fragmentos de áudio podem passar pelo cache de execução
antes que o serviço proprietário os armazene. As chamadas podem acionar fluxos
de trabalho ou operações de serviço sem dar ao gateway a propriedade desses
domínios.

A transcrição transforma a voz no mesmo tipo de entrada estruturada disponível
para outras interfaces. Isso permite que um operador ou cliente interaja de
forma natural, enquanto a ação resultante ainda segue os contratos normais de
serviço e os caminhos de auditoria.

## Contexto confiável do tenant

Para o tráfego que chega pelo Fujin, o Resonus aceita o escopo do tenant do
envelope de mensagem confiável. Ele não infere um escopo a partir de um número
de telefone, rótulo de usuário ou payload do modelo. O escopo é mantido durante
a sessão e encaminhado aos serviços da plataforma usados por essa sessão.

Os caminhos de entrada que não conseguem estabelecer um escopo confiável devem
ser isolados até que a implantação os associe a um. Isso impede que um
identificador de mídia conveniente se torne silenciosamente uma decisão de
autorização.

## Limite do provedor

Os provedores de IA ficam por trás de um limite comum de sessão e política. A
escolha do provedor, a seleção do modelo, a voz e o comportamento de
transferência são decisões de implantação, e não suposições incorporadas em
todos os módulos de negócio. O gateway pode evoluir seus adaptadores de
provedor sem alterar a forma como o restante do Converged trata uma chamada
assistida por IA.

## Lugar no sistema

O Resonus é responsável pela mídia em tempo real e pela execução de sessões de
IA. Ele não é responsável por registros de clientes, histórico de chamadas,
definições de fluxos de trabalho, seleção de tenants ou roteamento geral de
mensagens. Essas responsabilidades permanecem com os serviços de domínio, o
Centimanus, a borda confiável e o Fujin.

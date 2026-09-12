# Runtime do contrato NRPC

NRPC é a camada de chamadas remotas tipadas da Converged. Ela transforma um
contrato de serviço TypeScript em clientes correspondentes e metadados de
serviço, para que um navegador, microsserviço, fluxo de trabalho ou runtime
nativo possa chamar a mesma capacidade sem manter definições de API separadas
baseadas em strings.

## Por que ele existe

A plataforma é composta por módulos implantados de forma independente. Chamar
um módulo diretamente por meio de um endereço faria com que seus chamadores
dependessem de onde ele é executado e de qual transporte utiliza. O NRPC separa
essas preocupações: um contrato nomeia o serviço e seus métodos, enquanto o
runtime entrega uma chamada ao processo que atualmente possui o destino
solicitado.

Isso mantém o acordo entre chamadores e implementações em um único lugar. Os
parâmetros, o tipo de retorno, o comportamento de streaming e o nível de acesso
de um método são conhecidos pela geração de código e estão disponíveis para
todos os clientes compatíveis.

## Do contrato à chamada

Os contratos são interfaces TypeScript em `modules/types/<domain>`. Executar
`bun run gen` em `core/tools/nrpc` analisa essas interfaces e cria um pacote
`modules/generated/g-<service>`. O pacote contém os metadados do contrato, uma
interface de servidor e fábricas de clientes com segurança de tipos para cada
runtime.

```text
Interface TypeScript
        |
        v
Gerador NRPC -> pacote g-<service>
        |                    |
        |                    +-> cliente de navegador
        |                    +-> cliente de cluster
        |                    +-> cliente de runtime de fluxo de trabalho
        v
implementação do serviço -> backend de mensagens
```

Um serviço registra sua implementação com `createMessagingBackend`. O NRPC
usa os metadados gerados para encontrar o método solicitado, valida o formato
da chamada no limite do cliente, restaura os valores tipados e invoca o método
de implementação correspondente. Um método que retorna `AsyncIterable` é
entregue como um fluxo; métodos comuns produzem uma única resposta.

## Caminhos de entrega

O NRPC preserva o mesmo contrato em vários ambientes de execução:

- Clientes de navegador usam um canal WebSocket compartilhado para enviar
  solicitações ao Fujin.
- Clientes de serviço e nativos usam o transporte do cluster por meio do Fujin,
  endereçados a um destino de processo lógico em vez de um endereço de host.
- Clientes de fluxo de trabalho usam o ponto de entrada RT, que chama por meio
  do transporte de host QuickJS/Zig e permanece síncrono para uma única
  avaliação de fluxo de trabalho.

O Fujin encaminha uma solicitação para a conexão de destino. O processo que
recebe escolhe o serviço e o método NRPC a partir dos metadados da solicitação;
o Fujin não precisa entender os serviços de domínio da plataforma.
`createHttpBackend` está disponível onde uma borda HTTP é necessária e pode
registrar a mesma implementação de serviço no runtime de mensagens, mantendo
as chamadas HTTP e internas alinhadas.

## Contexto e acesso

As chamadas carregam dados de correlação, prazos e um contexto confiável de
workspace ou escopo em seu envelope. O serviço receptor é executado com esse
contexto, o que permite que o código de armazenamento e autorização use o
mesmo limite de tenant estabelecido na borda. Os serviços não devem derivar a
identidade do workspace de um payload de negócio.

O decorador `@Access` declara uma classe ou método como `public`, `user` ou
`internal`. O NRPC resolve o nível declarado mais específico e aplica as regras
de permissão configuradas antes de invocar a implementação. Isso faz com que a
política de acesso seja parte do limite do serviço, em vez de uma convenção
inconsistente do cliente.

## Limite de responsabilidade

O NRPC é responsável pelos metadados do contrato, pelos clientes tipados
gerados, pela serialização de valores, pelo despacho de chamadas e pelos
adaptadores de transporte usados por essas chamadas. Ele não é responsável por
regras de negócio, descoberta de serviços, posicionamento de implantações,
persistência de domínio ou roteamento do barramento de mensagens. Essas
responsabilidades permanecem respectivamente com o serviço, o plano de
controle de implantação, a camada de armazenamento e o Fujin.

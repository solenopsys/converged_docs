# Valkey

O Valkey fornece ao Converged um serviço de chave-valor em memória. Ele é usado para
dados que se beneficiam dos comandos e da semântica de expiração do Valkey: valores
armazenados em cache, contadores, estado de coordenação de curta duração e outros
valores compartilhados que precisam ser lidos ou alterados rapidamente.

O wrapper compila o servidor fornecido como uma biblioteca nativa e o inicia em sua
própria thread. O servidor escuta no endereço local e na porta configurados; em
seguida, o wrapper se comunica com ele por meio da libvalkey. Sua API em C inicia e
interrompe o servidor, verifica a prontidão, informa o uso de memória e executa as
operações de chave-valor compatíveis.

Essa configuração incorporada desativa snapshots e AOF, usa um único banco de
dados lógico e aplica a política de despejo `allkeys-lru` dentro do limite de memória
configurado. Essas configurações tornam o ciclo de vida explícito, em vez de herdar
uma instalação externa do Valkey.

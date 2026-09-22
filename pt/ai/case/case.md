# CASE

CASE interpreta o pedido de um usuário como um comando da plataforma. Ele recebe o conjunto de comandos que a plataforma pode executar e exemplos das frases que expressam cada um deles. A partir de "mostrar equipamentos", ele seleciona o comando que abre a lista de equipamentos. A partir de "mostrar pedido 4815", ele seleciona o comando que abre um pedido.

O serviço compara o pedido com os exemplos de comandos e retorna o comando selecionado com uma pontuação. `EXECUTE` significa que um comando foi reconhecido com clareza suficiente para ser executado. `AMBIGUOUS` significa que vários comandos são próximos demais para escolher entre eles. `UNKNOWN` significa que o pedido não corresponde ao conjunto de comandos.

CASE escolhe o que o usuário está pedindo para fazer. Ele não extrai os detalhes desse pedido. Quando um comando precisa deles, PARAMS lê o mesmo texto e retorna os valores necessários para abrir ou filtrar o resultado: em "mostrar pedido 4815", CASE escolhe o comando de pedido e PARAMS extrai `4815`.

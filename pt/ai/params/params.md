# PARAMS

PARAMS extrai os valores de que um comando precisa a partir da solicitação do usuário. Ele é executado
depois que CASE reconhece o comando. Em "show order 4815", CASE seleciona o
comando de pedido e PARAMS retorna o número do pedido. O aplicativo pode então
abrir a tela do pedido com esse número já aplicado.

O comando fornece os parâmetros que aceita e, quando relevante, os valores
disponíveis que podem ser mencionados no texto. PARAMS usa o modelo ONNX
GLiNER2 para encontrar valores na solicitação e associá-los a esses parâmetros.
O mesmo mecanismo processa tanto um valor direto, como um número de pedido,
quanto uma opção nomeada, como um cliente, status ou item de equipamento.

Juntos, CASE e PARAMS transformam uma solicitação em um comando e seus
argumentos. O aplicativo recebe ambas as partes e executa a navegação ou
a ação habitual.

# Adaptador direto do UVtools

O adaptador do UVtools prepara arquivos para impressoras de resina. Ele executa `UVtoolsCmd`
contra arquivos fatiados, podendo inspecionar camadas, validar um arquivo, repará-lo,
converter entre formatos compatíveis, extrair miniaturas e relatar propriedades do
arquivo ou problemas detectados. Esse trabalho acontece antes de um arquivo ser
entregue a um adaptador de impressora.

O wrapper mantém o UVtools como um executável externo. Sua API expõe o caminho bruto
do argumento, bem como operações nomeadas para conversão, inspeção,
comparação, extração de miniaturas e relato de problemas. Ele retorna a saída
padrão, o erro padrão, o status de saída e o estado do adaptador do processo
filho ao chamador.

O próprio UVtools deve estar instalado no host. O wrapper fornece a fronteira
do processo: tempo limite do comando, diretório de trabalho, limites de saída
e captura do resultado.

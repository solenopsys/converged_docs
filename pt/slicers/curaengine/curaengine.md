# CuraEngine

O CuraEngine prepara trabalhos FDM e FFF para a Converged. Dado um modelo e um perfil
 de impressora, ele divide a geometria em camadas, gera paredes, preenchimento e
 trajetórias de suporte e, em seguida, grava o G-code que uma impressora de extrusão de
 material executa. Ele é o fatiador do ecossistema Cura, usado aqui sem a interface
 de desktop.

O wrapper nativo executa `CuraEngine slice` em um diretório temporário isolado
 e retorna o G-code gerado por meio de sua ABI C. Executar o fatiador fora do
 processo contém seu estado global e os caminhos de falha, de modo que um modelo ou
 perfil inválido não derrube o processador que solicitou o fatiamento.

O wrapper prepara um trabalho; ele não envia G-code para uma impressora. O despacho e
 a execução são tratados posteriormente pelo adaptador de equipamento apropriado.

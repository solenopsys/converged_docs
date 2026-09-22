# OpenCAMLib

O OpenCAMLib fornece a parte geométrica do fluxo de trajetórias de ferramenta CNC no Converged.
Ele trabalha com geometria de superfícies STL e parâmetros da ferramenta de corte para calcular
trajetórias de fresagem e estimativas. Enquanto o CuraEngine constrói trajetórias aditivas camada a camada,
o OpenCAMLib modela o contato da ferramenta de corte com a peça de trabalho para operações
subtrativas.

A biblioteca implementa operações de drop-cutter, push-cutter e waterline, e
oferece suporte a ferramentas de corte cilíndricas, esféricas, bull, cônicas e compostas. O
wrapper local expõe a pequena ABI em C necessária ao fluxo existente de estimativa de
fresagem de STL e compila a biblioteca C++ upstream como um artefato nativo.

O OpenCAMLib produz a geometria da trajetória da ferramenta. O pós-processamento para o dialeto
de comandos de um controlador específico e a execução em uma máquina pertencem aos fluxos de CAM
e de equipamentos que vêm a seguir.

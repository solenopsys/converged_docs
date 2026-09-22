# MTConnect CppAgent

Este wrapper executa o MTConnect C++ Agent para o Converged. O agente recebe
sinais dos adaptadores de máquina configurados e os publica como um fluxo de
dados MTConnect. Ele fornece a equipamentos CNC, robôs, sensores e outros
dispositivos do chão de fábrica um modelo comum que o restante da plataforma
pode consumir.

O wrapper inicia o `cppagent` com um `agent.cfg`, aguarda até que seu endpoint
HTTP esteja pronto e interrompe o processo quando o serviço é liberado. O XML
do dispositivo descreve o modelo do equipamento; a configuração do agente
seleciona adaptadores, portas e opções de execução. Os clientes leem os
endpoints `/probe`, `/current` e `/sample` resultantes do agente em execução.

A integração é deliberadamente baseada em processos. Ela utiliza a
configuração nativa e a interface HTTP do agente, em vez de incorporar sua
biblioteca C++ ao runtime do Zig.

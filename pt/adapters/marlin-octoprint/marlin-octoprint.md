# Adaptador serial do Marlin

O adaptador Marlin é o caminho serial direto do Converged para uma impressora
FDM executando o firmware Marlin. Ele abre a porta serial da impressora, envia
G-code e acompanha os detalhes do protocolo que tornam um fluxo de impressão
confiável: números de linha, somas de verificação, respostas `ok` e solicitações
de reenvio.

A API abrange controle de trabalhos, movimentação e homing, aquecedores,
extrusão, operações no cartão SD, parada de emergência e G-code bruto. As
respostas do firmware são analisadas no estado da impressora: temperaturas,
coordenadas, identidade, progresso no SD e status da impressão. Isso permite que
a camada de equipamentos use um único modelo de estado enquanto o adaptador
continua falando o protocolo serial do firmware.

O nome permanece por motivos de compatibilidade com a API ao redor. O wrapper
não executa o OctoPrint nem chama sua API HTTP; ele se comunica diretamente com
o Marlin.

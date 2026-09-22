# Adaptador local Bambu Lab

O adaptador Bambu Local permite que o Converged trabalhe com uma impressora
Bambu Lab por meio de sua interface de rede local. Ele se conecta ao endpoint
MQTT sobre TLS da impressora, autentica-se com o código de acesso à LAN e
direciona-se ao dispositivo pelo número de série. O controle da impressão e a
telemetria permanecem na rede local; a Bambu Cloud não faz parte desse caminho.

O adaptador publica comandos para pausar, retomar, interromper, JSON bruto e
G-code. Ele assina os relatórios do dispositivo e encaminha o estado mais
recente, as informações da impressora, os erros e a telemetria da impressão por
meio de callbacks. Os chamadores também podem solicitar um snapshot JSON quando
precisarem do estado atual de forma síncrona.

A conexão padrão aceita o certificado autoassinado normalmente apresentado
pelas impressoras no modo LAN. A API de conexão estendida aceita um certificado
CA quando a verificação do certificado é necessária.

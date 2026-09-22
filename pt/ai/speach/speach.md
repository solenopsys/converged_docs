# SPEACH

SPEACH é o caminho de entrada de voz local do Converged. Ele transforma o áudio do microfone e das chamadas no mesmo texto que CASE e PARAMS recebem de um teclado. Assim, uma instrução falada pode entrar no fluxo normal de comandos e parâmetros sem enviar o áudio para um serviço remoto de transcrição.

Para uma solicitação gravada, o SPEACH aceita áudio WAV ou Opus, converte-o em uma forma de onda mono de 16 kHz e executa o modelo CTC local. Para uma perna ao vivo, ele decodifica pacotes Opus, usa detecção de atividade de voz para coletar uma frase e emite eventos parciais e de transcrição concluída. Pausas curtas permanecem dentro de uma frase; o silêncio a encerra. Um segmento é limitado a quarenta segundos.

O reconhecimento termina no texto. O SPEACH não tenta adivinhar a qual comando de tela as palavras se referem. A transcrição segue para o mesmo roteamento com reconhecimento de contexto e extração de parâmetros usados pela entrada digitada.

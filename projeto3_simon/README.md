Esse projeto é um jogo de memória com LEDs e botões, inspirado no Genius (ou Simon):
O funcionamento é o seguinte:
Configuração dos pinos: Há quatro LEDs (vermelho, azul, amarelo e verde) ligados aos pinos 2 a 5, cada LED tem um botão correspondente, conectado aos pinos 6 a 9, com resistores de pull-up internos ativados.
Início do jogo: O programa gera uma sequência aleatória de LEDs, armazenando os valores em um vetor chamado sequence, a cada rodada, a sequência aumenta em um LED.
Exibição da sequência: O Arduino pisca os LEDs na ordem da sequência, com um pequeno intervalo entre eles.
Resposta do jogador: O jogador precisa pressionar os botões correspondentes na mesma ordem, a função waitForPress() aguarda o botão ser pressionado e verifica se ele corresponde ao LED da sequência, se o botão estiver correto, o LED pisca novamente como confirmação, caso o botão errado seja pressionado ou o tempo acabe, o jogo termina.
Fim de jogo: Quando o jogador erra, todos os LEDs piscam três vezes, sinalizando o game over, o programa então reinicia automaticamente, pronto para começar uma nova rodada.


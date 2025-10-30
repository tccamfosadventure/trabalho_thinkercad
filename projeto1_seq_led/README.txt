  Esse projeto controla uma sequência de cinco LEDs conectados ao Arduino. O funcionamento é simples: cada LED acende por três segundos, apaga, e o próximo acende, seguindo essa ordem até o último LED.
  No código, os pinos dos LEDs são guardados em um vetor chamado `leds[]`. Durante o `setup()`, o programa configura esses pinos como saídas. Já no `loop()`, um laço `for` percorre cada LED, ligando e desligando com um intervalo de três segundos. Quando o último LED termina seu ciclo, o programa recomeça automaticamente, mantendo a sequência de acendimento em repetição contínua.


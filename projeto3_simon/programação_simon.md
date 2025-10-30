const int redLED = 2;
const int blueLED = 3;
const int yellowLED = 4;
const int greenLED = 5;

const int redButton = 6;
const int blueButton = 7;
const int yellowButton = 8;
const int greenButton = 9;

int sequence[10];
int waitTime = 4000; // tempo pra apertar o botão

void setup() {
  pinMode(redLED, OUTPUT);
  pinMode(blueLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);

  pinMode(redButton, INPUT_PULLUP);
  pinMode(blueButton, INPUT_PULLUP);
  pinMode(yellowButton, INPUT_PULLUP);
  pinMode(greenButton, INPUT_PULLUP);

  randomSeed(analogRead(0));
}

void loop() {
  int seqNo = 0;
  bool correctSeq = true;

  while (seqNo < 10 && correctSeq) {
    sequence[seqNo] = random(2, 6);

    // Mostra sequência (
    for (int i = 0; i <= seqNo; i++) {
      blink(sequence[i], 700); 
    }

    // Jogador repete
    for (int i = 0; i <= seqNo; i++) {
      if (!waitForPress(sequence[i])) {
        correctSeq = false;
        break;
      }
    }

    seqNo++;
    delay(700); // pausa entre rodadas
  }

  gameOver();
}

// Espera o botão correto
bool waitForPress(int color) {
  unsigned long start = millis();
  while (millis() - start < waitTime) {
    int btn = checkButton();
    if (btn != 0) {
      if (btn == color) {
        blink(color, 300); // pisca quando acerta
        while (checkButton() != 0); // espera soltar o botão
        return true;
      } else {
        return false;
      }
    }
  }
  return false; // tempo acabou
}

// Verifica botão pressionado
int checkButton() {
  if (digitalRead(redButton) == LOW) return redLED;
  if (digitalRead(blueButton) == LOW) return blueLED;
  if (digitalRead(yellowButton) == LOW) return yellowLED;
  if (digitalRead(greenButton) == LOW) return greenLED;
  return 0;
}

// Pisca LED 
void blink(int color, int time) {
  digitalWrite(color, HIGH);
  delay(time);
  digitalWrite(color, LOW);
  delay(200);
}

//game over
void gameOver() {
  for (int i = 0; i < 3; i++) {
    digitalWrite(redLED, HIGH);
    digitalWrite(blueLED, HIGH);
    digitalWrite(yellowLED, HIGH);
    digitalWrite(greenLED, HIGH);
    delay(400);
    digitalWrite(redLED, LOW);
    digitalWrite(blueLED, LOW);
    digitalWrite(yellowLED, LOW);
    digitalWrite(greenLED, LOW);
    delay(400);
  }
  delay(1500);
}

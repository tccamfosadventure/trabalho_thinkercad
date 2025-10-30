#include "LiquidCrystal.h"

LiquidCrystal lcd(1, 3, 4, 5, 6, 7);

const int trigPin = 9;
const int echoPin = 10;
long duration;
int Cm;

float A; 
float B; 
float L;

void setup() {
  
lcd.begin(16,2);
  
pinMode(trigPin, OUTPUT);
pinMode(echoPin, INPUT);
  
  pinMode(13,INPUT); //led azul
  pinMode(12,INPUT); //led verde
  pinMode(11,INPUT); //led amarelo
  pinMode(8,INPUT); //led laranja
  pinMode(3,INPUT); //led vermelho1
  
  pinMode(0,OUTPUT);

}

void loop() {
 
  int valor = analogRead(echoPin);
  delay(1000);
  
digitalWrite(trigPin, LOW);
delayMicroseconds(2);
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

duration = pulseIn(echoPin, HIGH);
Cm= duration*0.034/2;
  
  A= (334 - Cm);
  B= A * 10000;
  L = B/1000;

lcd.setCursor(0,0);
lcd.print("Distance: ");
lcd.print(Cm);
lcd.print("cm");
delay(200);
lcd.setCursor(0,1);
lcd.print("Caixa: ");
lcd.print(L);
lcd.print("L ");
delay(200);


  if (Cm <= 110.33)
  {
  digitalWrite(3,HIGH);
  digitalWrite(8,LOW);
  digitalWrite(11,LOW);
  digitalWrite(12,LOW);
  digitalWrite(13,LOW);
  digitalWrite(0,LOW);
} 
 else if (Cm > 110.33 && Cm <= 165.5)
  {
  digitalWrite(3,LOW);
  digitalWrite(8,HIGH);
  digitalWrite(11,LOW);
  digitalWrite(12,LOW);
  digitalWrite(13,LOW);
} 
  else if (Cm > 165.5 && Cm <= 220.66)
  {
  digitalWrite(3,LOW);
  digitalWrite(8,LOW);
  digitalWrite(11,HIGH);
  digitalWrite(12,LOW);
  digitalWrite(13,LOW);
} 
  else if (Cm > 220.66 && Cm <= 275.833)
  {
  digitalWrite(3,LOW);
  digitalWrite(8,LOW);
  digitalWrite(11,LOW);
  digitalWrite(12,HIGH);
  digitalWrite(13,LOW);
} 
  else if (Cm > 275.833)
  {
  digitalWrite(3,LOW);
  digitalWrite(8,LOW);
  digitalWrite(11,LOW);
  digitalWrite(12,LOW);
  digitalWrite(13,HIGH);
  digitalWrite(0,HIGH);
} 
  
}

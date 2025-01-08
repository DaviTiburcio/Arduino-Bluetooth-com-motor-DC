#include <Servo.h>

#define echoPin 11
#define trigPin 10

Servo myServo; 

char incomingData;

void setup() {

  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);

  myServo.attach(12);  // Conecta o servo ao pino digital 12
  myServo.write(0);    // Posição inicial do servo (0 graus)

  Serial.println("Setup completo! Servo iniciado em 0 graus.");

  Serial.begin(9600);

  pinMode(2, OUTPUT);
  pinMode(3, OUTPUT);


  digitalWrite(2, LOW);
  digitalWrite(3, LOW);
}

void loop() {
 
  if (Serial.available() > 0) {
    incomingData = Serial.read(); 


    switch (incomingData) {

      case '12':
        digitalWrite(2, HIGH);
        digitalWrite(3, HIGH); 
        break;

      case '1':
        digitalWrite(2, HIGH);
        break;

      case '2':
        digitalWrite(3, HIGH);
        break;

      case '0':
        digitalWrite(2, LOW);
        digitalWrite(3, LOW);
        break;

      default:
        break;
    }
  }

   long duracao, distancia;


  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);

  digitalWrite(trigPin, LOW);
  duracao = pulseIn(echoPin, HIGH);

  distancia = (duracao / 2) / 29.1;

  Serial.print("Distancia: ");
  Serial.print(distancia);
  Serial.println(" cm");

  if (distancia < 10) {
    myServo.write(90);  
    Serial.println("Objeto detectado! Servo a 90 graus.");
  } else {
    myServo.write(0);   
    Serial.println("Nada detectado. Servo a 0 graus.");
  }

}

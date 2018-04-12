#include <Servo.h>
#define trigPin P1_4
#define echoPin P1_5

Servo servo;

void setup(){

  Serial.begin (9600);
  pinMode(P2_7,OUTPUT);
  pinMode(P2_5,OUTPUT);
  pinMode(P1_7,OUTPUT);
  pinMode(P8_2,OUTPUT);
  pinMode(P5_1,OUTPUT);
  pinMode(P8_3,OUTPUT);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  servo.attach(P1_0);

}

void loop(){

  long duration, distance;
  servo.write(90);
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH); 
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distance = (duration/2) / 29.1;
  if (distance > 20){
     moveforward();
  //  servo.write(180);
  }else{
   // servo.write(90);
    stopMove();
    int w = watch();
    servo.write(90);
    delay(500);
    if (w==1)
      turnleft();
    else
      turnright();
  }
  delay(500);
}

void moveforward()
{
  digitalWrite(P2_7, HIGH);
    digitalWrite(P2_5, LOW);
   // analogWrite(P1_7, 100);
    digitalWrite(P8_2, HIGH);
    digitalWrite(P5_1, LOW);
   // analogWrite(P8_3, 100);
}

void movebacward(){
   digitalWrite(P2_7, LOW);
    digitalWrite(P2_5, HIGH);
  //analogWrite(P1_7, 200);
    digitalWrite(P8_2, LOW);
    digitalWrite(P5_1, HIGH);
  //  analogWrite(P8_3, 200);
}

void turnleft()
{
   digitalWrite(P2_7, LOW);
    digitalWrite(P2_5, HIGH);
  //analogWrite(P1_7, 1000);
    digitalWrite(P8_2, HIGH);
    digitalWrite(P5_1, LOW);
  //analogWrite(P8_3, 1000);
    delay(500);
}

void turnright()
{
  digitalWrite(P2_7, HIGH);
    digitalWrite(P2_5, LOW);
  //analogWrite(P1_7, 1000);
    digitalWrite(P8_2, LOW);
    digitalWrite(P5_1, HIGH);
  //analogWrite(P8_3, 1000);
    delay(500);
}  

void stopMove()
{
  digitalWrite(P2_7, LOW);
    digitalWrite(P2_5, LOW);
  //analogWrite(P1_7, 0);
    digitalWrite(P8_2, LOW);
    digitalWrite(P5_1, LOW);
  //analogWrite(P8_3, 0);
}  

int watch(){
  long  duration, distanceL, distanceR;
  servo.write(20);
  delay(500);
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH); 
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distanceL = (duration/2) / 29.1;
  delay(500);
  servo.write(180);
  delay(500);
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH); 
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distanceR = (duration/2) / 29.1;
  delay(500);
  if(distanceL > distanceR)
    return 1;
  return 0;
}


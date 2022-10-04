/*
Código realizado para la competencia de libros & libros,
categoria 2 (HANN).

Equipo: Oblivion.
Integrantes:
    - Amilkar José Orozco Galán (tutor).
    - Juan Camilo Calvete Leaño (estudiante).
    - Sebastian Fernando Bula Coba (estudiante).

Colegio Sagrado Corazón de Jesús - Calle 74.
*/

#include <NewPing.h>
#include <Servo.h>

Servo motor1;
Servo motor2;

// Pin de la tarjeta Arduino donde se haya conectado el pin Echo del sensor ultrasonidos
int pinEcho = A0;   
// Pin de la tarjeta Arduino donde se haya conectado el pin Trig del sensor ultrasonidos
int pinTrig = A1; 


int max_distance = 200; // Distancia máxima a detectar en cm
NewPing sonar(pinTrig, pinEcho, max_distance);

void setup(){
pinMode(pinTrig, OUTPUT);
pinMode(pinEcho, INPUT);

motor1.attach(6);
motor2.attach(5);

motor1.write(0);
motor2.write(0);
Serial.begin(9600);
}

void loop(){

int distancia = sonar.ping_cm();
Serial.println(distancia);

if(distancia < 30){

motor1.write(180);
motor2.write(180);
 
}else{

motor1.write(-180);
motor2.write(180);
  
}
}
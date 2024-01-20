# PRACTICA-6
INDICADOR DE NIVEL DE AGUA

Este repositorio muestra como podemos programar una ESP32 con el sensor Ultrasonico y conectar unos led´s de manera que nos sirva como un **indicador visual del nivel de agua**

## Introducción

### Descripción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```Ultrasonico```) para medir los litros de agua de un tanque ; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- HC-SR04 Ultrasonic Distance Sensor


## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).
![](https://github.com/WilberVD/PRACTICA-DHT/blob/main/woki.jpg)


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:

```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int led1 = 22;
const int led2 = 21;
const int led3 = 19;
const int led4 = 18;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=3 && safetyDistance<=102)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=102 && safetyDistance<=201) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=201 && safetyDistance<=300) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=300 && safetyDistance<=399) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}
else
{
 digitalWrite(led1,  LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}

// Prints the distance on the Serial Monitor
Serial.print("litros: ");
Serial.println(distance);
delay (2000);
}

```


2. Hacer la conexion de los sensores **Ultrasonico**  con la **ESP32** y los leds   como se muestra en la siguente imagen.

![](https://github.com/WilberVD/PRACTICA-6/blob/main/CONEXION.jpg)

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la distancia dando *doble click* al sensor **Ultrasonico** 

## Resultados

Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en la siguente imagen.

![](https://github.com/WilberVD/PRACTICA-6/blob/main/FUNCIONAMIENTO.jpg)

# Créditos

Desarrollado por Wilber Valladares Diaz

- [GitHub](WilberVD (github.com))
- [LINK DEL PROGRAMA EN WOKI](https://wokwi.com/projects/387397504423951361)

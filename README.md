# PRACTICA ESP32 CON SENSOR DE DISTANCIA PARA SABER EL NIVEL DE AGUA.
Este repositorio muestra como podemos programar una ESP32 con el sensor ultrasonico esto para medir en nivel de agua en una tina.

## Introducción

### Descripción

La Esp32 la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor ultrasonico para amedir en nivel de agua en una tina ; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).


## Material Necesario

Para realizar esta practica necesitas lo siguiente

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor ultrasonico
- 4 Leds
- 4 Resistencias



## Instrucciones

### Requisitos previos

Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente programación:


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
if (safetyDistance>=2 && safetyDistance<=5)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=5 && safetyDistance<=10) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}

else if(safetyDistance>=10 && safetyDistance<=15) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}

else if(safetyDistance>=15 && safetyDistance<=20) 
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
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}


2. Hacer la conexion de *DHT22*, pantalla *lcd16x2(I2C)* con la *ESP32* como se muestra en la siguente imagen.


![](https://github.com/jroldanap/niveldeagua/blob/main/CON.png?raw=true)

### Instrucciónes de operación

1. Iniciar simulador dando click en el boton verde de play.
2. Visualizar los datos en el monitor serial.
3. Colocar la distancia  dando doble click al sensor *ultrasonico* 
4. Visualizar los leds prendidos cuando se cumplen las condiciones.

## Resultados

Cuando haya funcionado, veras los leds correspondientes prender segun la condición.

1era condicion
![](https://github.com/jroldanap/niveldeagua/blob/main/funcionamineto%201.png?raw=true)

2da condicion
![](https://github.com/jroldanap/niveldeagua/blob/main/da%20condicion.png?raw=true)

3ra condicion
![](https://github.com/jroldanap/niveldeagua/blob/main/ra%20condicion.png?raw=true)

4ta condicion
![](https://github.com/jroldanap/niveldeagua/blob/main/ta%20cond.png?raw=true)



## Evidencias de programa corriendo

1era condicion
![](https://github.com/jroldanap/niveldeagua/blob/main/funcionamineto%201.png?raw=true)

2da condicion
![](https://github.com/jroldanap/niveldeagua/blob/main/da%20condicion.png?raw=true)

3ra condicion
![](https://github.com/jroldanap/niveldeagua/blob/main/ra%20condicion.png?raw=true)

4ta condicion
![](https://github.com/jroldanap/niveldeagua/blob/main/ta%20cond.png?raw=true)



# Créditos

Desarrollado por Jorge Alberto Roldan Aponte

- [GitHub](https://github.com/jroldanap)
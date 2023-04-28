# aud5i022-2023-control

## pauta

- punto base
- asistencia
- materiales
- circuito

- código

// Control l Arduino 28 de abril 2023
// Maria Cecilia Clemente y Noelia Poblete
// AUD5L022-1
//Código editado de https://www.geekfactory.mx/tutoriales-arduino/tutorial-arduino-con-fotoresistencia-ldr/

// Declaración de los pines utilizados
const int rojo = 3; 
const int amarillo = 6;
const int verde = 5;
const int LDR = A0;

void setup() {
  // Configuración de los pines de los LED como salidas
  pinMode(rojo, OUTPUT);
  pinMode(amarillo, OUTPUT);
  pinMode(verde, OUTPUT);

  Serial.begin(9600);
  
}

void loop() {
  // Lectura del valor analógico del LDR
  int ldrValue = analogRead(LDR);

  Serial.println(ldrValue);
  
  // Convertir el valor del LDR a un valor de brillo para los LEDs (entre 0 y 255)
  int brightness = map(ldrValue, 0, 1023, 0, 255);
  
  //La cantidad de luz en la sala que logra leer el fotoresistor tiene un valor de 300, por ende, decidimos programar nuestras luces con valores graduales mayores o iguales a 400 para que su encendido dependade su proximidad a la luz.
   if (ldrValue > 400) {
  analogWrite(rojo, brightness / 2);
    } else {
    analogWrite(rojo, 0);
  }
  
  
  
  if (ldrValue > 600) {
    analogWrite(amarillo, brightness / 1);
  } else {
    analogWrite(amarillo, 0);
  }
  
  
  if (ldrValue > 800) {
    analogWrite(verde, brightness / 1);
  } else {
    analogWrite(verde, 0);
  }
  
  // Espera un poco antes de leer el LDR nuevamente
  delay(3);
}

- imágenes
- conclusiones

Fue complejo programar el resistor y la coordinación de múltiples LED, tuvimos que rehacer la conexión del resistor, nos equivocamos en un momento y conectamos el resistor "a la nada", pero una vez que lo logramos aprendimos a conectar cada elemento en lugares accesibles donde sea fácil trabajar con ellos. Una vez que lo logramos fue gratificante y ahora sabemos cómo programar más de un LED con sus respectivos resistores y un fotoresistor. 

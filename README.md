
##  💻 Sistema de Procesamiento de Datos 💥

## 😎 Integrantes
✨ Pardo Agustina

✨ Sassone Irina

## Proyecto
![ArduinoTinkercad](https://github.com/AGUSPARDO/ArduinoSPD/assets/123899891/45760a22-5013-42a8-b251-a19298c326d5)

### Parte 1 : Contador de 0 a 99 con Display 7 Segmentos y Multiplexación

![Proyecto_Uno](https://github.com/AGUSPARDO/ArduinoSPD/assets/123899891/b3328a50-715d-4280-a1e1-a76853524541)


### Descripción
Este emocionante proyecto tiene como objetivo la creación de un contador que abarca desde 0 hasta 99, utilizando dos displays de 7 segmentos y tres botones para controlar el valor del contador. Para lograr esta tarea, implementamos una técnica crucial llamada "multiplexación", que permite alternar y mostrar los dígitos en los dos displays de 7 segmentos de manera eficiente. El contador comienza en 0 y es capaz de aumentar o disminuir su valor en una unidad con los botones correspondientes, proporcionando así una solución interactiva y visualmente atractiva.

### Función Principal
La función más importante en este código se llama mostrarContador. Esta función se encarga de controlar y actualizar la visualización en los displays de 7 segmentos de acuerdo con el valor del contador proporcionado como argumento. Aquí tienes una breve explicación de la función mostrarContador:
```
// Función que muestra el valor del contador en los displays de 7 segmentos
void mostrarContador(int contador) {
    // Apaga el primer display
    apagarDisplay(DISPLAY_UNO); 
    // Muestra el dígito de las decenas en el primer display     
    mostrarDigito(contador / 10);    
    // Enciende el primer display para mostrar el dígito de las decenas
    prenderDisplay(DISPLAY_UNO);
    // Apaga el segundo display
    apagarDisplay(DISPLAY_DOS);    
    // Muestra el dígito de las unidades en el segundo display  
    mostrarDigito(contador % 10);    
    // Enciende el segundo display para mostrar el dígito de las unidades
    prenderDisplay(DISPLAY_DOS);      
}
```
En esta función, se realiza la multiplexación para mostrar los dígitos en los dos displays de 7 segmentos. Primero, apaga un display, muestra el dígito de las decenas, enciende ese display y luego apaga el otro display, mostrando el dígito de las unidades y encendiéndolo. Esto permite mostrar el contador completo en dos dígitos.

### Parte 2: Modificación con Interruptor Deslizante y Números Primos


![t725](https://github.com/AGUSPARDO/ArduinoSPD/assets/123899891/b44839dd-4ed4-407d-a5ba-10027037ac84)


### Descripción
En la segunda parte del proyecto, hemos mejorado el contador de 0 a 99 utilizando displays de 7 segmentos. Hemos reemplazado los botones por un interruptor deslizante de dos posiciones que permite alternar entre mostrar el contador y los números primos. Además, se ha integrado un motor de aficionado y un sensor de temperatura. El motor se activa cuando se muestran números primos y la temperatura supera los 25°C. Esta versión combina visualización digital y una respuesta física a las condiciones ambientales.

### Función Principal

La función principal en esta segunda parte del proyecto es loop(). En esta función, se lee el estado del interruptor deslizante para alternar entre dos modos de visualización: contador y números primos. Además, se monitorea la temperatura ambiente a través de un sensor. En el modo contador, se muestra el valor actual en los displays de 7 segmentos, y en el modo números primos, se muestra el siguiente número primo en el rango de 0 a 99. Cuando se muestran números primos y la temperatura supera los 25 grados Celsius, se activa un motor de aficionado. La función loop() también actualiza continuamente el contador y controla el tiempo para cambiar de número primo. En resumen, esta función orquesta la lógica principal del proyecto y permite una visualización versátil y reactiva a las condiciones ambientales.
```
void loop() {
    int estadoInterruptor = digitalRead(INTERRUPTOR);
    //SENSOR TEMP.
  	int lecturaSensor = analogRead(SENSOR);
  	//Funcion MAP transforma lectura de analog read en lo que deseo en este caso temp con param.
	int temperatura;
  	temperatura = map(lecturaSensor,20,358,-40,125);
  	Serial.println(temperatura);

    if (estadoInterruptor != interruptorEstadoAnterior) {
        // Si el interruptor cambia de estado, reinicia el contador a cero
        contador = 0;
        cambiarDisplay(mostrarContadorFlag);
        interruptorEstadoAnterior = estadoInterruptor;
    }

    if (estadoInterruptor == LOW) {
        mostrarContadorFlag = true;
      	digitalWrite(MOTOR, LOW);
    } else {
        mostrarContadorFlag = false;
    }

    if (mostrarContadorFlag) {
        mostrarContadorEnDisplays(contador);
        if (millis() - cambioTiempo >= tiempoEntreCambio) {
            contador++;
            if (contador > 99) {
                contador = 0;
            }
            cambioTiempo = millis();
        }
    } else {
        int primo = siguientePrimo(contador);
        mostrarContadorEnDisplays(primo);
        // Enciende el motor cuando se muestra un número primo y la temperatura es mayor a 25
        if (temperatura > 25 && esPrimo(primo)) {
            digitalWrite(MOTOR, HIGH);
        } else {
            digitalWrite(MOTOR, LOW);
        }

        if (millis() - cambioTiempo >= tiempoMostrarPrimo) {
            cambioTiempo = millis();
            contador = primo;
        }
    }
}
```


### Parte 3: Modificación según el Último Número de Documento

![t725 (1)](https://github.com/AGUSPARDO/ArduinoSPD/assets/123899891/73e045cb-2345-499a-b2c1-b41d756b061e)

### Descripción
En la tercera parte de este proyecto, se agregó un sensor de luz ambiental para medir la intensidad de la luz en el entorno. Este sensor se integra al proyecto para detectar si la luz ambiental supera un umbral predefinido y, en caso afirmativo, enciende un LED indicador. Esto permite al proyecto adaptarse a diferentes condiciones de iluminación en su entorno, mejorando su versatilidad y proporcionando una experiencia interactiva más completa.

### Función Principal
La función más importante en la Parte 3, que incorpora el sensor de luz ambiental, sigue siendo loop, ya que coordina las operaciones generales del proyecto y agrega la funcionalidad del sensor de luz ambiental y otros elementos sin cambiar la función principal de la Parte 2.
```
void loop() {
    int estadoInterruptor = digitalRead(INTERRUPTOR);
    //SENSOR TEMP.
  	int lecturaSensor = analogRead(SENSOR);
  	//Funcion MAP transforma lectura de analog read en lo que deseo en este caso temp con param.
	int temperatura;
  	temperatura = map(lecturaSensor,20,358,-40,125);
  	Serial.print("Temperatura: ");
  	Serial.println(temperatura);
  	
  	int lecturaLuz = analogRead(FOTORESISTOR);
    Serial.print("Luz: ");
    Serial.println(lecturaLuz);
  	
  	if (lecturaLuz > umbralLuz) {
        digitalWrite(LED, HIGH); // Enciende el LED si la lectura del fototransistor supera el umbral
    } else {
        digitalWrite(LED, LOW); // Apaga el LED si no supera el umbral
    }

    if (estadoInterruptor != interruptorEstadoAnterior) {
        // Si el interruptor cambia de estado, reinicia el contador a cero
        contador = 0;
        cambiarDisplay(mostrarContadorFlag);
        interruptorEstadoAnterior = estadoInterruptor;
    }

    if (estadoInterruptor == LOW) {
        mostrarContadorFlag = true;
      	digitalWrite(MOTOR, LOW);
    } else {
        mostrarContadorFlag = false;
    }

    if (mostrarContadorFlag) {
        mostrarContadorEnDisplays(contador);
        if (millis() - cambioTiempo >= tiempoEntreCambio) {
            contador++;
            if (contador > 99) {
                contador = 0;
            }
            cambioTiempo = millis();
        }
    } else {
        int primo = siguientePrimo(contador);
        mostrarContadorEnDisplays(primo);
        // Enciende el motor cuando se muestra un número primo y la temperatura es mayor a 25
        if (temperatura > 25 && esPrimo(primo)) {
            digitalWrite(MOTOR, HIGH);
        } else {
            digitalWrite(MOTOR, LOW);
        }

        if (millis() - cambioTiempo >= tiempoMostrarPrimo) {
            cambioTiempo = millis();
            contador = primo;
        }
    }
}
```



### 🤖 Enlaces al Proyecto
Puedes encontrar más detalles y el código fuente de nuestros proyectos: 

🌟Parte 1 en [este enlace](https://www.tinkercad.com/things/0eTntFCBWut?sharecode=yzwHhfn_uPqiHSUPGH1Mm2tKrUIFOl7Cr3AhCLUSpms)

🌟Parte 2 en [este enlace](https://www.tinkercad.com/things/dcBgZpA0Ob5?sharecode=NgFRvHaiIKIEFd5GLVA9g6_qzRWeY9xMHloZ0mLg1jk)

🌟Parte 3 en [este enlace](https://www.tinkercad.com/things/jIqqVZ08YlE?sharecode=ylVlUf1VscF7EYQJx7HGwiXBswUNr06PZD3KbVdRrBU)

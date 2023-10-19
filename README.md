
##  💻 Sistema de Procesamiento de Datos 💥

## 😎 Integrantes
✨ Pardo Agustina

✨ Sassone Irina

## Proyecto
![ArduinoTinkercad](https://github.com/AGUSPARDO/ArduinoSPD/assets/123899891/45760a22-5013-42a8-b251-a19298c326d5)

### Parte 1 : Contador de 0 a 99 con Display 7 Segmentos y Multiplexación

![Proyecto_Uno](https://github.com/AGUSPARDO/ArduinoSPD/assets/123899891/b3328a50-715d-4280-a1e1-a76853524541)


### Descripción
Este proyecto consiste en la creación de un contador de 0 a 99 utilizando un Display de 7 Segmentos y la técnica de multiplexación. El objetivo es ofrecer una solución que permita mostrar un contador de dos dígitos de manera eficiente y elegante.

### Función Principal
En la función principal de nuestro código, utilizamos los pines B0, B1, B2 y B3, definidos previamente, para controlar los LEDs y realizar la multiplexación en el Display de 7 Segmentos. Esto nos permite mostrar los números del contador en los dos dígitos del display.

### Parte 2: Modificación con Interruptor Deslizante y Números Primos


![t725](https://github.com/AGUSPARDO/ArduinoSPD/assets/123899891/b44839dd-4ed4-407d-a5ba-10027037ac84)


### Descripción
En la segunda parte del proyecto, hemos mejorado el contador de 0 a 99 utilizando displays de 7 segmentos. Hemos reemplazado los botones por un interruptor deslizante de dos posiciones que permite alternar entre mostrar el contador y los números primos. Además, se ha integrado un motor de aficionado y un sensor de temperatura. El motor se activa cuando se muestran números primos y la temperatura supera los 25°C. Esta versión combina visualización digital y una respuesta física a las condiciones ambientales.

### Función Principal

La función principal en esta segunda parte del proyecto es loop(). En esta función, se lee el estado del interruptor deslizante para alternar entre dos modos de visualización: contador y números primos. Además, se monitorea la temperatura ambiente a través de un sensor. En el modo contador, se muestra el valor actual en los displays de 7 segmentos, y en el modo números primos, se muestra el siguiente número primo en el rango de 0 a 99. Cuando se muestran números primos y la temperatura supera los 25 grados Celsius, se activa un motor de aficionado. La función loop() también actualiza continuamente el contador y controla el tiempo para cambiar de número primo. En resumen, esta función orquesta la lógica principal del proyecto y permite una visualización versátil y reactiva a las condiciones ambientales.

### Parte 3: Modificación según el Último Número de Documento

![t725 (1)](https://github.com/AGUSPARDO/ArduinoSPD/assets/123899891/73e045cb-2345-499a-b2c1-b41d756b061e)

### Descripción
Este proyecto consiste en la creación de un contador de 0 a 99 utilizando un Display de 7 Segmentos y la técnica de multiplexación. El objetivo es ofrecer una solución que permita mostrar un contador de dos dígitos de manera eficiente y elegante.

### Función Principal
En la función principal de nuestro código, utilizamos los pines B0, B1, B2 y B3, definidos previamente, para controlar los LEDs y realizar la multiplexación en el Display de 7 Segmentos. Esto nos permite mostrar los números del contador en los dos dígitos del display.




### 🤖 Enlace al Proyecto
Puedes encontrar más detalles y el código fuente en nuestro proyecto en [este enlace](https://www.tinkercad.com/things/0eTntFCBWut?sharecode=yzwHhfn_uPqiHSUPGH1Mm2tKrUIFOl7Cr3AhCLUSpms)

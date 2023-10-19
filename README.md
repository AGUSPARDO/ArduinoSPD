
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

```


### Parte 3: Modificación según el Último Número de Documento

![t725 (1)](https://github.com/AGUSPARDO/ArduinoSPD/assets/123899891/73e045cb-2345-499a-b2c1-b41d756b061e)

### Descripción
Este proyecto consiste en la creación de un contador de 0 a 99 utilizando un Display de 7 Segmentos y la técnica de multiplexación. El objetivo es ofrecer una solución que permita mostrar un contador de dos dígitos de manera eficiente y elegante.

### Función Principal
En la función principal de nuestro código, utilizamos los pines B0, B1, B2 y B3, definidos previamente, para controlar los LEDs y realizar la multiplexación en el Display de 7 Segmentos. Esto nos permite mostrar los números del contador en los dos dígitos del display.




### 🤖 Enlace al Proyecto
Puedes encontrar más detalles y el código fuente en nuestro proyecto en [este enlace](https://www.tinkercad.com/things/0eTntFCBWut?sharecode=yzwHhfn_uPqiHSUPGH1Mm2tKrUIFOl7Cr3AhCLUSpms)

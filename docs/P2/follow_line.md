# Follow Line

## Introducción
El objetivo de esta prácitca es aprender a programar y manejar controladores para mejorar la respuesta de un sistema, reduciendo el error y evitando producir
oscilaciones o respuestas lentas.

## Ideas principales
Los objetivos principales de esta práctica son aprender a usar filtros de color y a controlar los sistemas usando un PID.

## Filtro de color
Para el filtro de color lo más sencillo es usar la libreria de python de OpenCV y crear una máscara con los límites del color que queramos, en mi caso con un límite inferior de ``` [(17, 15, 100)] ``` y un límite superior de ``` [(52, 56, 255)] ``` para el color rojo, el resultado ha sido muy bueno.

Una vez definidos los límites solo hay que aplicarlos a la imagen y quedará algo como esto:

![Linea filtrada](./media/Linea_roja.PNG)

## PID
Una vez filtrada la linea, debemos escoger los puntos de referencia que tomaremos.

Estos puntos de referencia nos servirán para tener una estimación de cuánto error hay y así poder usar el PID para arreglarlo y centrar el coche de forma progresiva, 
haciendo el movimiento mucho más fluído.

Para esta práctica he pensado en 3 puntos distintos de referencia, a distintas distancias del coche.

![Puntos de referencia](./media/ref_points.PNG)

Los tres puntos corresponden al punto medio de la linea roja y la linea vertical azul corresponde con la mitad de la pantalla.

Para diseñar el PID, usamos los puntos de referencia y calculamos como de lejos están de la mitad de la pantalla, ya que cuando el coche vaya recto, estos deberían 
coincidir.

A este error obtenido le aplicamos distintas operaciones según el tipo de controlador.

En este caso, al ser un PID, significa que contiene parte proporcional, derivativa e integral.

Por lo tanto, deberemos sumar cada una de las partes:

  1. Proporcional: error * Kp (ganancia proporcional)
  1. Derivativa: (error<sub>t</sub> - error<sub>t-1</sub>) * Kd (ganancia derivativa)
  1. Integral: Σerror<sub>i</sub> * Ki (ganancia integral)

Kp, Kd y Ki son constantes que tendremos que probar a cambiar sus valores hasta obtener el resultado esperado


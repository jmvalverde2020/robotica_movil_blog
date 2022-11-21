# Obstacle Avoidance

## Introducción
El objetivo de esta prácitca es aprender a programar un coche de carreras capaz de navegar y esquivar obstáculos con el método VFF (Virtual Force Field).

## Ideas principales
El método VFF consiste en crear un campo con las fuerzas de atracción y repulsión que generan el objetivo y los obstáculos respectivamente y obtener
la fuerza resultante que será la que mueva el coche, permitiendo seguir el objetivo y evitar obstáculos.

## Metodología
El método VFF se sirve principalmente de 3 elementos:
  -[] Vector de atracción
  -[] Vector de repulsión
  -[] Relación entre repulsión y atracción
 
La correcta implementación de los 3 elementos dará un comportamiento deseable, sin embargo, implementarlos correctamente y conseguir un 
comportamiento robusto ha sido complicado.

## Vector de atracción
En un primer momento puede parecer un problema sencillo, y en parte es el menos complicado de los 3, aunque sí hay que tener un par de cosas en cuenta.

Lo primero es que obtener las coordenadas del objetivo respecto al coche no es suficiente, ya que con un objetivo muy lejano la atracción será demasiado grande y puede provocar comporamientos no deseados.

Por lo tanto el primer paso es acotar el módulo del objetivo para que no sobrepase cierto umbral, este umbral dependerá de cada implementación y en mi caso coincide con la velocidad máxima que quiero que alcanze el vehículo. Esto es porque al obtener las componentes con el nuevo vector acotado, en los casos extremos, la atracción no sobrepasará la velocidad máxima.

Teniendo esto en cuenta, solo resta un problema:

El caso en el que el objetivo está detrás del coche. En este caso, calcular el ángulo puede ser un problema. 
La solución a la que he llegado ha sido que al sobrepasar el objetivo, cambio el signo de las componentes para que la resultante apunte correctamente.

Con esto el vector de atracción está implementado.
  -[x] Vector de atracción
  -[] Vector de repulsión
  -[] Relación entre repulsión y atracción

## Vector de repulsión
Este elemento fue el que más me costó entender para obtener una buena forma de implementarlo, sobretodo debido a pensar de forma errónea cómo funciona.

Lo primero fue entender que la media de las lecturas devuelve el sitio con menos obstáculos (ya que las medidas serán mayores por no tener un objeto cerca, y por lo tanto tendrán más peso en la media), en ese momento ví que realmente lo que buscaba era lo contrario, que los obstáculos tuvieran más peso para, al obtener la media, tener el vector de repulsión.

Para esta tarea creé una función similar a $15 \over e^2x$

[Vuelve al blog](../)

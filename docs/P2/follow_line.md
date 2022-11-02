# Follow Line

## Introducción
El objetivo de esta prácitca es aprender a programar y manejar controladores para mejorar la respuesta de un sistema, reduciendo el error y evitando producir
oscilaciones o respuestas lentas.

## Ideas principales
Los objetivos principales de esta práctica son aprender a usar filtros de color y a controlar los sistemas usando un PID.

## Filtro de color
Para el filtro de color lo más sencillo es usar la libreria de python de OpenCV y crear una máscara con los límites del color que queramos, en mi caso con un límite inferior de ``` [(17, 15, 100)] ``` y un límite superior de ``` [(52, 56, 255)] ``` para el color rojo, el resultado ha sido muy bueno.

Una vez definidos los límites solo hay que aplicarlos a la imagen y quedará algo como esto:

![Linea filtrada](./media/Linea_roja.png)



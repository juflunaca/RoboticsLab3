# Laboratorio 3 - 
## Por: Sebastian Campiño Figueroa, Julián Felipe Luna Castro y Diego Fernando Mejía Hernández

Este reporsitorio contiene los archivos, videos y programas desarrollados en la práctica de Robótíca industrial No. 2. Esta practica está orientada a aprender sobre cómo usar el módulo de entradas y salidas digitales dispuesto en el controlador *ABB IRC5* y también a usar los condicionales en *RAPID*. El objetivo planteado es crear dos salidas y dos entradas digitales, la primera señal de entrada inicia una rutina de escritura en el tablero (en este caso es la letra D) y se enciende una luz de indicación, al final de la rutina el brazo regresa a su posición de HOME donde todos los ángulos articulares son 0 grados. La segunda señal de entrada posiciona el brazo en una pose de mantenimiento donde se puede instalaro desinstalar la herramienta y se apaga la luz de indicación.
Para esta implementación los botones en el mando de señales digitales controlan la transición entre las rutinas.

## Requerimientos

* Robot Studio versión 5 o superior.
* Hoja de datos del manipulador industrial IRB 140.
* Hoja de datos del módulo 3HAC025917-001/00 DSQC 652
* Manipuladores industriales ABB IRB 140.
* Controlador ABB IRC5
* Memoria USB por equipo de trabajo.
* Herramienta
  
## Elaboración de la subrutina en RAPID- Robot Studio
Inicialmente se definié la posición de mantenimiento, para esto se crea un *joint target*, la posición de este punto es **[90,0,0,0,0,0]**, osea la primer articulación del manipulador tiene un valor de 90° y el resto de articulaciones tienen un valor de 0. Posteriormente se crea el Path asociado a la posición de mantenimiento.  Posteriormente en la pestaña de *Controlador* en la opción *Configuration* se selecciona en *Type* la opción *Signal*, en este apartado se crean las nuevas señales, en este caso se asigna un nombre un tipo y se asigna la señal a un *Device*, posterior a esto ya teniendo las señales de entrada y salida respectivas creadas en el apartado RAPID se inicializan las salidas digitales siguiendo la siguiente estructura: *SetDO nombreDO,valor(1 o 0);*. en este caso se le asigna el valor de 0 a la salida digital que está asociada con la luz indicadora cuando el robot termina el movimiento asociado a llegar a la posición de mantenimiento y el valor de 1 cuando inicia la rutina de la escitura de la letra D, para las entradas la estrucura es la siguiente: *WaitDI nombreDI, valor (1 o 0);*. Se ubican en el código las entradas y salidas en la ubicación adecuada y en opción de *I/O Simulator* en la pestaña de *Simulation* se selecciona el controlador y el dispositivo en donde están las entradas y salidas, posterior a esto se ejecuta el programa elaborado y se manipulan las señales de entrada como se muestra en la siguiente sección.

## Simulación en Robot Studio
A continuacion se puede ver un corto video con la simulacion en Robot Studio de los movimientos del manipulador para realizar la trayectoria de escritura en el tablero con las entradas y salidas digitales.

<video width="320" height="240" controls>
  <source src="./videos/VideoSimulacionL3.mp4" type="video/mp4">
</video>

## Implementación LABSIR
Para la implementación de la práctica en el laboratorio LABSIR se carga el programa RAPID al ABB Flex Pendant por medio de una memoria USB, a continuación se definen las entradas haciendo uso del modulo *3HAC025917-001/00 DSQC 652* que está instalado en el controlador ABB IRC5 del laboratorio, luego se define el WorkObject según los datos del WorkObject de Robot Studio y finalmente se inicia la subrutina y se manipulan las entradas como se muestra en los siguientes videos:

<video width="320" height="240" controls>
  <source src="./videos/VideoImplementacionL3-1.mp4" type="video/mp4">
</video>
<video width="320" height="240" controls>
  <source src="./videos/VideoImplementacionL3-2.mp4" type="video/mp4">
</video>

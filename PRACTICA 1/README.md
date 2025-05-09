Práctica 1: GNUradio para el Procesamiento de Señales
###
Integrantes

Edwar Alexis Diaz Rodriguez - 2194682 \
Leonel Ricardo Araque Carreño - 2204224 \
Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones\
Universidad Industrial de Santander

Fecha
07 de marzo del 2025

Declaración de Originalidad y Responsabilidad:

Certifico que el contenido de este informe es original y ha sido elaborado de manera independiente. Cualquier fuente externa utilizada ha sido debidamente citada.

Además, asumo plena responsabilidad por la información presentada en este documento.

Uso de IA: Utilicé ChatGPT como apoyo para mejorar la estructura del informe y revisar la gramática, pero todo el contenido técnico y el análisis fueron desarrollados por nosotros.

**Resumen**\

1A:En esta práctica se exploró el uso de GNU Radio para la generación y procesamiento de señales, analizando su comportamiento en el dominio del tiempo y la frecuencia. Se configuraron bloques 
fundamentales como Signal Source, Throttle, QT GUI Frequency Sink y QT GUI Time Sink. Además, se estudiaron conceptos clave como la teoría de muestreo de Nyquist, interpolación y decimación.
Se realizaron pruebas variando parámetros como frecuencia y amplitud, y se analizaron los efectos de una frecuencia de muestreo inadecuada.

1B: Para esta práctica, además de GNU Radio, se utilizaron diversos equipos de telecomunicaciones, como el osciloscopio, el analizador de espectros y el dispositivo USRP 2920. Con estos instrumentos,
se realizaron mediciones de potencia y amplitud a distintas frecuencias y ganancias, permitiendo analizar el comportamiento del sistema en diferentes condiciones.
 1C:Esta práctica abordó la medición de potencia y frecuencia en sistemas de radio definidos por software, empleando GNU Radio, un osciloscopio y un analizador de espectros. Se analizaron señales en los dominios del tiempo y la frecuencia, evaluando parámetros como ganancia, potencia, ancho de banda y relación señal a ruido (SNR). Se compararon los resultados obtenidos en simulación con los experimentales.
 
Palabras clave: GNUradio, procesamiento de señales, muestreo, interpolación, decimación,Relación señal a ruido (SNR), Ganancia, Frecuencia.




Introducción

1A: El procesamiento digital de señales es un área fundamental en las telecomunicaciones, permitiendo manipular señales en distintos dominios para optimizar su transmisión y recepción.
GNU Radio es una herramienta de software definida por radio (SDR) que facilita este procesamiento sin necesidad de hardware especializado

En esta práctica, además de GNU Radio, se emplearon diferentes equipos de telecomunicaciones como el osciloscopio, el analizador de espectros y el USRP 2920.
Con estos dispositivos, se llevaron a cabo numerosas mediciones que permitieron caracterizar el comportamiento del sistema en distintas condiciones,
evaluar la transmisión y recepción de señales, y comprender la importancia del análisis detallado en sistemas de telecomunicaciones

En la práctica 1A se estudió el efecto del muestreo y los cambios en las señales al variar parámetros clave, abordando preguntas como:
	•	¿Qué ocurre cuando la frecuencia de muestreo no cumple el criterio de Nyquist?
	•	¿Cómo afectan la interpolación y la decimación a una señal?
	•	¿Cuál es la importancia del control de flujo en simulaciones sin hardware SDR?

En telecomunicaciones, comprender el comportamiento de las señales es clave para una transmisión eficiente. Se utilizó el SDR USRP 2920 y el analizador de espectros R&S FPC1000 para evaluar su rango de frecuencias, además de configurar parámetros en GNU Radio y medir señales con un osciloscopio. También se estudió el concepto de piso de ruido y su relación con factores como la frecuencia central, el SPAN y la RBW, fundamentales para la detección de señales débiles.

**Procedimiento**

1A: Configuración del entorno en GNUradio
	1.	Se inició GNUradio y se creó un diagrama de flujo con los siguientes bloques:
	•	Signal Source: Genera señales en distintas formas de onda.
	•	Throttle: Controla el flujo de datos en ausencia de hardware.
	•	QT GUI Frequency Sink: Muestra el espectro de frecuencia.
	•	QT GUI Time Sink: Muestra la señal en el dominio del tiempo.
	2.	Se establecieron variables para controlar parámetros como frecuencia y amplitud, usando QT GUI Range.
 ![imagen1](https://github.com/leo09p/GNURADIO_LABCOMUIS_2025_1_B1A_G4/blob/main/PRACTICA%201/Practica_1A/captura1.png?raw=true)
 En esta captura se pueden visualizar los bloques configurados en GNU Radio, la señal generada y cómo se representan en el dominio del tiempo y frecuencia,se muestra la señal de referencia antes de aplicar transformaciones.

Efectos de la Interpolación y Decimación
	•	Interpolación: Se aumentó la tasa de muestreo y se evidenció cómo la señal se suaviza.
	•	Decimación: Se redujo la tasa de muestreo, observando una reducción en la resolución temporal y posibles efectos de aliasing.
![imagen3](https://github.com/leo09p/GNURADIO_LABCOMUIS_2025_1_B1A_G4/blob/main/PRACTICA%201/Practica_1A/CAPTURA1_4.png?raw=true)
 En esta captura se pueden observar cambios en la forma de onda y el espectro de frecuencia debido a la interpolación o decimación. Un aumento en la tasa de muestreo suaviza la señal, mientras que una disminución puede generar aliasing o pérdida de información.
 
Demostración del Teorema de Nyquist

Se generaron señales senoidales y se estudió el efecto de la frecuencia de muestreo en la visualización de la señal. Se compararon casos con:
	•	Frecuencia de muestreo mayor al doble de la frecuencia de la señal (cumpliendo Nyquist).
	•	Frecuencia de muestreo insuficiente, observando aliasing.
 ![imagen2](https://github.com/leo09p/GNURADIO_LABCOMUIS_2025_1_B1A_G4/blob/main/PRACTICA%201/Practica_1A/captura6_2.png?raw=true)
Esta captura se muestra una señal muestreada en puntos discretos. Si la frecuencia de muestreo es mayor o igual al doble de la frecuencia de la señal, no hay aliasing. Si es menor, se observa solapamiento en el dominio de la frecuencia, lo que valida el Teorema de Nyquist.

Parav la practica 1B nos apoyamos en la guia para realizar la actividad y medir ciertas amplitudes del osciloscopio con frecuencias y ganacias variables
donde los resultados fueron de la siguiente manera: 

![tabla1](https://github.com/leo09p/GNURADIO_LABCOMUIS_2025_1_B1A_G4/blob/main/PRACTICA%201/practica_1B/imagen_2025-03-06_181449587.png)
donde al final se obtuvo unformacion para responder a la preguntas:
1). ¿De que depende la precisión de medida en el osciloscopio?
la precision depende de varios factores. en primer lugar la resolución y sensibilidad del mismo osciloscopio. luego la escala vertical también es importante
ya que al tener la señal muy pequeña se pierden detalles de esta misma y debe ajustarse para tener errores bajos. si la escala es pequeña la señal se recorta
y se satura y genera mediciones inexactas. en la escala horizontal si el tiempo es demasiado grande se pueden perder detalles de variaciones rápidas y si
el tiempo es corto se analiza solo una parte de la señal y no un comportamiento general.

2). 2. Determine el porcentaje de amplitud de la señal recibida con respecto a la señal generada desde el PC. Es igual para todos los casos, en caso de ser diferente
¿a que atribuye esta caída de tensión?

 en el primer caso con fc=200Mhz fe una relación aproximada en cada uno de los subcasos medidos ya que la amplitud en el osciloscopio es ligeramente mayor a la
generada en el pc. mientras que en los demás casos como donde fc=300Mhz la medida de la señal es aproximadamente el doble y en fc=400Mhz es el cuádruple de la
señal generada en el pc. esto se debe a que la frecuencia portadora y la ganancia ya que a medida que la frecuencia aumenta las perdidas pueden ser mayores y al aumentar las ganancias, satura la señal

Para la segunda actividad tenemos la Medida de atenuación de un cable coaxial donde se usaba el analizador de espectros para llenar la siguuente tabla obteniendo diferentes ganancias y calculando luego una grafica de potencia
![tabla2](https://github.com/leo09p/GNURADIO_LABCOMUIS_2025_1_B1A_G4/blob/main/PRACTICA%201/practica_1B/captura%20tablab2%20.png)
![grafica1](https://github.com/leo09p/GNURADIO_LABCOMUIS_2025_1_B1A_G4/blob/main/PRACTICA%201/practica_1B/GRAFICAb2.png)



Para llevar a cabo esta práctica, se realizaron tres actividades principales: la revisión y configuración de los equipos de medición, la simulación de señales en GNU Radio y la transmisión y análisis de señales con el USRP 2920.  los pasos a seguir con la actividad se encuentran en su respectiva carpeta 
cabe acalrar que no se desarrollo en 100% de la actividad propuesta. 


Conclusiones
	•	Se verificó la importancia del teorema de Nyquist en el muestreo de señales.
	•	Se comprobó que la interpolación suaviza la señal y la decimación reduce su resolución.
	•	El uso de GNU Radio facilita la simulación y análisis de señales sin necesidad de hardware SDR.

esta práctica permitió explorar las simulaciones de señales y analizar los factores que afectan su calidad, como pérdidas en cables coaxiales, desajustes de impedancia e interferencias. Se propusieron soluciones como el uso de cables de mejor calidad y amplificadores para optimizar la transmisión. Además, se reafirmó la importancia de respetar el teorema de Nyquist para evitar aliasing y asegurar una representación precisa de las señales.

Referencias
Elaborado con informacion del moodle [UIS, 2025] Universidad Industrial de Santander. Práctica 1A: GNU Radio para el Procesamiento de Señales. Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones, 2025.

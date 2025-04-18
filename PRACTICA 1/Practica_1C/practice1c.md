
# Práctica 1C. Mediciones de potencia y frecuencia

## **Objetivo General**
Familiarizarse con el uso de herramientas de software definido por radio (SDR) como GNU Radio, junto con equipos de medición como el USRP 2920, el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000. Los estudiantes aprenderán a medir y analizar parámetros clave en comunicaciones, como potencia, ancho de banda, relación señal a ruido (SNR) y piso de ruido.

---

## **Materiales y Equipos**
- **USRP 2920**: Radio definido por software.
- **Osciloscopio R&S RTB2004**: Para visualización de señales en el dominio del tiempo y frecuencia.
- **Analizador de Espectros R&S FPC1000**: Para mediciones en el dominio de la frecuencia.
- **Computador con GNU Radio**: Para simulación y generación de señales usando el USRP 2920.
- **Cables y conectores**: Para interconexión de equipos.

---

## **Actividad 1: Revisión de Especificaciones de los Equipos**

### **Objetivo**
Familiarizarse con las especificaciones técnicas de los equipos de laboratorio y entender cómo configurarlos para realizar mediciones.

### **Procedimiento**
1. **Revisar Manuales y Verificar Equipos**:
   - Revisar las especificaciones de los equipos de laboratorio (USRP 2920, Osciloscopio R&S RTB2004 y Analizador de Espectros R&S FPC1000).
   - Identificar las principales funciones y controles de los equipos.

2. **Seleccionar Especificaciones Relevantes**:
   - Seleccionar las **5 especificaciones** que consideren **más relevantes** de cada equipo. 

3. **Configuración de los Equipos**:
   - **USRP 2920**: Identificar el rango de frecuencia y ganancia configurable del radio. Para esto, conecte la alimentación y el cable de red al radio, y desde un terminal (Ctrl + Alt + T) ejecute el comando `uhd_usrp_probe`.
   - **Osciloscopio R&S RTB2004**: Identificar el ancho de banda máximo, resolución vertical y tipos de mediciones soportadas.
   - **Analizador de Espectros R&S FPC1000**: Identificar el rango de frecuencia, resolución y figura de ruido.

### **Preguntas Orientadoras**
1. ¿Cuál es el rango de frecuencia del USRP 2920 y cómo se compara con el del analizador de espectros?

   su rango de frecuencia es de 50Mhz a 2.2Ghz. este cubre un rango de frecuencias mayor en una banda superior lo que lo hace mas util para señales de radio definida por el sofware mientras que el analizador de espectro tiene mejor cobertura en fecuencias mas bajas desde los 5Khz y es mas util en el analicis de esatsa señales
   
2. ¿Qué parámetros del USRP 2920 se deben configurar para transmitir una señal en una frecuencia específica?
   
hay que definir la frecuencia portadora de la señal, ajustar tambien la potencia de salida del transmisor, el ancho de banda de muestreo y ya deoendiendo tambien qe ipo de señal se quiera transmitir 
   
3. ¿Cómo se configura el osciloscopio para medir la amplitud y la frecuencia de una señal?

   se conecta a un canal la señal, configuramos la escala vertical y horizontal para evitar saturaciones y visualizar el periodo de a señal. y para medir la amplitud usamos los cursores verticales o tambien en la funcion de medicion de voltaje pico a pico. para la frecuencia se puede con la fncion de medicion o manualmente con f=1/T
   
4. ¿Qué diferencia hay entre medir una señal en el dominio del tiempo (osciloscopio) y en el dominio de la frecuencia (analizador de espectros)?

en el osciloscopio se muesra como cambia la señal en fncion del tiempo y se usa para analizar la forma de onda y su amplitud. y en el analizador se muestra como se distribuye la energia de la señal en diferenes frecuencias 
   
5. ¿Cómo se mide el piso de ruido en el analizador de espectros? ¿Cómo afecta la frecuencia central, SPAN y RBW la medida de piso de ruido? ¿Por qué?



### **Evidencias**
- Lista con las 5 especificaciones más relevantes de cada equipo.
  
- USRP 2920:
  trabaja en un rango de fecuencia  50Mz a 2.2Ghz
  
  con un ancho de banda de 20Mhz
  
  tiene un formato de muestreo de 12 bits "convertidor de ADC a DAC"
  
  tiene una potencia de transmicion maxima de +20dBm
  
  tiene una sencibilidad de resepcion maxima de -15dBm
  

- OSCILOSCOPIO R&S RTB2004: es un osciloscopio digital Y tactil con taza de muesteo de 2.5GSa/s
  
  trabaja con  canales analogicos
  
  tiene un anco de banda de 70Mhz, 100Mhz, 200Mhz
  
  es generador de patrnes y señales
  
  tiene funciones avanzadas "FFT"

- ANNALIZADOR DE ESPECTROS R&S FPC1000:
  trabaja en rango de frecuencia de 5Khz a 1Ghz

  tiene un anco de banda de resolucion "RBW" desde 1hz hasta 3Mhz

  tiene rango dinamico de 110dB para medicines precisas

  tiene impedancia de entrada de 50 ohms con conector tipo N

  la conectividad soporta USB, LAN y acceso remoto

  **punto 3 **
  USRP 2920: Rango de frecencia es de 68.75 a 2200 Mhz y su rango de ganancia de 0 a 31.5 dB
  
  OSCILOSCOPIO R&S RTB20: tiene un anco de banda de 70Mhz y resolucion de 10 bits,los tipos de
  medida que tiene, alguna de ellas pueden ser medidas de voltae como maximo y minimo, valor RMS etc. tambien mediciones de tiempo fecuencia, periodo ancho de pulso entre otros
  medidas de forma de onda y tambien otra como FFT.

  - ANNALIZADOR DE ESPECTROS R&S FPC1000: el rando de frecuencia es de 5kHz a 1Ghz, tiene resolucion de y 
  
- Realice una medición de piso de ruido normalizado.

---

## **Actividad 2: Simulación de Señales en GNU Radio**

### **Objetivo**
Generar y analizar señales en GNU Radio para entender cómo se comportan diferentes formas de onda en tiempo y frecuencia.

### **Procedimiento**
1. **Iniciar GNU Radio**:
   - Ejecute GNU Radio Companion (GRC) (`gnuradio-companion`).
   - Cargue el flujograma [`simple_flowgraph.grc`](https://github.com/omreyes/LabComUIS/blob/develop/guides/practice1/simple_flowgraph.grc).
   - Identifique los bloques principales: `Signal Source`, `Throttle`, `QT GUI Time Sink` y `QT GUI Frequency Sink`.
   - Configure la frecuencia de muestreo (samp_rate) en 20 kHz.

2. **Ejecutar el Flujograma**:
   - Ejecute el flujograma y observe los diferentes controles (Source Controls, Channel Controls, USRP Controls), así como las señales generadas en las ventanas de tiempo (`Time Sink`) y frecuencia (`Frequency Sink`).
   - Identifique y relacione los bloques presentes en el flujograma con lo observado en la ventana de ejecución.
  
3. **Análisis de Señales** 
   - Analice y valide los resultados en el dominio del tiempo y de frecuencia si se modifica:
     - el tipo de dato de la fuente (compleja o flotante)
     - la forma de onda 
     - la frecuencia y fase de la señal
     - la amplitud de la señal generada.
   - Modifique el nivel de ruido del modelo de canal y analice el efecto en tiempo y frecuencia.

### **Preguntas Orientadoras**
1. ¿Cómo se puede explicar matemáticamente la diferencia entre una fuente de tipo flotante y una de tipo complejo?

una señal tipo flotante genera solo una señal (real), mientras que una compleja tiene dos componentes una en parte real y otra en imaginaria 
la señal flotante se puede representar como x(t)=A*f(t) donde A es la amplitud mientras que la imaginaria se reprencenta como x(t)=A*e^ĵ(2pift+o) equivalente tambien en seno y coseno con una real y otra imaginaria 

2. ¿Cómo afecta la forma de onda a la distribución de energía (potencia) en el dominio de la frecuencia?

la forma de onda determina como se distribuye la energia en el especto. la senoidal pura consentra toda su energia en una unica frecuencia, la fundamental. la triangular tiene una distribucion de energia mas ancha 

3. ¿Qué sucede con la señal en el dominio del tiempo y la frecuencia si se modifican los diferentes parámetros de la fuente? ¿Lo observado corresponde a lo esperado teóricamente?

teoricamente si se cambia la frecuencia se observa un aumento o disminucion en la taza de oscilacion de la señal y un desplazamiento en el pico de la frecuencia. si por otro lado se modifica la amplitud se observa un crecimiento o disminucion en la magnitud de la señal en el tiempo y en la altura del pico en frecuencia. justo como pasa en la practica 

4. ¿Cómo se relaciona la amplitud de la señal con la potencia observada en el dominio de la frecuencia?

la potencia de una señal en el dominio de la frecuencia esta relacionada con el cuadrado de la amplitud en el tiempo. en el dominio de la frecuencia si se duplica la amplitud en el tiempo, la potencia esectral se cuadriplica

5. ¿Qué diferencias se observan entre una señal senoidal y una señal cuadrada en el dominio de la frecuencia?

la señal senoidal tiene un solo pico en su frecuencia. la señal cuadrada tiene multiples armonicos impares con amplitudes decrecientes 

### **Evidencias**
- Capturas de pantalla de señales generadas en el dominio del tiempo y la frecuencia que evidencien cada una de las comparaciones realizadas.

---

## **Actividad 3: Transmisión y Medición de Señales con el USRP 2920**

### **Objetivo**
Transmitir señales usando el USRP 2920 y medir parámetros clave como potencia, ancho de banda, piso de ruido y relación señal a ruido (SNR).

### **Procedimiento**
1. **Configurar el USRP 2920**:
   - Configure el flujograma en GNU Radio para transmitir una señal a través del USRP. Habilite o deshabilite los bloques correspondientes (Channel Model, Throttle, UHD: USRP Sink, Virtual Sink). Para esto seleccione el bloque deseado y presionando `E` (enable) o `D` (disable), respectivamente.
   - Identifique el bloque de frecuencia de muestreo (samp_rate) y observe el efecto de cambiar su valor (e.g. 10 kHz).
   - Configure la frecuencia de muestreo (samp_rate) en 1 MHz.
   - Verifique el efecto de modificar la frecuencia y ganancia del USRP. 

2. **Medición con el Analizador de Espectros**:
   - Conecte la salida del USRP al analizador de espectros.
   - Mida el piso de ruido normalizado a la frecuencia de portadora que va a utilizar.
   - Compare el espectro de la señal observada en el analizador de espectros con la observada en la pantalla de simulación. Tenga en cuenta que el radio (USRP) equivale al diagrama de bloques mostrado en la figura.

<img src="qam_modulator.png" alt="QAM Modulator" width="400">
     
   - Analice y valide los resultados en el dominio de la frecuencia si se modifica:
     - el tipo de dato de la fuente (compleja o flotante)
     - la forma de onda 
     - la frecuencia y fase de la señal
     - la amplitud de la señal generada.
   - Mida potencia de la señal transmitida y ancho de banda de diferentes señales generadas.
   - Conecte una antena apropiada a la entrada del analizador de espectros y observe el espectro de una señal FM (las estaciones FM se sitúan entre los 88 MHz y 108 MHz). Mida su ancho de banda y relación señal a ruido. 
   - Determinar la máxima potencia de transmisión.
   - Evalúe la respuesta en frecuencia del canal midiendo los cambios de ganancia del sistema cuando varía la frecuencia de portadora.
   - Compare los resultados de transmitir usando un cable y usando antenas.

4. **Medición con el Osciloscopio**:
   - Analice y valide los resultados en el dominio del tiempo si se modifica:
     - el tipo de dato de la fuente (compleja o flotante)
     - la forma de onda 
     - la frecuencia y fase de la señal
     - la amplitud de la señal generada.
  - Contraste estos resultados con los obtenidos con el analizador de espectros.

5. **Cálculo de la Relación Señal a Ruido (SNR)**:
   - Usar las mediciones de potencia y piso de ruido para calcular la SNR de algunas de las señales generadas.
   - Anotar el valor de la SNR en dB.

### **Preguntas Orientadoras**
1. ¿Cómo se configura el USRP 2920 para transmitir una señal en una frecuencia específica?
2. ¿Qué parámetros del flujograma afectan la potencia de la señal transmitida?
3. ¿Cómo se mide el ancho de banda de la señal transmitida en el analizador de espectros?
4. ¿Cómo se calcula la relación señal a ruido (SNR) a partir de las mediciones de potencia y piso de ruido?
5. ¿Qué diferencias se observan en las mediciones de potencia cuando se varía la ganancia del USRP?
6. ¿Es posible medir o estimar la potencia de la señal observada en el osciloscopio? ¿Por qué?

### **Evidencia**
- Capturas de pantalla de señales generadas en el dominio del tiempo y la frecuencia que evidencien las principales comparaciones realizadas.
- Captura de la señal FM usada para medición de ancho de banda.

---

## **Actividad 4: Análisis de Resultados y Conclusiones**

### **Objetivo**
Analizar los resultados obtenidos y sacar conclusiones sobre el comportamiento de las señales en diferentes condiciones para elaborar el informe.

### **Para la Elaboración del Informe**
1. **Comparar Resultados**:
   - Compare los resultados obtenidos en las simulaciones y las transmisiones reales.
   - Discuta las diferencias entre las mediciones realizadas con el osciloscopio y el analizador de espectros.

2. **Reflexionar sobre la SNR**:
   - Analice la importancia de la relación señal a ruido (SNR) en las comunicaciones inalámbricas.
   - Discuta cómo el piso de ruido afecta la capacidad de detectar señales débiles.

3. **Conclusiones Finales**:
   - Escriba conclusiones basadas en los resultados obtenidos.
   - Reflexe sobre las limitaciones de los equipos y cómo se podrían mejorar las mediciones.

### **Preguntas Orientadoras**
1. ¿Qué conclusiones se pueden obtener sobre la relación entre la potencia de la señal y la calidad de la comunicación?
2. ¿Cómo afecta el piso de ruido a la capacidad de detectar señales débiles?
3. ¿Qué limitaciones tienen los equipos utilizados en términos de ancho de banda y precisión en las mediciones?
4. ¿Cómo se pueden mejorar las mediciones de señal en un entorno con alto nivel de ruido?
5. ¿Qué aplicaciones prácticas tienen las mediciones de potencia y ancho de banda en sistemas de comunicaciones reales?
6. ¿Cómo se puede medir la respuesta en frecuencia de un canal alámbrico?
7. ¿Cómo se puede obtener un modelo sencillo de las pérdidas (_pathloss_) en un canal inalámbrico?

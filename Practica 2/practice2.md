# Práctica 2A. Modelo de canal

## Objetivos
- Observar cómo el canal puede afectar la calidad de la señal transmitida y cómo  mitigar sus efectos.
- Evaluar aspectos clave como la relación señal-ruido y la eficiencia en la transmisión de datos.

Este enfoque permitirá no solo verificar la teoría, sino también desarrollar habilidades prácticas en el manejo de equipos de laboratorio, como equipos de medición (USRP 2920, osciloscopio R&S RTB2004 y analizador de espectros R&S FPC1000).

---

## Materiales y Equipos

- **USRP 2920:** Radio definido por software.
- **Osciloscopio R&S RTB2004:** Para visualización de señales en el dominio del tiempo y la frecuencia.
- **Analizador de Espectros R&S FPC1000:** Para mediciones en el dominio de la frecuencia.
- **Computador con GNU Radio:** Para simulación y generación de señales usando el USRP 2920.
- **Cables y conectores:** Para interconexión de equipos.
- **Audífonos y micrófono** (opcional, debe traerlo cada grupo)

### Ajustes preliminares

- En el [flujograma](filters_flowgraph.grc) propuesto para esta práctica, se incluye un bloque "Wav File Source". **Antes** de ejecutar el flujograma, seleccione un archivo WAV para ser usado por este bloque. Algunos archivos WAV de ejemplo los puede encontrar en: [LabComUIS/samples/](../../samples/) 
- Tenga en cuenta que existen instrumentos de visualización en dominio tiempo y frecuencia tanto para la señal ANTES como DESPUÉS del filtro.
---

## Actividad 1: Actividades de simulación de canal en GNU Radio

### Objetivo

Familiarizarse con algunos fenómenos de canal en un ambiente simulado.

### Procedimiento

**Simulación**
   - Verificar equipos y elementos a utilizar (revisar manuales de ser necesario)
   - Cargar el flujograma: [filters_flowgraph.grc](filters_flowgraph.grc).
   - Configurar siempre la frecuencia de muestreo (`samp_rate`) en $25e6/2^n$ Hz`, donde $n$ es un número entero mayor a 2.
   - Genere diferentes señales y observe el efecto de variar las frecuencias de corte del filtro.
   - Analice el efecto del ruido en el dominio del tiempo y la frecuencia para al menos dos formas de onda distintas.
   - Muestre con un ejemplo gráfico el umbral de máximo de ruido ante el cual considera que es posible recuperar cada forma de onda utilizando únicamente filtrado.

### Preguntas Orientadoras

-¿Cuál es el efecto de filtrar las frecuencias altas de una señal periódica?
filtrar las frecuencias altas de una señal suaviza su forma de onda, reduce detalles y bordes pronunciados y puede ayudar a eliminar ruido pero también degradar la calidad de la información contenida en la señal

-¿Qué sucede al filtrar muy cerca de la frecuencia fundamental de la señal?

Puede afectar mucho su forma y contenido, si se elimina o atenúa demasiado la señal pierde la estructura principal y se distorsiona. 

-¿Cuál es el efecto de filtrar las frecuencias bajas de una señal periódica?

se eliminaran componentes de baja frecuencia lo que provoca que la señal resultante tenga cambios más  violentos, la señal se vuelve menos suave y más oscilatoria ya que predominarán frecuencias más altas 

-¿Qué ocurre al eliminar los primeros armónicos de la señal?

Los primeros armónicos son los responsables de darle la estructura a la señal, si se eliminan solo algunos puede que se suavice y mantenga su forma parecida a la original. si se eliminan muchos la señal puede ser irreconocible respecto a la original. los primeros armónicos contienen gran parte de la energía de la señal y eliminarlos reduce su amplitud y faceta el contenido espectral

-Explique el fenómeno de la desviación de frecuencia en una señal. Puede hacerlo con al menos dos casos.

La desviación de frecuencia ocurre cuando la frecuencia instantánea de una señal cambia con el tiempo, en una señal modulada en frecuencia, la desviación de frecuencia está controlada por la amplitud de la señal moduladora, En sistemas de comunicación, pequeñas variaciones en el oscilador como el ruido de fase o inestabilidad del oscilador pueden provocar desviaciones no deseadas en la frecuencia, afectando la calidad de la señal recibida. 

-Observe cómo se degrada la señal al aumentar los niveles de ruido. Analice su comportamiento en el dominio del tiempo y la frecuencia para al menos dos formas de onda distintas.
Señal senoidal: En el dominio del tiempo, el ruido aparece como una perturbación aleatoria superpuesta a la onda, dificultando la identificación de su frecuencia original. En el dominio de la frecuencia, el espectro de la señal se ensancha y pueden aparecer componentes no deseadas.
Señal cuadrada: En el dominio del tiempo, los bordes de la señal se vuelven menos definidos y se observan fluctuaciones aleatorias. En el dominio de la frecuencia, los armónicos característicos de la onda cuadrada se ven afectados, y puede haber pérdida de componentes importantes.
Señal triangular:el ruido altera las transiciones suaves de la onda triangular en el tiempo y ensucia su espectro, dificultando su identificación y recuperación en niveles altos de interferencia.

-¿Cómo se puede mejorar la relación señal a ruido en una señal? Demuestre con un ejemplo gráfico y determine el umbral de ruido con el cual es posible recuperar cada forma de onda utilizando únicamente filtrado.	
Se puede mejorar aplicando filtrado pasabajos para reducir el ruido de alta frecuencia o promediado temporal para suavizar las variaciones aleatorias.

### Evidencia

![imagen1](https://github.com/leo09p/GNURADIO_LABCOMUIS_2025_1_B1A_G4/blob/main/Practica%202/Actividad%201/captura2A2.png)
![imagen2](https://github.com/leo09p/GNURADIO_LABCOMUIS_2025_1_B1A_G4/blob/main/Practica%202/Actividad%201/captura2A52.png)
![imagen3](https://github.com/leo09p/GNURADIO_LABCOMUIS_2025_1_B1A_G4/blob/main/Practica%202/Actividad%201/captura2A66.png)

---

## Actividad 2: Fenómenos de canal en el osciloscopio

### Objetivo

Familiarizarse con los fenómenos de un canal alámbrico real en el dominio del tiempo.

### Procedimiento

1. **Configurar el USRP 2920:**
   - Configurar el flujograma [filters_flowgraph.grc](filters_flowgraph.grc) en GNU Radio para transmitir una señal a través del USRP.
   - Habilitar o deshabilitar los bloques correspondientes (`Channel Model`, `Throttle`, `UHD: USRP Sink`, `UHD: USRP Source`, `Virtual Sink`). Para esto, seleccione el bloque deseado y presione **E** (enable) o **D** (disable), según corresponda.
   - Configurar siempre la frecuencia de muestreo (`samp_rate`) en $25e6/2^n$ Hz`, donde $n$ es un número entero mayor a 2. Verifique que la frecuencia de muestreo durante la ejecución, sea la misma que ha configurado en el flujograma.

2. **Configurar el osciloscopio:**
   - Encender, configurar y conectar el osciloscopio a la salida del USRP 2920 usando diferentes cables coaxiales, y ajustando los parámetros necesarios para evidenciar los fenómenos de canal analizados en la Actividad 1.
   - Variar la frecuencia de portadora del USRP entre 50 MHz hasta 500 MHz y anaalizar los resultados.

### Preguntas Orientadoras

- ¿Cuál es el efecto del ruido sobre la amplitud de las señales medidas en el osciloscopio? ¿Conservan las mismas relaciones que se evidencian en la simulación?

  Al comparar ambas imágenes, se nota que la amplitud máxima y mínima de la señal se mantienen constantes. Esto significa que el ruido no está afectando mucho la amplitud general de la señal. En otras palabras, el canal de transmisión no está causando una atenuación significativa ni alterando la relación de amplitudes que se esperaba según la simulación.

- ¿La relación señal a ruido creada intencionalmente en el computador se amplifica o se reduce en la señal observada en el osciloscopio?
  Al observar las señales, la envolvente y la amplitud se mantienen prácticamente sin cambios. Esto confirma que el SNR sigue siendo el mismo, sin amplificación ni reducción significativa en comparación con la simulación. El canal no ha añadido un ruido excesivo que afecte la señal.
- Demuestre ¿cómo se puede mejorar la relación señal a ruido en una señal?

  Mejorar la relación señal a ruido (SNR) requiere un equilibrio entre aumentar la potencia de la señal y reducir lo mayor posible el ruido en el sistema.
  
- ¿Cómo se evidencia el fenómeno de desviación de frecuencia en el osciloscopio? Evidenciar al menos con dos formas de onda.

podemos ver claramente cómo tanto la onda triangular como la cuadrada mantienen su amplitud constante, pero su frecuencia cambia con el tiempo. Esto indica un desplazamiento en la portadora, un fenómeno típico de la modulación en frecuencia (FM). 

- Determine la afectación de un medio de transmisión coaxial (usar cables largos) sobre una señal periódica operando a las capacidades máximas de muestreo del USRP.
  Al usar un cable coaxial largo, la señal pierde amplitud debido a la atenuación, causada por la resistencia y capacitancia del cable. Este efecto es más notable a altas frecuencias y en el límite de muestreo del USRP, ya que la señal se debilita progresivamente a lo largo de la transmisión.
  
  - **NOTA:** La frecuencia de transmisión no debe superar los 500 MHz para ser observada en el osciloscopio. Para el experimento, considere las relaciones de muestreo correspondientes.
- Usando cables coaxiales de diferentes longitudes, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida?
  A mayor distancia entre el transmisor y el receptor, la amplitud de la señal medida disminuye debido a la atenuación introducida por el cable coaxial. Esta pérdida se debe a la resistencia y capacitancia del cable, que aumentan con la longitud, disipando energía y afectando más a señales de alta frecuencia.
- Usando antenas, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? ¿Es posible compensar el fenómeno?
  Al aumentar la distancia entre el transmisor y el receptor, la amplitud de la señal medida disminuye debido a la dispersión y absorción de la energía en el espacio. En la primera medición (23 cm), la amplitud es de 82.74 mV, mientras que en la segunda (46 cm), la amplitud cae a 33.39 V, lo que indica una atenuación significativa.Este fenómeno puede compensarse aumentando la potencia de transmisión, utilizando antenas de mayor ganancia o incorporando amplificadores de señal en el receptor para recuperar parte de la energía perdida.
- ¿Qué modelo de canal básico describe mejor las mediciones obtenidas en la práctica?
- 
El cable corto es la mejor opción en términos de calidad de señal, ya que minimiza la atenuación y mantiene la amplitud original.
### Evidencia
![imagena5c](https://github.com/leo09p/GNURADIO_LABCOMUIS_2025_1_B1A_G4/blob/main/Practica%202/Actividad%202/act2P5cuadrada_2.jpg)
![imagena5t](https://github.com/leo09p/GNURADIO_LABCOMUIS_2025_1_B1A_G4/blob/main/Practica%202/Actividad%202/Act2P5triang_2.jpg)
![imagena7](https://github.com/leo09p/GNURADIO_LABCOMUIS_2025_1_B1A_G4/blob/main/Practica%202/Actividad%202/Act2P7_46cm.jpg)
---

## Actividad 3: Fenómenos de canal en el analizador de espectro

### Objetivo

Familiarizarse con los fenómenos de un canal alámbrico real en el dominio de la frecuencia.

### Procedimiento

1. **Configurar el USRP 2920:**
   - Configurar el flujograma [filters_flowgraph.grc](filters_flowgraph.grc) en GNU Radio para transmitir una señal a través del USRP.
   - Habilitar o deshabilitar los bloques correspondientes (`Channel Model`, `Throttle`, `UHD: USRP Sink`, `UHD: USRP Source`, `Virtual Sink`). Para esto, seleccione el bloque deseado y presione **E** (enable) o **D** (disable), respectivamente.
   - Configurar siempre la frecuencia de muestreo (`samp_rate`) en $25e6/2^n$ Hz`, donde $n$ es un número entero mayor a 2.  Verifique que la frecuencia de muestreo durante la ejecución, sea la misma que ha configurado en el flujograma.

2. **Configurar el Analizador de Espectros:**
   - Encender, configurar y conectar el analizador de espectros a la salida del USRP 2920 usando diferentes cables coaxiales, y ajustando los parámetros necesarios para evidenciar los fenómenos de canal analizados en la Actividad 1.

### Preguntas Orientadoras

- ¿Cuál es el efecto del ruido sobre la respuesta en frecuencia de las señales medidas en el analizador de espectro? ¿Conservan las mismas relaciones que se evidencian en la simulación?
- ¿La relación señal a ruido creada intencionalmente desde el computador se amplifica o se reduce en la señal observada en el analizador de espectro?
- Adjunte la evidencia de la medición de la relación señal a ruido de dos formas de onda distintas.
- ¿Cómo se evidencia el fenómeno de desviación de frecuencia en el analizador de espectro? Evidenciar al menos con dos formas de onda.
- Determine la afectación de un medio de transmisión coaxial (usar cables largos) sobre una señal periódica operando a las capacidades máximas de muestreo del USRP.
  - **NOTA:** La frecuencia de transmisión no debe superar los 1000 MHz para ser observada en el analizador. Para el experimento, considere las relaciones de muestreo correspondientes.
- Usando cables coaxiales de diferentes longitudes, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida?
- Usando antenas, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? ¿Es posible compensar el fenómeno?
- ¿Qué modelo de canal básico describe mejor las mediciones obtenidas en la práctica?

### Evidencia

*(Adjuntar las evidencias de la práctica en el Aula Virtual: capturas de pantalla, observaciones, cálculos o mediciones preliminares)*

## Actividad 4: Efectos de los fenómenos de canal en la conversión de frecuencia

### Objetivo

Familiarizarse con los efectos de los fenómenos de un canal alámbrico e inalámbrico real en la conversión de frecuencia.

### Procedimiento

**Configurar el USRP 2920:**
   - Configurar el flujograma [filters_flowgraph.grc](filters_flowgraph.grc) en GNU Radio para **transmitir y recibir ** una señal a través del USRP.
   - Habilitar o deshabilitar los bloques correspondientes (`Channel Model`, `Throttle`, `UHD: USRP Sink`, `UHD: USRP Source`, `Virtual Sink`). Para esto, seleccione el bloque deseado y presione **E** (enable) o **D** (disable), respectivamente.
   - Configurar siempre la frecuencia de muestreo (`samp_rate`) en $25e6/2^n$ Hz`, donde $n$ es un número entero mayor a 2. Verifique que la frecuencia de muestreo durante la ejecución, sea la misma que ha configurado en el flujograma.
   - Compare los resultados al recibir la señal usando diferentes medios (aire o cable coaxial).

### Preguntas Orientadoras

- ¿Cómo se evidencian los diferentes fenómenos de canal en la señal recibida?
- ¿Cómo se pueden mitigar los efectos del canal en la señal recibida?

### Evidencia

*(Adjuntar las evidencias de la práctica en el Aula Virtual: capturas de pantalla, observaciones, cálculos o mediciones preliminares)*

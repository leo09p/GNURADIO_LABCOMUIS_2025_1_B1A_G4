Práctica 2A. Modelo de canal

Leonel Ricardo Araque Carreño 2204224
Edwar Alexis Diaz Rodriguez 2194682
Objetivo General
Durante la práctica, los estudiantes tendrán la oportunidad de observar cómo estos modelos afectan la calidad de la señal transmitida y como pueden mitigar sus efectos. Además, se evaluarán aspectos clave como la relación señal-ruido y la eficiencia en la transmisión de datos.
Este enfoque práctico nos permitirá no solo verificar las teorías aprendidas en clase, sino también desarrollar habilidades prácticas en el manejo de los equipos de laboratorio como con equipos de medición como el USRP 2920, el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000.

Materiales y Equipos
USRP  2920:  Radio definido por software.
Osciloscopio 	R&S RTB2004:  Para visualización de señales en el dominio del tiempo y  frecuencia.
Analizador 	de Espectros R&S FPC1000: Para mediciones en el dominio de la frecuencia.
Computador 	con GNU Radio: Para simulación y generación de señales usando el USRP 2920.
Cables y conectores: Para interconexión de equipos.


Actividad 1: Actividades de simulación de canal en GNU Radio
Objetivo
Familiarizarse con los fenómenos de canal en un ambiente simulado.
Procedimiento
Revisar Manuales y Verificar Equipos:
Cargue el flujograma Enlace Descarga
Configure siempre la frecuencia de muestreo (samp_rate) en 25e6/2n  Hz. donde n es un número entero mayor a 2. 	
Preguntas Orientadoras
¿Cuál es el efecto de filtrar las frecuencias altas de una señal periódica?
filtrar las frecuencias altas de una señal suaviza su forma de onda, reduce detalles y bordes pronunciados y puede ayudar a eliminar ruido pero también degradar la calidad de la información contenida en la señal

¿Qué sucede al filtrar muy cerca de la frecuencia fundamental de la señal?

puede afectar mucho su forma y contenido, si se elimina o atenúa demasiado la señal pierde la estructura principal y se distorsiona. 

¿Cuál es el efecto de filtrar las frecuencias bajas de una señal periódica?

se eliminaran componentes de baja frecuencia lo que provoca que la señal resultante tenga cambios más  violentos, la señal se vuelve menos suave y más oscilatoria ya que predominarán frecuencias más altas 

¿Qué ocurre al eliminar los primeros armónicos de la señal?

Los primeros armónicos son los responsables de darle la estructura a la señal, si se eliminan solo algunos puede que se suavice y mantenga su forma parecida a la original. si se eliminan muchos la señal puede ser irreconocible respecto a la original. los primeros armónicos contienen gran parte de la energía de la señal y eliminarlos reduce su amplitud y faceta el contenido espectral

Explique el fenómeno de la desviación de frecuencia en una señal. Puede hacerlo con al menos dos casos.



Observe cómo se degrada la señal al aumentar los niveles de ruido. Analice su comportamiento en el dominio del tiempo y la frecuencia para al menos dos formas de onda distintas.



¿Cómo se puede mejorar la relación señal a ruido en una señal? Demuestre con un ejemplo gráfico y determine el umbral de ruido con el cual es posible recuperar cada forma de onda utilizando únicamente filtrado.	
Evidencia
	
Actividad 2: fenómenos de canal en el osciloscopio
_________________________________________________________
Objetivo
Familiarizarse con los fenómenos de canal en un ambiente simulado.
Procedimiento
Configurar el USRP 2920:
Configure el flujograma (Enlace Descarga) en GNU Radio para transmitir una señal a través del USRP. Habilite o deshabilite los bloques correspondientes (Channel Model, Throttle, UHD: USRP Sink, Virtual Sink). Para esto seleccione el bloque deseado y presione E (enable) o D (disable), respectivamente.
Configure siempre la frecuencia de muestreo (samp_rate) en 25e6/2n  Hz. donde n es un número entero mayor a 2. 
Encienda, conecte y configure el osciloscopio con el USRP 2920 con los parámetros necesarios para evidenciar los fenómenos de canal.
Preguntas Orientadoras
¿Cuál es el efecto del ruido sobre la amplitud de las señales medidas en el osciloscopio? 

distorsiona la señal en sus picos…

Conservan las mismas relaciones que se evidencian en la simulación. 

si, lo ocurrido en la simulación sucede simultaneo en el osciloscopio

¿la relación señal a ruido creada intencionalmente en el computador se amplifica o se reduce en la señal observada en el osciloscopio?

se amplifica

demuestre ¿Cómo se puede mejorar la relación señal a ruido en una señal?



¿Cómo se evidencia el fenómeno de desviación de frecuencia en el osciloscopio? evidencie al menos con dos formas de onda




Determine la afectación de un medio de transmisión coaxial (use los cables largos) sobre una señal periódica operando a las capacidades máximas de muestreo del USRP. 
NOTA: La frecuencia de transmisión no debe superar los 500 MHz para ser observada en el osciloscopio. Para el experimento considere las relaciones de muestreo correspondientes,
afecta su amplitud…

Usando cables coaxiales de diferentes longitudes ¿Cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? 

la amplitud del cable largo es mas baja que la del cable coto

usando antenas ¿Cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? es posible compensar el fenomeno


entre mas leos la amplitud se hace más pequeña 


¿Qué modelo de canal básico describe mejor las mediciones obtenidas en la práctica?

cable corto
Evidencia




Actividad 3: fenómenos de canal en el analizador de espectro
_________________________________________________________
Objetivo
Familiarizarse con los fenómenos de canal en un ambiente simulado.
Procedimiento
Configurar el USRP 2920:
Configure el flujograma en GNU Radio (Enlace Descarga) para transmitir una señal a través del USRP. Habilite o deshabilite los bloques correspondientes (Channel Model, Throttle, UHD: USRP Sink, Virtual Sink). Para esto seleccione el bloque deseado y presione E (enable) o D (disable), respectivamente.
Configure siempre la frecuencia de muestreo (samp_rate) en 25e6/2n  Hz. donde n es un número entero mayor a 2. 
Encienda, conecte y configure el analizador de espectro con el USRP 2920 con los parámetros necesarios para evidenciar los fenómenos de canal.
Preguntas Orientadoras
¿Cuál es el efecto del ruido sobre la respuesta en frecuencia de las señales medidas en el analizador de espectro? Conservan las mismas relaciones que se evidencian en la simulación. 


	
¿La relación señal a ruido creada intencionalmente desde el computador se amplifica o se reduce en la señal observada en el analizador de espectro?
adjunte la evidencia de la medición de la relación señal a ruido de dos formas de onda distintas. 



¿Cómo se evidencia el fenómeno de desviación de frecuencia en el analizador de espectro? evidencie al menos con dos formas de onda. 


Determine la afectación de un medio de transmisión coaxial (use los cables largos) sobre una señal periódica operando a las capacidades máximas de muestreo del USRP. 
NOTA: La frecuencia de transmisión no debe superar los 1000 MHz para ser observada en el analizador. Para el experimento considere las relaciones de muestreo correspondientes,

Usando cables coaxiales de diferentes longitudes ¿Cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? 


usando antenas ¿Cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? es posible compensar el fenómeno



¿Qué modelo de canal básico describe mejor las mediciones obtenidas en la práctica?
Evidencia

Actividad 4: Efectos de los fenómenos de canal en la conversión de frecuencia
Objetivo
Familiarizarse con los efectos de los fenómenos de un canal alámbrico e inalámbrico real en la conversión de frecuencia.
Procedimiento
Configurar el USRP 2920:
Configurar el flujograma filters_flowgraph.grc en GNU Radio para **transmitir y recibir ** una señal a través del USRP.
Habilitar o deshabilitar los bloques correspondientes (Channel Model, Throttle, UHD: USRP Sink, UHD: USRP Source, Virtual Sink). Para esto, seleccione el bloque deseado y presione E (enable) o D (disable), respectivamente.
Configurar siempre la frecuencia de muestreo (samp_rate) en 25 e 6 / 2 n Hz`, donde n es un número entero mayor a 2. Verifique que la frecuencia de muestreo durante la ejecución, sea la misma que ha configurado en el flujograma.
Compare los resultados al recibir la señal usando diferentes medios (aire o cable coaxial).
Preguntas Orientadoras
¿Cómo se evidencian los diferentes fenómenos de canal en la señal recibida?


¿Cómo se pueden mitigar los efectos del canal en la señal recibida?
Evidencia
(Adjuntar las evidencias de la práctica en el Aula Virtual: capturas de pantalla, observaciones, cálculos o mediciones preliminares)


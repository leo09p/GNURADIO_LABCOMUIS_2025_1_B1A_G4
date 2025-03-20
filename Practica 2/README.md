# Laboratorio de Comunicaciones
## Universidad Industrial de Santander


# Práctica 2:

### Integrantes
- **Leonel Ricardo Araque Carreño** - 2204224
- **Edwar Alexis Diaz Rodriguez** - 2194682


Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

### Fecha
20 de Marzo de 2025

---

## Declaración de Originalidad y Responsabilidad
Certifico que el contenido de este informe es original y ha sido elaborado de manera independiente. Cualquier fuente externa utilizada ha sido debidamente citada.

Además, asumo plena responsabilidad por la información presentada en este documento.

Uso de IA: Utilicé ChatGPT como apoyo para mejorar la estructura del informe y revisar la gramática, pero todo el contenido técnico y el análisis fueron desarrollados por nosotros

---
## Contenido

### Resumen
En esta práctica de laboratorio, se analizaron los efectos de los modelos de canal en la transmisión de señales mediante simulaciones en GNU Radio y mediciones con equipos de laboratorio. Se estudiaron fenómenos como la atenuación, la relación señal-ruido y la desviación de frecuencia, utilizando herramientas como el USRP 2920, el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000. Se realizaron experimentos tanto en simulaciones como en mediciones físicas para evaluar cómo los diferentes medios de transmisión afectan la calidad de la señal. Finalmente, se exploraron estrategias para mitigar los efectos adversos del canal y mejorar la eficiencia en la transmisión de datos.
**Palabras clave:** de 2 a 5 palabras clave. 

### Introducción
La transmisión de señales en sistemas de telecomunicaciones está sujeta a diversas interferencias y degradaciones debido a los efectos del canal. Factores como el ruido, la atenuación y la dispersión afectan la integridad de la señal, lo que puede comprometer la calidad de la comunicación. Además, la distancia entre el transmisor y el receptor, así como el medio de transmisión utilizado, influyen en la pérdida de información y la relación señal-ruido.

Esta práctica tiene como propósito analizar estos fenómenos mediante la simulación y medición de señales en diferentes condiciones de transmisión. Se estudiará cómo los modelos de canal afectan la propagación de la señal y qué efectos producen en su estructura y calidad.

A través de estos experimentos, se busca comprender cómo se pueden mitigar las degradaciones del canal mediante técnicas como el filtrado y el ajuste de parámetros de transmisión, permitiendo optimizar la comunicación y mejorar la eficiencia en la transmisión de datos.

### Procedimiento
El procedimiento detallado, junto con la configuración de los equipos y los pasos seguidos en cada actividad, se encuentra documentado en el archivo correspondiente a la práctica. En este informe se presentan los resultados obtenidos, el análisis de los efectos del canal en la señal y las conclusiones derivadas del experimento.

### Conclusiones
Se observó que el canal de transmisión afecta significativamente la calidad de la señal, introduciendo fenómenos como atenuación, ruido y distorsión. Estos efectos varían dependiendo del medio de transmisión utilizado (cable coaxial corto, cable largo o antena).
En el cable coaxial corto, la señal se conserva mejor, con mínima atenuación y menos interferencias.
En el cable coaxial largo, la señal experimenta una mayor atenuación, especialmente en altas frecuencias.
En la transmisión por antena, la señal es más susceptible a la interferencia y la pérdida de energía, agravándose con la distancia entre transmisor y receptor


Se evidenció que el ruido puede afectar tanto la amplitud como la estructura espectral de la señal, reduciendo su calidad. A través de filtrado y ajustes en la ganancia del receptor, se pudo mitigar parte del ruido y mejorar la SNR.

Al aplicar filtros, se observó que la eliminación de altas frecuencias suaviza la señal, mientras que la eliminación de bajas frecuencias la hace más oscilatoria. También se confirmó que eliminar los primeros armónicos puede afectar significativamente la estructura de la señal.


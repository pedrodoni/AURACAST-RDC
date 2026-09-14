# Tarea 3

## Cuestionario

### 4.1. ¿Por qué hay dos cables en un par trenzado de cobre?
Los dos cables se entrecruzan formando un bucle espiral para reducir las interferencias electromagnéticas, que se conocen como diafonía, que suceden entre los pares adyacentes confinados en una misma envoltura.

### 4.2. ¿Cuáles son las limitaciones del par trenzado?
En comparación con el cable coaxial o la fibra óptica, el par trenzado soporta menores anchos de banda, menores velocidades de transmisión y un alcance más reducido. Además, es sumamente susceptible al ruido electromagnético y su atenuación está fuertemente ligada a la frecuencia.

### 4.3. ¿Cuál es la diferencia entre el par trenzado no apantallado y el par trenzado apantallado?
El cable UTP es económico y de fácil manipulación, pero altamente vulnerable a interferencias electromagnéticas externas. Por su parte, el STP mitiga estas interferencias al envolver el cable con una malla metálica, mejorando su rendimiento a altas velocidades, aunque resulta más costoso e inflexible.

### 4.4. Describir los principales componentes del cable de fibra óptica.
Un cable de fibra óptica tiene tres secciones concéntricas: el núcleo (compuesto por una o varias fibras plásticas o de cristal), el revestimiento (con propiedades ópticas diferentes para confinar la luz) y la cubierta exterior (que añade protección contra humedad y abrasión).

### 4.5. ¿Qué ventajas y desventajas tiene la transmisión de microondas?
Requieren menos amplificadores que un cable coaxial y permiten alcanzar un gran ancho de banda a frecuencias elevadas. Como desventajas, las antenas exigen una alineación estricta en trayectoria visual, la señal sufre atenuación por la lluvia y las áreas de cobertura solapadas pueden generar interferencias.

### 4.6. ¿Qué es la difusión directa por satélite (DBS, Direct Broadcast Satellite)?
Es una aplicación tecnológica satelital donde las señales de televisión y video se transmiten directamente desde el satélite hacia los receptores en los domicilios de los usuarios.

### 4.7. ¿Por qué un satélite debe usar frecuencias ascendentes y descendentes distintas?
Para lograr una transmisión continua y libre de interferencias, el satélite no puede transmitir y recibir de manera simultánea en una misma banda.

### 4.8. Indique las diferencias más significativas entre la difusión de radio y las microondas.
Las ondas de radio poseen un diagrama omnidireccional, por lo cual no requieren antenas parabólicas ni una alineación precisa entre transmisor y receptor, y son menos sensibles a la lluvia. Las microondas son sumamente direccionales y requieren alineación milimétrica.

### 4.9. ¿Qué dos funciones realiza una antena?
En modo de transmisión, la antena convierte energía eléctrica en energía electromagnética para su radiación. En modo de recepción, captura energía electromagnética del ambiente y la transforma nuevamente en energía eléctrica.

### 4.10. ¿Qué es una antena isotrópica?
Es una antena ideal y teórica representada por un punto en el espacio que radia potencia de manera uniforme en todas las direcciones posibles.

### 4.11. ¿Cuál es la ventaja de una antena parabólica por reflexión?
Si una fuente de energía se sitúa en su foco, las ondas reflejadas siguen trayectorias paralelas al eje geométrico del paraboloide, produciendo teóricamente un haz paralelo que no presenta dispersión.

### 4.12. ¿Qué factores determinan la ganancia de una antena?
La ganancia, o nivel de direccionalidad, queda determinada por la frecuencia de la portadora y por el área efectiva de la antena, la cual depende de su geometría y de su tamaño físico.

### 4.13. ¿Cuál es la principal causa de la pérdida de señal en comunicaciones vía satélite?
La causa predominante es la pérdida en el espacio libre, ocasionada porque la señal radiada se dispersa y ocupa un área progresivamente mayor a medida que avanza la distancia.

### 4.14. ¿Qué es la refracción?
Es el fenómeno por el cual la velocidad de propagación de una onda electromagnética se altera al atravesar medios con distintas densidades.

### 4.15. ¿Qué diferencia hay entre difracción y dispersión?
La difracción es un fenómeno asociado al comportamiento físico de las ondas electromagnéticas cuando se encuentran o sortean obstáculos sólidos. La dispersión se refiere a los desvíos y cambios de dirección que sufren los rayos lumínicos al colisionar con impurezas o pequeñas partículas del medio.

## Ejercicios

### 4.1
Supóngase que unos datos se almacenan en disquetes de 1,4 Mbytes que pesan 30 g cada uno y que una compañía aérea transporta 10⁴ kg de disquetes a una velocidad de 1.000 km/h sobre una distancia de 5.000 km. ¿Cuál es la velocidad de transmisión en bits por segundo de este sistema?

**Respuesta**

Carga total en gramos:

$$10^4\ \text{kg} = 10^7\ \text{g}$$

Cantidad de disquetes transportados:

$$N = \frac{10^7\ \text{g}}{30\ \text{g/disquete}} \approx 333.333\ \text{disquetes}$$

Volumen total de datos, directo en bits:

$$B_{total} = 333.333 \times 11{,}2\times10^{6}\ \text{bits} \approx 3{,}7333\times10^{12}\ \text{bits}$$

Tiempo de vuelo:

$$t = \frac{5.000\ \text{km}}{1.000\ \text{km/h}} = 5\ \text{h} = 18.000\ \text{s}$$

Velocidad de transmisión:

$$R = \frac{3{,}7333\times10^{12}\ \text{bits}}{18.000\ \text{s}} \approx 207.407.407\ \text{bps} \approx \mathbf{207{,}41\ Mbps}$$

### 4.2
Sea una línea telefónica caracterizada por una pérdida de 20 dB. La potencia de la señal a la entrada es de 0,5 W y el nivel del ruido a la salida es de 4,5 μW. Calcule la relación señal/ruido para la línea en dB.

**Respuesta**

Potencia de entrada en dBW:

$$P_{in}(\text{dBW}) = 10\log_{10}(0{,}5) = -3{,}01\ \text{dBW}$$

Potencia de salida (resta directa de la pérdida en dB):

$$P_{out}(\text{dBW}) = -3{,}01 - 20 = -23{,}01\ \text{dBW} \;\;(\approx 5\ \text{mW})$$

Ruido en dBW:

$$P_{ruido}(\text{dBW}) = 10\log_{10}(4{,}5\times10^{-6}) = -53{,}47\ \text{dBW}$$

Relación señal/ruido:

$$SNR_{dB} = -23{,}01 - (-53{,}47) = \mathbf{30{,}46\ dB}$$

### 4.3
Dada una fuente de 100 W, determine la máxima longitud alcanzable en los siguientes medios de transmisión, si la potencia a recibir es 1 vatio:

a) Un par trenzado de 0,5 mm (24 gauges) a 300 kHz.
b) Un par trenzado de 0,5 mm (24 gauges) a 1 MHz.
c) Un cable coaxial de 9,5 mm a 1 MHz.
d) Un cable coaxial de 9,5 mm a 25 MHz.
e) Una fibra óptica trabajando a su frecuencia óptima.

**Respuesta**

Pérdida máxima admisible (única para los 5 casos):

$$L_{max} = 10\log_{10}\!\left(\frac{P_{tx}}{P_{rx}}\right) = 10\log_{10}\!\left(\frac{100}{1}\right) = 20\ \text{dB}$$

Distancia por medio:

$$d_{max} = \frac{L_{max}}{\alpha}$$

- a) Par trenzado 0,5 mm (24 AWG) @ 300 kHz — α ≈ 18 dB/km:
  $$d = \frac{20}{18} \approx \mathbf{1{,}11\ km}$$
- b) Par trenzado 0,5 mm (24 AWG) @ 1 MHz — α ≈ 29 dB/km:
  $$d = \frac{20}{29} \approx \mathbf{0{,}69\ km}$$
- c) Coaxial 9,5 mm @ 1 MHz — α ≈ 2,5 dB/km:
  $$d = \frac{20}{2{,}5} = \mathbf{8\ km}$$
- d) Coaxial 9,5 mm @ 25 MHz — α ≈ 11 dB/km:
  $$d = \frac{20}{11} \approx \mathbf{1{,}82\ km}$$
- e) Fibra óptica — α ≈ 0,2 a 0,5 dB/km:
  $$d = \frac{20}{0{,}5}\ \text{a}\ \frac{20}{0{,}2} \Rightarrow \mathbf{40\ km\ a\ 100\ km}$$

### 4.4
El cable coaxial es un sistema de transmisión con dos conductores. ¿Qué ventaja tiene conectar la malla exterior a tierra?

**Respuesta**

Al aterrizar la malla exterior, esta actúa como pantalla electromagnética: cualquier interferencia externa que la alcance (campos radiados, acoplamiento de cables vecinos) se deriva a tierra en lugar de inducirse sobre el conductor central que porta la señal. El resultado es una reducción sustancial del ruido acoplado y del crosstalk, junto con una referencia de potencial estable y protección eléctrica adicional para el sistema.

### 4.5
Demuestre que duplicando la frecuencia de transmisión o duplicando la distancia entre las antenas de transmisión y recepción, la potencia recibida se atenúa en 6 dB.

### 4.6
La profundidad en el océano a la que se detectan las señales electromagnéticas generadas desde aeronaves crece con la longitud de onda. Por tanto, los militares encontraron que usando longitudes de onda muy grandes, correspondientes a 30 Hz, podrían comunicarse con cualquier submarino alrededor del mundo. La longitud de las antenas es deseable que sea del orden de la mitad de la longitud de onda. ¿Cuál debería ser la longitud típica de las antenas para operar a esas frecuencias?

### 4.7
La potencia de la señal de voz está concentrada en torno a los 300 Hz. Las antenas para transmitir esta frecuencia deberían tener un tamaño enormemente grande. Esto hace que, para transmitir voz por radio, la señal deba enviarse modulando una señal de frecuencia superior (portadora) para la que la antena correspondiente requiera un tamaño menor.

a) ¿Cuál debe ser la longitud de una antena, equivalente a la mitad de la longitud de onda, para enviar una señal de 300 Hz?
b) Una posible alternativa es emplear algún esquema de modulación, de tal manera que la señal a transmitir tenga un ancho de banda estrecho, centrado en torno a la frecuencia portadora. Supóngase que quisiéramos una antena de 1 metro de longitud. ¿Qué frecuencia de portadora debería utilizarse?

### 4.8
Hay leyendas sobre gente que es capaz de recibir la señal de radio a través de los empastes de los dientes. Supóngase que tiene un empaste de 2,5 mm (0,0025 m) de largo que actuara a modo de antena, siendo igual su longitud a la mitad de la longitud de onda. ¿Qué frecuencia recibiría?

### 4.9
Suponga una comunicación entre dos satélites que cumple la ley del espacio libre. Suponga que la señal es muy débil. Se disponen de dos alternativas de diseño: una consiste en utilizar una frecuencia igual al doble de la frecuencia actual y la otra consiste en duplicar el área efectiva de las dos antenas. Manteniendo todos los demás parámetros inalterados, ¿se conseguirá la misma potencia recibida? o, en caso contrario, ¿cuál de las dos alternativas proporcionaría una potencia recibida superior? ¿Cuál sería el incremento de potencia recibida en el mejor de los casos?

### 4.10
En la transmisión de radio en el espacio libre, la potencia de la señal se reduce proporcionalmente al cuadrado de la distancia recorrida desde la fuente, mientras que en una transmisión en un cable, la atenuación es una cantidad fija en dB por kilómetro. En la siguiente tabla se muestra, en dB, la reducción relativa a una referencia dada para la transmisión en el espacio libre y en un cable uniforme. Rellene las celdas que faltan para completar la tabla.

| Longitud (km) | Radio (dB) | Cable (dB) |
|---|---|---|
| 1 | -6 | -3 |
| 2 | | |
| 4 | | |
| 8 | | |
| 16 | | |

### 4.11
En la Sección 4.2 se ha establecido que si una fuente de energía electromagnética se sitúa en el foco de un paraboloide, y que si el paraboloide tiene una superficie reflectante, entonces, la onda se reflejará en líneas paralelas al eje del paraboloide. Para demostrar esto considérese, por ejemplo, la parábola mostrada en la Figura 4.12. Sea P(x₁, y₁) un punto de la parábola y sea PF la línea que une P con el foco. Construya la línea L que pasa por P paralela al eje x y la recta M tangente a la parábola en P. El ángulo entre L y M es β y el ángulo entre PF y M es α. El ángulo α es el ángulo con el que el rayo que pasa por F incide en la parábola en P. Debido a que el ángulo de incidencia es igual al ángulo de reflexión, el rayo reflejado por P debe formar también el ángulo α. Por tanto, si se demuestra que α = β, se habrá demostrado que los rayos que se emitan desde F y sean reflejados por la parábola serán paralelos al eje x.

a) Demuestre primero que tan β = p/y₁. Sugerencia: recuérdese que la pendiente de una recta es igual a la tangente del ángulo que forma esa recta con el eje x positivo, y que la pendiente de una recta tangente a una curva en un punto dado es igual a la derivada de la curva en ese punto.
b) Ahora demuéstrese que tan α = p/y₁, lo que demostraría que α = β. Sugerencia: recuérdese la fórmula de la tangente de la diferencia entre dos ángulos α₁ y α₂: tan(α₂ − α₁) = (tan α₂ − tan α₁)/(1 + tan α₂ · tan α₁).

### 4.12
A menudo es más conveniente expresar las distancias en km en lugar de en m y las frecuencias en MHz en lugar de Hz. Rescriba la Ecuación (4.1) usando estas unidades.

### 4.13
Suponga que un transmisor emite 50 W de potencia.

a) Exprese la potencia transmitida en dBm y dBW.
b) Si la potencia del transmisor se aplica a una antena con ganancia unidad, usando una frecuencia de portadora de 900 MHz, ¿cuál es la potencia recibida, en dBm, en el espacio libre a una distancia de 100 m?
c) Repita el apartado (b) para una distancia de 10 km.
d) Repita (c) pero suponiendo una ganancia para la antena de recepción de 2.

### 4.14
Un transmisor de microondas tiene una salida de 0,1 W a 2 GHz. Suponga que este transmisor se utiliza en un sistema de comunicación de microondas en el que las antenas transmisora y receptora son parábolas, cada una con un diámetro igual a 1,2 m.

a) ¿Cuál es la ganancia de cada antena en decibelios?
b) Teniendo en cuenta la ganancia de la antena para la señal transmitida, ¿cuál es la potencia efectiva radiada?
c) Si la antena receptora se sitúa a 24 km de la antena transmisora en el espacio libre, determine la potencia de la señal a la salida de la antena receptora en dBm.

### 4.15
En la Sección 4.3 se afirma que si no hay obstáculos intermedios, la trayectoria visual óptica se puede expresar como d = 3,57√h, donde d es la distancia entre la antena y el horizonte, en kilómetros, y h es la altura de la antena, en metros. Teniendo en cuenta que el radio de la Tierra es 6.370 km, obtenga la expresión anterior. Sugerencia: supóngase que la antena es perpendicular a la superficie terrestre y nótese que la recta que une el punto más alto de la antena y el horizonte es la tangente a la superficie terrestre en el horizonte. Para visualizar más claramente el problema, dibuje un gráfico con la antena, la trayectoria visual y el radio de la Tierra.


### 4.16 
Calcule la altura de una antena de una emisora de TV que sea capaz de alcanzar clientes alejados a 80 km.

**Respuesta**

En transmisiones de radio y televisión, se debe usar la fórmula del horizonte de radio (línea de visión efectiva), la cual tiene en cuenta la curvatura de la Tierra y la refracción atmosférica: 
$$ d = 3,57\sqrt{Kh} $$

*   **$d$** (distancia máxima) = $80\text{ km}$.
*   **$K$** (factor de ajuste de refracción) = $4/3 \approx 1,333$ (valor estándar sugerido en el texto).
*   **$h$** = altura de la antena en metros (lo que buscamos).

1. Sustituimos los valores conocidos en la fórmula:
   $$ 80 = 3,57 \cdot \sqrt{1,333 \cdot h} $$
2. Pasamos el $3,57$ dividiendo para aislar la raíz cuadrada:
   $$ \sqrt{1,333 \cdot h} = \frac{80}{3,57} \approx 22,41 $$
3. Elevamos ambos lados al cuadrado para eliminar la raíz:
   $$ 1,333 \cdot h \approx (22,41)^2 \approx 502,16 $$
4. Despejamos la altura ($h$):
   $$ h = \frac{502,16}{1,333} \approx 376,7 $$

Para alcanzar una cobertura de 80 km, la antena de televisión debe tener una altura aproximada de **376,7 metros**.

### 4.17 
Suponga que un rayo de luz visible pasa desde la atmósfera hasta el agua formando un ángulo con el horizonte de 30°. ¿Cuál es el ángulo del rayo en el agua? Nota: en condiciones atmosféricas normales en la superficie terrestre, un valor razonable del índice de refracción es 1,0003. El valor típico del índice de refracción en el agua es 4 3.

**Respuesta**

Se utiliza la relación de los índices de refracción (conocida como la Ley de Snell), que establece que el cociente de los índices es inversamente proporcional al cociente de los senos de los ángulos respecto a la "normal" (la línea perpendicular a la superficie):
$$ n_1 \cdot \sin(\theta_1) = n_2 \cdot \sin(\theta_2) $$

*   **$n_1$** (índice de refracción de la atmósfera) = $1,0003$.
*   **$n_2$** (índice de refracción del agua) = $4/3 \approx 1,3333$.
*   **$\theta_1$** (ángulo de incidencia): El texto dice que el rayo forma 30° con el horizonte. Como el ángulo debe medirse desde la perpendicular (la normal), restamos: $90^\circ - 30^\circ = 60^\circ$.

1. Sustituimos los valores en la ecuación:
   $$ 1,0003 \cdot \sin(60^\circ) = 1,3333 \cdot \sin(\theta_2) $$
2. Calculamos el seno de 60° (que es $\approx 0,8660$) y multiplicamos:
   $$ 1,0003 \cdot 0,8660 = 1,3333 \cdot \sin(\theta_2) $$
   $$ 0,8663 = 1,3333 \cdot \sin(\theta_2) $$
3. Despejamos el $\sin(\theta_2)$:
   $$ \sin(\theta_2) = \frac{0,8663}{1,3333} \approx 0,6497 $$
4. Aplicamos la función arcoseno ($\arcsin$) para encontrar el ángulo:
   $$ \theta_2 = \arcsin(0,6497) \approx 40,52^\circ $$

El ángulo del rayo de luz dentro del agua es de **40,52°** medido con respecto a la línea vertical (la normal). *(Si se quisiera saber el ángulo respecto a la superficie del agua, sería $90^\circ - 40,52^\circ = 49,48^\circ$).*


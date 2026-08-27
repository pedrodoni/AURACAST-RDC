# Ejercicio 3

**Consigna:** Resumir brevemente y para ir pensando: ¿Cómo ayudan los sistemas de transmisión digital a detectar y corregir errores producidos por ruido en el canal? ¿Y a compensar cambios en la frecuencia?


**Detección y corrección de errores (Ruido)**

Básicamente, la idea para lidiar con el ruido es agregar información redundante a los datos originales. Esto se puede hacer de varias formas:

- **Detección:** Se le agrega un código de control a los datos antes de enviarlos (como un bit de paridad o un CRC). Cuando el receptor recibe el mensaje, hace el mismo cálculo. Si los resultados no dan igual, asume que hubo ruido y descarta el paquete.
- **Retransmisión (ARQ):** Si se detecta un error o se pierde un paquete, el receptor simplemente no manda el acuse de recibo (ACK). Al emisor se le vence un timer y vuelve a mandar ese bloque. Esto se usa un montón en protocolos como TCP.
- **Corrección hacia adelante (FEC):** A veces pedir que retransmitan algo es muy lento (por ejemplo en conexiones inalámbricas malas). Acá se usa más matemática (como códigos de Hamming) para mandar redundancia suficiente como para que el receptor no solo se dé cuenta de que hay un error, sino que pueda calcular qué bit falló y corregirlo ahí mismo sin pedir retransmisión.
- **Espectro expandido:** En conexiones inalámbricas se usan técnicas como el salto en frecuencia. La idea es desparramar la señal en un ancho de banda grande, así si hay una interferencia puntual en una frecuencia, solo afecta una parte muy chica de la señal y los datos se pueden recuperar.

**Compensación de cambios en la frecuencia (Sincronismo)**

Para que el transmisor y el receptor no se desfasen con los tiempos (mantener el sincronismo de reloj) y para aguantar variaciones, se suele jugar con la codificación de línea:

- **Códigos autosincronizados:** Formatos como Manchester te obligan a que haya un cambio de tensión en el medio de cada bit. Ese cambio constante le sirve al receptor como señal de "reloj", así que por más que haya una deriva en las frecuencias, se mantienen sincronizados.
- **Scrambling (Aleatorización):** El problema es que si mandás muchos ceros o muchos unos seguidos, la tensión queda constante y el receptor pierde el ritmo. Para evitarlo se usan técnicas como HDB3 o B8ZS que meten saltos de polaridad "falsos" a propósito para forzar a que haya transiciones de voltaje.
- **DMT (Multitono Discreto):** Se usa bastante en ADSL. Lo que hacen es agarrar el espectro y dividirlo en muchos subcanales. Si el módem nota que una frecuencia en particular está ruidosa o degradada, le baja la cantidad de datos que manda por ahí o directamente mueve el tráfico a otras frecuencias más limpias.


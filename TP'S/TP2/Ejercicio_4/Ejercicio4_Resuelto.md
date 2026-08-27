# Ejercicio 4 Resuelto

--
## Inciso a

**¿Qué significa sincronización en una comunicación digital? Diferencia entre sincronización de bits y sincronización de trama.**

### El problema de fondo

Los datos se transmiten bit a bit por el medio, y la temporización (velocidad de transmisión, duración y separación entre bits) debe ser común en el emisor y en el receptor. El receptor muestrea la señal una vez por cada bit recibido, idealmente en la parte central del intervalo, por lo que necesita conocer **el instante de llegada y la duración de cada bit**.

El problema aparece cuando el receptor delimita esas duraciones con su propio reloj y los dos relojes no están sincronizados con precisión. Stallings lo cuantifica: con una pérdida de sincronismo del 1 %, el primer muestreo se desplaza 0,01 veces la duración del bit, y **tras unas 50 muestras el desplazamiento acumulado llega a medio bit**, momento en el cual el muestreo se realiza en un instante incorrecto. Su conclusión es tajante:

*"Si se emite un número suficiente de bits, dicho error aparecerá irremediablemente si no se adoptan medidas para sincronizar al transmisor y al receptor."* 

En las diapos del teorico se define la sincronización, dentro de las *tareas claves en la comunicación*, como: *"Determinar inicio y término de la comunicación y duración de cada dato"*  Esa definición ya contiene los dos niveles del problema: **"duración de cada dato"** corresponde al nivel de bit, e **"inicio y término"** al nivel de trama.

### Sincronización de bits (o de reloj)

Responde a la pregunta: **¿cuándo muestreo? ¿dónde empieza y termina cada bit?** Es un problema de capa física, y las alternativas para resolverlo son la **línea de reloj independiente**, el **reloj embebido en la propia señal** (codificaciones autosincronizantes como Manchester) y la **resincronización carácter a carácter** de la transmisión asíncrona.

Cada una tiene su ventaja: la línea de reloj separada es la más simple y funciona bien a distancias cortas; el reloj embebido no necesita un canal extra y por eso escala a distancias largas — la Clase 02 muestra que es indispensable, ya que en NRZ *"15 ceros se ven muy parecidos a 16 ceros, a menos que usted cuente con un reloj muy exacto"*, y la resincronización por carácter evita el problema de raíz al no enviar cadenas largas ininterrumpidas, a costa de bits suplementarios.
En el fondo todas hacen lo mismo: **darle al receptor una referencia temporal periódica** para que su reloj no derive respecto del emisor. Cambia sólo de dónde sale esa referencia — de un cable aparte, de las transiciones de la propia señal, o de un reinicio en cada carácter.

### Sincronización de trama

Responde a una pregunta distinta: ya leo los bits correctamente, pero **¿dónde empieza y dónde termina el bloque? ¿qué bits son encabezado y cuáles son datos?**

Stallings la presenta de la siguiente manera:

*"En la transmisión síncrona se requiere además un nivel de sincronización adicional para que el receptor pueda determinar dónde está el comienzo y el final de cada bloque de datos. Para llevar a cabo esto, cada bloque comienza con un patrón de bits denominado preámbulo y, por lo general, termina con un patrón de bits denominado final."* 

La enumera como el **primer requisito** del control del enlace de datos:

*"**Sincronización de trama:** los datos se envían en bloques denominados tramas, cuyo principio y fin deben ser identificables."*


### Relación entre ambos niveles

Los dos niveles no son independientes: **una falla de sincronización de bits se propaga y rompe la sincronización de trama**. Stallings lo muestra al analizar el error de temporización en transmisión asíncrona:

> *"Un error como el anterior en realidad dará lugar a dos errores. Primero, el último bit muestreado será incorrecto, y segundo, la cuenta de bits puede estar desalineada. Si el bit 7 es un 1 y el bit 8 es un 0, el bit 8 se puede interpretar erróneamente como un bit de comienzo. Este tipo de error se denomina **error de delimitación de trama**."*

---

## Inciso b

**¿Qué es una trama (frame)? Diferencias entre encabezado (header), carga útil (payload) y tráiler (trailer).**

### Qué es una trama

Stallings define la trama como la unidad completa de información que circula por el enlace, no sólo los datos:

*"Al conjunto de bits, o unidad de información formada por los datos más el preámbulo más los bits de final junto con la información de control se le denomina **trama**. El formato en particular de la trama dependerá del procedimiento de control del enlace que se utilice."* 

Luego declara

*"Normalmente, la trama comienza con un preámbulo de 8 bits llamado delimitador (flag). El mismo delimitador se utiliza igualmente como indicador del final de la trama. (…) Este delimitador estará seguido por algunos campos de control, el campo de datos (de longitud variable para la mayoría de los protocolos), más campos de control y, por último, se repetirá el delimitador indicando el final de la trama."*

"**Datos y control sobre el mismo enlace:** por lo general, no se desea tener un canal de comunicaciones independiente para la información de control. En consecuencia, el receptor deberá ser capaz de diferenciar entre la información de control y los datos."*

### Header, payload y trailer

Los campos de delimitación, de dirección y de control, que preceden al campo de información, se denominan **cabecera/header**. Los campos FCS y de delimitación, que están a continuación del campo de datos, se denominan **cola/trailer**.

El **payload** o carga útil es el campo de datos propiamente dicho, es decir la información que la capa superior le entregó al enlace para que la transporte. Es la única parte de la trama que le interesa al destinatario final: el header y el trailer existen solamente para que ese payload llegue bien y se pueda ubicar dentro del flujo de bits. Su longitud suele ser variable, y por eso muchos protocolos necesitan un campo de longitud o un delimitador para saber dónde termina (como el campo LENGTH del ejercicio 5).

Una diferencia clave de diseño: el *trailer* contiene el **FCS (campo de comprobación de la trama)** y no la cabecera, porque el código detector de errores debe calcularse **sobre todos los bits que lo preceden** (cabecera + datos). Por eso se transmite al final, una vez que ya pasaron por el emisor todos los bits que protege.


---

## Inciso c

**¿Qué función puede cumplir un preámbulo antes de una trama? ¿Es necesariamente parte de la información que se quiere transmitir?**

### Función del preámbulo

El preámbulo es un **patrón de bits conocido de antemano** que se antepone a la trama y que cumple dos funciones:

**1. Permitir la sincronización de bits (recuperación del reloj).**
El receptor usa las transiciones del patrón para enganchar su reloj al del emisor *antes* de que empiecen a llegar los datos reales. Esto es indispensable porque, como vimos en el inciso a), en codificaciones como NRZ *"una larga sucesión de 0s o 1s deja la señal sin cambios"*  y el receptor perdería la referencia temporal.

El caso más explícito está en FDDI, donde el propio material de clase indica la finalidad: **`PA` = Preámbulo: 30 caracteres IDLE, para sincronismo**

**2. Marcar el comienzo de la trama (sincronización de trama).**
Stallings lo plantea al describir la transmisión síncrona:

*"cada bloque comienza con un patrón de bits denominado **preámbulo** y, por lo general, termina con un patrón de bits denominado **final**."*

Y en el formato típico de trama síncrona: *"Normalmente, la trama comienza con un preámbulo de 8 bits llamado delimitador (flag). (…) El receptor buscará la aparición del delimitador que determina el comienzo de la trama."* En HDLC ese patrón es `01111110`, y *"los receptores estarán continuamente intentando detectar la secuencia de delimitación para sincronizarse con el comienzo de la trama"*.

En la práctica, ambas funciones suelen repartirse en dos campos: un preámbulo largo para enganchar el reloj y un delimitador corto que marca exactamente dónde empieza la trama.

### ¿Es parte de la información que se quiere transmitir?

**No.** El preámbulo es **información de servicio (overhead), no datos del usuario**. Hay tres argumentos en las fuentes:

Stallings lo contabiliza como "bits suplementarios", separados de los datos.**


Si el preámbulo formara parte de la información a transmitir, no tendría sentido computarlo como *overhead* ni calcular qué porcentaje del enlace desperdicia.

**2. El mismo criterio aparece en la transmisión asíncrona.**
Sobre los bits de arranque y parada: *"de cada diez bits, dos no contendrán información ya que se dedicarán a la sincronización; por tanto, los bits suplementarios llegan a un 20 por ciento"* Cumplen la misma función que un preámbulo y son explícitamente bits que **no contienen información**.
Su contenido es un patrón fijo y predecible.


### Consecuencia práctica

Como el preámbulo no es información útil, existe un **compromiso de diseño**: es puro costo, pero es imprescindible. Se lo minimiza enviando bloques de datos grandes, de modo que el overhead se amortice — que es justamente el argumento de Stallings para preferir la transmisión síncrona sobre la asíncrona:

> *"Para los bloques de datos que sean suficientemente grandes, la transmisión síncrona es mucho más eficiente que la asíncrona."* 

---

## Inciso d
Estas son algunas de las formas mediante las cuales un protocolo puede determinar dónde termina una trama, entre otras. Tomamos las sujeridas que son las mas widely-used y agregamos una mas que nos pareció interesante extraida del libro "Redes de Computadoras" de Tanenbaum

### 1. Longitud fija
Todas las tramas tienen un tamaño idéntico y previamente acordado. El receptor cuenta bits/bytes y, al alcanzar ese número, sabe que la trama terminó.
- **Ventaja:** simple, sin campos extra.
- **Desventaja:** desperdicia ancho de banda si los datos no llenan el tamaño fijo, y un error de conteo desincroniza todas las tramas siguientes.

### 2. Campo que indica la longitud
La trama incluye en su encabezado un campo numérico que indica cuántos bytes tiene el cuerpo. El receptor lee ese valor y cuenta esa cantidad exacta.
- **Ventaja:** permite tramas de longitud variable.
- **Desventaja:** si ese campo se corrompe, se pierde la sincronización con las tramas siguientes.

### 3. Caracteres/secuencias delimitadoras
Se usan bytes o bits especiales (banderas) al inicio y fin de la trama, como el `01111110` de HDLC. Si esa secuencia aparece dentro de los datos, se usa **relleno (byte/bit stuffing)**: se inserta un bit/byte de escape que el receptor luego quita.
- **Ventaja:** longitud variable y fácil resincronización ante pérdida de una trama.
- **Desventaja:** requiere procesamiento extra para insertar y remover el relleno.

### 4. Violaciones de codificación de la capa física
Algunos esquemas de codificación de señal (por ejemplo, Manchester, usado en Ethernet clásico) representan cada bit válido con una combinación específica de niveles eléctricos. Existen combinaciones que nunca se usan para datos válidos (por ejemplo, alto-alto o bajo-bajo). El protocolo reserva esas combinaciones "inválidas" como marcadores de inicio y fin de trama.
- **Ventaja:** no hay riesgo de que el delimitador aparezca por casualidad en los datos, y no requiere relleno (stuffing).
- **Desventaja:** depende del esquema de codificación física utilizado, por lo que no es aplicable a cualquier medio de transmisión.

---

## Fuentes

- **Stallings, W.** — *Comunicaciones y Redes de Computadores*, 7ª ed., Pearson.
- **Tanenbaum** — *Redes de Computadoras*, 7ª ed., Pearson.

- **Clase 02 – Material Extra 1** 
- **Clase 02 – Material Extra 2** 
- **Clase 02 – Material Extra 2** 



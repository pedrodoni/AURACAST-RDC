# Tarea 2 

# CONSIGNA B

## 3.1. ¿En qué se diferencia un medio guiado de un medio no guiado?

En ambos casos la comunicación se realiza mediante ondas electromagnéticas, pero:

- **Medio guiado:** las ondas se transmiten confinadas a lo largo de un camino físico (por ejemplo, par trenzado, cable coaxial o fibra óptica).
- **Medio no guiado** también llamados inalámbrico: proporciona un medio para transmitir las ondas electromagnéticas sin confinarlas a un camino físico, por ejemplo propagándose a través del aire, el mar,etc

## 3.2. ¿Cuáles son las diferencias entre una señal electromagnética analógica y una digital?

- **Señal analógica:** es aquella donda la intensidad de la señal varía de forma suave y continua en el tiempo, sin saltos ni discontinuidades.
- **Señal digital:** es aquella donde la intensidad se mantiene constante durante un intervalo de tiempo determinado, y luego cambia a otro valor constante
 
## 3.3. ¿Cuáles son las tres características más importantes de una señal periódica?

Una onda seno genérica (señal periódica por excelencia) queda representada por tres parámetros:

1. **Amplitud de Pico (A):** valor de pico/máximo que alcanza la señal
2. **Frecuencia (f):** es la razon a la que la señal se repite
3. **Fase (φ):** es la medida de la posicion relativa de la señal dentro de un periodo de la misma

## 3.4. ¿Cuántos radianes hay en 360°?

360° equivalen a **2π radianes**.

## 3.5. ¿Cuál es la relación entre la longitud de onda y la frecuencia en una onda seno?

La longitud de onda (λ) es la distancia entre dos puntos de igual fase en dos ciclos consecutivos. Si la señal se propaga a una velocidad *v*, la relación con el periodo T y la frecuencia f es:

λ = v·T, o de forma equivalente, **λ·f = v**

Es decir, la longitud de onda y la frecuencia son inversamente proporcionales: a mayor frecuencia, menor longitud de onda.

## 3.6. ¿Cuál es la relación entre el espectro de una señal y su ancho de banda?

El **espectro** de una señal es el conjunto (rango) de frecuencias que la componen. El **ancho de banda** es la anchura de ese espectro, es decir, la diferencia entre la frecuencia más alta y la más baja que lo constituyen (ancho de banda absoluto). Muchas señales tienen un ancho de banda infinito, pero concentran la mayor parte de su energía en una banda de frecuencias relativamente estrecha; a esa banda se la denomina **ancho de banda efectivo**.

## 3.7. ¿Qué es la atenuación?

**Atenuación** es la pérdida (disminución) de energía o potencia que sufre una señal a medida que se propaga a través de un medio de transmisión, ya sea guiado (cable, fibra) o no guiado (aire, espacio).

## 3.8. Defina la capacidad de un canal.

La **capacidad del canal** es la velocidad máxima (en bits por segundo) a la que se pueden transmitir datos de forma confiable a través de un canal de comunicación, bajo unas condiciones dadas.

## 3.9. ¿Qué factores clave afectan a la capacidad de un canal?

Existen cuatro conceptos interrelacionados:

- **La velocidad de transmisión de los datos:** velocidad, en bps, a la que se transmiten los datos.
- **El ancho de banda:** ancho de banda de la señal transmitida, limitado por el transmisor y por la naturaleza del medio (Hz/segundos).
- **El ruido:** nivel medio de ruido presente en el camino de transmisión.
- **La tasa de errores:** frecuencia con la que ocurren errores (un 1 recibido como 0, o viceversa).

# CONSIGNA C

## Ejercicio 3.1

**a)** En una configuración multipunto, sólo un dispositivo puede trasmitir cada vez, ¿por qué?

**Respuesta a):**
Porque al estar en multipunto, comparten el mismo medio físico. Si transmiten al mismo tiempo, las señales chocan (generan interferencias) y la información llega corrupta al receptor.

**b)** Hay dos posibles aproximaciones que refuerzan la idea de que, en un momento dado, sólo un dispositivo puede transmitir. En un sistema centralizado, una estación es la responsable del control y podrá transmitir o decidir que lo haga cualquier otra. En el método descentralizado, las estaciones cooperan entre sí, estableciéndose una serie de turnos. ¿Qué ventajas y desventajas presentan ambas aproximaciones?

**Respuesta b): Centralizado vs. Descentralizado**
* **Centralizado (una estación controla todo)**:
  * **Ventaja**: Mucho orden, elimina las colisiones de raíz.
  * **Desventaja**: Si se rompe el equipo central, se paraliza toda la red.
* **Descentralizado (las estaciones cooperan entre sí)**:
  * **Ventaja**: Es robusto frente a fallos; si un equipo se apaga, la red sigue funcionando.
  * **Desventaja**: Es más complejo de implementar y requiere procesar "mensajes extra" solo para coordinarse.

## Ejercicio 3.2

Una señal tiene una frecuencia fundamental de 1000 Hz. ¿Cuál es su periodo?

**Respuesta:**
* **Fórmula:** $T = 1/f$
* **Cálculo:** $T = 1 / 1000 = 0,001 \text{ s}$ (o $1 \text{ ms}$)

## Ejercicio 3.3

Simplifique las siguientes expresiones:
**a)** `sen(2πft - π) + sen(2πft + π)`
**b)** `sen(2πft) + sen(2πft - π)`

**Respuesta:**
Para simplificar estas expresiones usamos la **regla trigonométrica clave:** $\sin(x \pm \pi) = -\sin(x)$

**a)** $\sin(2\pi ft-\pi) + \sin(2\pi ft+\pi)$
$$-\sin(2\pi ft) - \sin(2\pi ft) = -2\sin(2\pi ft)$$

**b)** $\sin(2\pi ft) + \sin(2\pi ft-\pi)$
$$\sin(2\pi ft) - \sin(2\pi ft) = 0$$

## Ejercicio 3.4

El sonido se puede modelar mediante funciones sinusoidales. Compare la frecuencia relativa y la longitud de onda de las notas musicales. Piense que la velocidad del sonido es igual a 330 m/s y que las frecuencias de una escala musical son:

| Nota           |  DO   |  RE   |  MI   |  FA   |  SOL  |  LA   |  SI   |  DO   |
| :------------- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Frecuencia** |  264  |  297  |  330  |  352  |  396  |  440  |  495  |  528  |

**Respuesta:**
* **Fórmula:** $\lambda = v/f$
* **Relación:** Son **inversamente proporcionales**; a mayor frecuencia, menor longitud de onda ($\lambda$).
* **Ejemplos representativos:**
  * **DO:** $\lambda = 330 / 264 = 1,25 \text{ m}$
  * **LA:** $\lambda = 330 / 440 = 0,75 \text{ m}$
  * **DO (octava alta):** $\lambda = 330 / 528 = 0,625 \text{ m}$

## Ejercicio 3.5

Si la curva trazada con una línea continua de la Figura 3.17 representa al `sen(2πt)`, ¿qué función corresponde a la línea discontinua? En otras palabras, la línea discontinua se puede expresar como `A sen(2πft + φ)`; ¿qué son A, f y φ?

**Respuesta:**
* **Amplitud ($A$):** $2$. El pico de la onda discontinua llega exactamente hasta la marca de 2,0.
* **Frecuencia ($f$):** $2\text{ Hz}$. Completa un ciclo entero en 0,5 segundos ($T=0,5$), por ende entran 2 ciclos completos en un segundo.
* **Fase ($\phi$):** $\pi$ radianes. La onda arranca en 0 pero baja hacia los negativos; esto equivale a una función seno invertida (un desfasaje exacto de $180^\circ$ o $\pi$).

**Resultado final:**
$$s(t) = 2\sin(4\pi t + \pi)$$

## Ejercicio 3.16
La según Nyquist para la capacidad del canal es:
$$C = 2B \log_2 M$$

Donde para este caso tenemos:
- $C = 9.600\text{ bps}$ (tasa de bits dato)
- $n = \log_2 M$ donde $M$ es la cantidad de bits por elemento de señal (palabra de bits, que tambien es dato)
- $B$ es el ancho de banda mínimo necesario

**a)** Para $n = 4\text{ bits}$ , $M = 2^4 = 16$:
  $$B = \frac{9.600\text{ bps}}{2 \times 4} = \frac{9.600}{8} = 1.200\text{ Hz}$$

**b)** Para $n = 8\text{ bits}$ , $M = 2^8 = 256$
  $$B = \frac{9.600\text{ bps}}{2 \times 8} = \frac{9.600}{16} = 600\text{ Hz}$$

## Ejercicio 3.17
La potencia del ruido térmico ($N$) depende exclusivamente de la constante de Boltzmann ($k$), la temperatura en Kelvin ($T$) y el ancho de banda ($B$). 
$$N = kTB$$


La potencia de transmisión de la señal ($1.000\text{ W}$) que da como dato no influye en la generación del ruido térmico del medio.

Ahora:
- $k = 1,38 \times 10^{-23}\text{ J/K}$ (constante de Boltzmann)
- $T = 50\text{ C} + 273,15 = 323,15\text{ K}$
- $B = 10\text{ kHz} = 10^4\text{ Hz}$
$$N = (1,38 \times 10^{-23}\text{ J/K}) \times (323,15\text{ K}) \times (10^4\text{ Hz}) \approx 4,4595 \times 10^{-17}\text{ W}$$
Expresado en decibelios-vatio ($\text{dBW}$) sería:
$$N_{\text{dBW}} = 10 \log_{10}(N) = 10 \log_{10}(4,4595 \times 10^{-17}) \approx -163,51\text{ dBW}$$

## Ejercicio 3.18
Considérense los trabajos de Shannon y Nyquist sobre la capacidad del canal. Cada uno de ellos estableció un límite superior para la razón de bits del canal basándose en dos aproximaciones diferentes. ¿Cómo se pueden relacionar ambas aproximaciones?

- **Nyquist (Canal sin ruido):** Establece que para un canal ideal sin ruido de ancho de banda $B$, la capacidad máxima es $C = 2B \log_2 M$. Esta fórmula sugiere que se podría lograr una tasa de transmisión infinitamente alta aumentando arbitrariamente la cantidad de niveles discretos de la señal ($M$).
- **Shannon (Canal con ruido):** Considera un canal real afectado por ruido térmico gaussiano y demuestra que la capacidad máxima libre de errores está limitada físicamente por la relación señal-ruido:
  $$C = B \log_2(1 + \text{SNR})$$
En un sistema real, no es posible aumentar $M$ de forma infinita porque los niveles de tensión se vuelven tan pequeños y cercanos entre sí que el ruido presente en el canal los confunde, generando errores de detección en el receptor.  
  Igualando ambas expresiones para hallar el número máximo teórico de niveles discriminables:
  $$2B \log_2 M = B \log_2(1 + \text{SNR}) \implies \log_2 M = \frac{1}{2} \log_2(1 + \text{SNR}) \implies M = \sqrt{1 + \text{SNR}}$$
  Por lo tanto, la formulación de Shannon impone el límite superior realista sobre la cantidad de niveles $M$ utilizables en la ecuación de Nyquist.

## Ejercicio 3.19
Sea un canal con una capacidad de 20 Mbps. El ancho de banda de dicho canal es 3 MHz. ¿Cuál es la relación señal-ruido admisible para conseguir la mencionada capacidad?

A partir de la ecuación de capacidad de Shannon:
$$C = B \log_2(1 + \text{SNR})$$

Despejando:
$$\frac{C}{B} = \log_2(1 + \text{SNR})$$
$$\frac{20\text{ Mbps}}{3\text{ MHz}} = \frac{20}{3} \approx 6,6667\text{ bps/Hz}$$

Elevando en base 2:
$$1 + \text{SNR} = 2^{20/3} \approx 101,5937$$
$$\text{SNR} \approx 100,5937$$

Expresando en decibelios ($\text{dB}$):
$$\text{SNR}_{\text{dB}} = 10 \log_{10}(100,5937) \approx 20,03\text{ dB}$$

## Ejercicio 3.20
La onda cuadrada de la Figura 3.7c, con $T=1ms$, se transmite a través de un filtro paso bajo ideal de ganancia unidad con frecuencia de corte a 8 kHz. 

**a)** Determine la potencia de la señal de salida. 

La representación en serie de Fourier de una onda cuadrada de amplitud $A = 1$ es:
$$s(t) = \frac{4}{\pi} \sum_{k\text{ impar}} \frac{\operatorname{sen}(2\pi k f_0 t)}{k}$$

Para $T = 1\text{ ms} = 10^{-3}\text{ s}$, la frecuencia fundamental es:
$$f_0 = \frac{1}{T} = 1.000\text{ Hz} = 1\text{ kHz}$$

Dado que el filtro es un paso bajo ideal con corte en $8\text{ kHz}$, dejará pasar los armónicos impares cuyas frecuencias sean menores a $8\text{ kHz}$, es decir:
- $k = 1 \implies f_1 = 1\text{ kHz}$
- $k = 3 \implies f_3 = 3\text{ kHz}$
- $k = 5 \implies f_5 = 5\text{ kHz}$
- $k = 7 \implies f_7 = 7\text{ kHz}$

La potencia promedio de cada componente sinusoidal con amplitud de pico $A_k = \frac{4}{\pi k}$ es:
$$P_k = \frac{A_k^2}{2} = \frac{1}{2}\left(\frac{4}{\pi k}\right)^2 = \frac{8}{\pi^2 k^2}$$

Sumando la potencia de los armónicos que pasan por el filtro:
$$S = \sum_{k \in \{1, 3, 5, 7\}} \frac{8}{\pi^2 k^2} = \frac{8}{\pi^2} \left(1 + \frac{1}{3^2} + \frac{1}{5^2} + \frac{1}{7^2}\right)$$
$$S = \frac{8}{\pi^2} \left(1 + \frac{1}{9} + \frac{1}{25} + \frac{1}{49}\right) = \frac{8}{\pi^2} (1 + 0,1111 + 0,0400 + 0,0204) = \frac{8}{\pi^2} (1,1715)$$
$$S \approx 0,9497\text{ W}$$

**b)** Suponiendo que a la entrada del filtro hay un ruido térmico con $N_0 = 0,1\ \mu\text{W/Hz}$, encuentre la relación señal-ruido en dB a la salida.

- Densidad espectral de potencia de ruido: $N_0 = 0,1\ \mu\text{W/Hz} = 10^{-7}\text{ W/Hz}$
- Ancho de banda del filtro: $B = 8\text{ kHz} = 8.000\text{ Hz}$

Potencia total de ruido a la salida:
$$N = N_0 B = (10^{-7}\text{ W/Hz}) \times 8.000\text{ Hz} = 8 \times 10^{-4}\text{ W} = 0,0008\text{ W}$$

Relación señal-ruido lineal:
$$\text{SNR} = \frac{S}{N} = \frac{0,9497\text{ W}}{0,0008\text{ W}} \approx 1.187,13$$

Expresada en decibelios:
$$\text{SNR}_{\text{dB}} = 10 \log_{10}(1.187,13) \approx 30,75\text{ dB}$$

# Consigna D: Modulación en AM en Python

## Código de Modulación AM (basado en el siguiente link)

https://programacionpython80889555.wordpress.com/

El siguiente código implementa la modulación AM utilizando la librería `numpy` para los cálculos trigonométricos y `matplotlib` para la generación de los gráficos.

```python
import numpy as np
import matplotlib.pyplot as plt

fp = 40000     # Frecuencia de la señal portadora
fm = 400       # Frecuencia de la señal moduladora

Ap = 5         # Amplitud de la portadora y moduladora

ka = 1         # ka = 1 (100% modulación), ka < 1 (submodulación), ka > 1 (sobremodulación)

t = np.linspace(0, 0.005, 1000)

moduladora = Ap * np.cos(2 * np.pi * fm * t)

portadora = Ap * np.cos(2 * np.pi * fp * t)

am = Ap * (1 + ka * np.cos(2 * np.pi * fm * t)) * np.cos(2 * np.pi * fp * t)

plt.figure(figsize=(10, 8))

# Gráfico 1: Señal Moduladora
plt.subplot(3, 1, 1)
plt.plot(t, moduladora, color='green')
plt.title('Señal Moduladora (Información)')
plt.xlabel('Tiempo (s)')
plt.ylabel('Amplitud')
plt.grid(True)

# Gráfico 2: Señal Portadora
plt.subplot(3, 1, 2)
plt.plot(t, portadora, color='red')
plt.title('Señal Portadora (Alta Frecuencia)')
plt.xlabel('Tiempo (s)')
plt.ylabel('Amplitud')
plt.grid(True)

# Gráfico 3: Señal Modulada AM
plt.subplot(3, 1, 3)
plt.plot(t, am, color='blue')
plt.title(f'Señal Modulada AM (Índice ka = {ka})')
plt.xlabel('Tiempo (s)')
plt.ylabel('Amplitud')
plt.grid(True)

plt.tight_layout()
plt.show()
```

## Pruebas y Análisis al Variar los Parámetros

A continuación, se detalla el análisis del comportamiento de la señal modulada en amplitud (AM) al realizar pruebas variando los parámetros de amplitud ($A_p$), frecuencias ($f_p$, $f_m$) y el índice de modulación ($k_a$).



### A. Variación del Índice de Modulación ($k_a$)

El índice de modulación $k_a$ (también denotado como $m$) define la relación entre la variación de la amplitud de la envolvente y la amplitud de la portadora pura. Es el parámetro crítico que determina la calidad y fidelidad de la transmisión.

1. **Submodulación ($k_a < 1$, ejemplo: $k_a = 0.5$):**

![](imagenes/ka05.png)

   * **Comportamiento:** La amplitud de la portadora varía de forma proporcional a la señal moduladora, pero en sus puntos mínimos la señal nunca llega a tocar el nivel cero.
   * **Conclusión:** Es una transmisión segura. La envolvente preserva la forma exacta del mensaje original, lo que permite demodularla fácilmente mediante receptores sencillos (como un detector de envolvente con diodo) sin introducir distorsión.

2. **Modulación Crítica o Completa ($k_a = 1.0$ o $100\%$):**

![](imagenes/ka1.png)

   * **Comportamiento:** Los valles de la envolvente llegan exactamente a tocar el eje de amplitud cero ($0\text{ V}$) en los mínimos de la señal moduladora.
   * **Conclusión:** Representa el estado óptimo de transmisión en AM estándar, ya que se aprovecha al máximo la potencia de la portadora para transportar la información útil sin llegar a distorsionar la señal.

3. **Sobremodulación ($k_a > 1$, ejemplo: $k_a = 1.5$):**

![](imagenes/ka15.png)

   * **Comportamiento:** En los valles del mensaje, la envolvente intenta tomar valores negativos, lo que causa un cruce por cero, una inversión de fase de $180^\circ$ en la portadora y la cancelación/recorte del pico inferior.
   * **Conclusión:** Genera **distorsión por sobremodulación** (recorte de envolvente) en el receptor. Además, produce componentes armónicas no deseadas en el espectro frecuencial, lo que causa interferencia en los canales de radio adyacentes (esparcimiento espectral).



### B. Variación de las Frecuencias ($f_p$ y $f_m$)

La relación entre la frecuencia de la portadora y la de la moduladora determina la definición y resolución con la que se transmite la información:

1. **Relación de Frecuencias ($f_p \gg f_m$):**

![](imagenes/relaciondefrequencia.png)

   * **Comportamiento:** Para una modulación AM efectiva, la frecuencia de la portadora ($f_p$) debe ser significativamente mayor que la frecuencia de la señal de información ($f_m$). 
   * **Observación:** En la prueba realizada con $f_p = 40000\text{ Hz}$ y $f_m = 400\text{ Hz}$, la portadora oscila 100 veces dentro de un solo período de la señal moduladora, dibujando de forma clara y nítida el contorno de la envolvente.

2. **Aumento de la Frecuencia Moduladora ($f_m$):**

![](imagenes/fm.png)

   * **Comportamiento:** Al aumentar $f_m$, los ciclos de la envolvente ocurren con mayor rapidez en el tiempo (disminuye su período $T_m = 1/f_m$).
   * **Efecto Espectral:** Incrementa el ancho de banda requerido para la transmisión, el cual en AM equivale a $BW = 2 \cdot f_m$.

3. **Disminución de la Frecuencia Portadora ($f_p$):**

![](imagenes/fp.png)

   * **Comportamiento:** Si $f_p$ se aproxima demasiado a $f_m$, la cantidad de ciclos de la portadora dentro de la envolvente es insuficiente.
   * **Conclusión:** La señal modulada pierde definición visual y técnica, dificultando la separación de las señales en el proceso de demodulación en el receptor.

---

### C. Variación de la Amplitud ($A_p$)

* **Comportamiento:** Incrementar o reducir el valor de $A_p$ escala proporcionalmente el nivel de tensión (voltaje) de todas las señales del sistema.
* **Impacto:** Si la potencia del emisor aumenta, la relación señal-ruido ($SNR$) en el receptor mejora, lo que permite cubrir mayor alcance geográfico, manteniendo constante la profundidad de modulación si $k_a$ no varía.

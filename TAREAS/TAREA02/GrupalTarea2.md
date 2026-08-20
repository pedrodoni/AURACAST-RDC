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

# Ejercicios

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

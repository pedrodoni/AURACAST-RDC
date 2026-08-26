# Ejercicio 2 Resuelto

## Inciso a

En la figura se ve ruido impulsivo, una interferencia bastante fuerte que aparece durante un ratito corto y se suma a la señal. La onda se mantiene normal antes y después, pero en el momento del impulso se deforma y eso puede provocar errores en los bits que se reciben.

## Inciso b

Afecta mucho a las transmisiones inalámbricas, como la telefonía celular y a las que usan cables de cobre (cable coaxial). Estos medios son bastante susceptibles a las interferencias electromagnéticas.

La fibra óptica es mucho más resistente al ruido impulsivo porque la información viaja mediante luz y no como una señal eléctrica. Igual, puede tener otros problemas como atenuación o dispersión.

## Inciso c

La **SNR** (*Signal-to-Noise Ratio*) es la relación entre la potencia de la señal y la potencia del ruido que es expresada en decibeles:

$$SNR_{dB} = 10\log_{10}\left(\frac{P_{señal}}{P_{ruido}}\right)$$

Una SNR alta significa que la señal se recibe con buena claridad. Una SNR baja indica que hay un montón de ruido, lo que aumenta la probabilidad de equivocarse al interpretar los bits.

El **BER** (*Bit Error Rate*) representa la cantidad de bits recibidos de manera incorrecta:

$$BER = \frac{\text{bits recibidos con error}}{\text{bits transmitidos}}$$

Si, los dos conceptos están relacionados. Cuando la SNR baja, normalmente el BER sube. Un impulso fuerte puede generar varios errores seguidos aunque el promedio de la SNR del canal parezca bueno.
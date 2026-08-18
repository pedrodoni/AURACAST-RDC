# Transmisión de señales
No es conveniente transmitir una señal escalonada de manera inalámbrica debido a factores físicos y del canal de transmisión.

Por el teorema de Fourier, una señal con transiciones abruptas requiere una cantidad infinita de frecuencias altas para mantener sus esquinas rectas. El canal inalámbrico tiene un ancho de banda limitado, lo que actúa como un filtro que recorta estas frecuencias. Como resultado, la señal se deforma y sus flancos se redondean, provocando que los pulsos se solapen (Interferencia Entre Símbolos).

Además, para que una antena irradie energía de manera eficiente, su tamaño físico debe ser proporcional a la longitud de onda de la señal. Como las señales escalonadas puras tienen componentes de muy baja frecuencia (es decir, longitudes de onda inmensas), intentar transmitirlas directamente requeriría construir antenas de kilómetros de longitud.

Transmitir en frecuencias bajas por el espacio libre genera una enorme atenuación y hace que la señal sea extremadamente vulnerable al ruido electromagnético del ambiente. El receptor sería incapaz de distinguir de forma confiable los niveles lógicos que representan los bits.

Por estos motivos, la información digital no se envía por el aire "cruda", sino que se recurre a la modulación, donde se alteran los parámetros (amplitud, frecuencia o fase) de una onda electromagnética (portadora) para que transporte los datos a través de antenas de tamaño práctico y en bandas de frecuencia reguladas.

## Inciso a
Se está representando PSK (Phase Shift Keying o Modulación por Desplazamiento de Fase).
Se puede observar que la amplitud y la frecuencia de la onda portadora se mantienen constantes en todo momento. Lo que cambia es la fase de la onda. Cuando el bit es "0", la onda inicia su ciclo "subiendo" (fase 0°). Cuando el bit es "1", la fase se invierte y la onda inicia su ciclo "bajando".

## Inciso b

![Inciso b](./TP1/Ejercicio_3/imagenes/ondas_psk_b.png)

## Inciso c

## Inciso d


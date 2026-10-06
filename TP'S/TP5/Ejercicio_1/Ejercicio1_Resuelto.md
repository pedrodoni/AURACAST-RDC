# ICMP y primer contacto con Wireshark (Primera Parte):

#### a) ¿Qué es ICMP y para qué se usa? ¿Transporta datos de aplicaciones como lo hacen TCP o UDP?

ICMP significa Internet Control Message Protocol (o Protocolo de Mensajes de Control de Internet) y se usa en la capa de red para poder enviar mensajes de errores, de diagnóstico o de información sobre en qué estado están las comunicaciones. Y a diferencia de los protocolos TCP y UDP, el ICMP no esta diseñado para transportar datos de aplicaciones de usuario, sino que es una herramienta de soporte solo para la infraestructura de la red.

#### b) ¿Qué relación tiene con IP? ¿Viaja dentro de IP, al lado de IP o debajo de IP? ¿Cómo sabe el receptor que el contenido de un paquete IP es ICMP?

El ICMP viaja adentro de un paquete IP. La carga que es útil del paquete del protocolo de internet versión 4 (o IPv4) directamente encapsula el mensaje ICMP. El receptor sabe el contenido del paquete gracias a que lee el campo "Protocolo" del encabezado IP, el cual tiene el contenido numérico específico que indica la presencia del ICMP.

#### c) ¿Qué hace ping? ¿Qué son un Echo Request y un Echo Reply? ¿Qué campos de ICMP permiten distinguirlos?

El ping es una herramienta que verifica la conectividad a nivel de red con otro equipo, enviando paquetes de prueba y midiendo el tiempo de respuesta.
El Echo Request es la solicitud de eco inicial que se envía al destino para comprobar si está activo, mientras que el Echo Reply hace lo mismo, solo que es la respuesta del eco que el equipo de destino que devuelve al emisor original confirmando la recepción.
Los campos que permiten distinguirlos son el campo de tipo mensaje de ICMP (icmp.type): un Echo Request utiliza el valor 8, mientras que un Echo Reply usa el valor 0.

#### d) ¿Qué información mínima contiene un mensaje ICMP de tipo Echo?

El encabezado tiene el tipo de mensaje, un código y una suma de comprobación (el checksum) para detectar errores en la transmisión. También tiene un identificador, un número de secuencia para que el emisor original pueda emparejar cada solicitud con su respuesta correspondiente y una sección de datos que va con el mensaje de ida y también en el de vuelta reflejado idénticamente.



# Segunda Parte

#### a) La MAC destino del Echo Request enviado a 8.8.8.8, ¿es la MAC de 8.8.8.8? ¿De que equipo es? Comparenla con la MAC destino del ping al gateway. ¿Que conclusion sacan sobre el alcance de una direccion MAC frente al de una direccion IP?

![Echo Request a 8.8.8.8](Imagenes/IMG-20261005-WA0004.jpg)

Al observar la captura del paquete **Echo (ping) request** dirigido a la IP de Internet (`8.8.8.8`), podemos ver en la capa **Ethernet II** que la dirección MAC de destino es `80:ae:3c:d6:e1:c0` (fabricante *TaicangT&WEl*).

**No, no es la MAC de 8.8.8.8.** Esta dirección MAC le pertenece al **Gateway (el router local)** de la red. Aunque el ping original (captura del terminal) haya arrojado pérdida de paquetes hacia el gateway, la MAC de destino a la que se envían los paquetes para salir a Internet siempre será la del router de casa.

**Conclusión:**
Esta diferencia nos permite entender claramente el propósito de cada tipo de dirección:
1. **Alcance de la Dirección MAC (Física / Capa de Enlace):** Su alcance es estrictamente **local**. Sirve únicamente para enviar la trama desde la computadora hasta el próximo salto inmediato en la misma subred (en este caso, el router).
2. **Alcance de la Dirección IP (Lógica / Capa de Red):** Tiene un alcance **extremo a extremo** (end-to-end). La IP de destino se mantiene intacta como `8.8.8.8` a lo largo de toda Internet para asegurar que los datos lleguen al destinatario final, mientras que las direcciones MAC irán cambiando en cada cable o salto entre routers por los que pase el paquete.


#### b) Comparar un Echo Request con su Echo Reply, listar qué campos cambian y cuáles se mantienen en las cabeceras Ethernet, IPv4 e ICMP, y justificar el porqué (especialmente por qué el ID y número de secuencia se mantienen para poder vincular la respuesta). 

![Echo Reply desde 8.8.8.8](Imagenes/IMG-20261005-WA0005.jpg)

Al comparar el **Echo Request** con su respectivo **Echo Reply**, observamos los siguientes cambios y similitudes en las cabeceras:

- **Ethernet II:** Las direcciones MAC de origen y destino se **invierten**. En el Request, el origen es la PC y el destino es el router. En el Reply, el origen es el router y el destino es la PC.
- **IPv4:** Las direcciones IP de origen y destino también se **invierten**. El Request va de la IP local (`192.168.1.4`) hacia `8.8.8.8`, y el Reply viene de `8.8.8.8` hacia `192.168.1.4`. Otros campos como el *TTL* o el *Checksum* también cambian.
- **ICMP:**
  - El campo **Type** cambia de `8` (Echo Request) a `0` (Echo Reply), indicando la naturaleza del mensaje.
  - El **Identifier** (ID) y el **Sequence Number** se **mantienen idénticos** en ambos paquetes. Esto es crucial porque permite que la computadora emisora sepa exactamente a qué pregunta específica corresponde la respuesta que está recibiendo (los vincula).


#### c) Encontrar el "payload" (datos) del ping, ver su tamaño, contenido, si es igual en la respuesta, y razonar por qué sería distinto entre un ping hecho desde Windows y uno desde Linux. 

![Payload del ping (ICMP Data)](Imagenes/IMG-20261005-WA0006.jpg)

Si revisamos la capa **ICMP** (como se ve en la captura), al final encontramos el campo de **Data** (Payload).
- El tamaño del payload es de **48 bytes** (como se observa al restarle las cabeceras a la longitud total del paquete de 98 bytes capturado en el cable).
- El contenido está compuesto por datos en hexadecimal (marcas de tiempo y otra información generada por el SO).
- El payload en el Echo Reply es **exactamente el mismo** que en el Echo Request (ya que debe hacer un "eco" exacto de lo enviado).

Si comparáramos un ping hecho desde Windows con uno de Linux, veríamos que **el tamaño y contenido son distintos**. Windows por defecto envía 32 bytes de payload consistentes en las letras del abecedario (abcd...), mientras que Linux envía 48 bytes que suelen incluir timestamps (marcas de tiempo) para que el comando `ping` pueda calcular la latencia con mayor precisión al recibir la respuesta.
```

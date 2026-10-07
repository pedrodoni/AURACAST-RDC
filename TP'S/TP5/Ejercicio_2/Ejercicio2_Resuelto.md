# Ejercicio 2: ARP - De una IP a una dirección MAC

#### a) ¿Qué problema resuelve ARP? ¿En qué capa lo ubicarían y por qué es discutible?

ARP (Address Resolution Protocol) resuelve el problema de asociar una dirección IP de la capa de red con la dirección MAC correspondiente de la capa de enlace para poder entregar las tramas dentro de una misma red local.
Su ubicación es discutible porque opera entre las capas 2 y 3: por un lado, se encapsula directamente dentro de tramas Ethernet (sin usar IP), lo que lo acerca a la capa de enlace; por otro lado, existe únicamente para dar soporte al direccionamiento IP, administrando información de la capa de red.

#### b) ¿Qué es un ARP Request y un ARP Reply? ¿A quién se envía cada uno?

Un ARP Request es la consulta que hace un equipo para preguntar a toda la red qué dirección MAC le pertenece a una IP determinada. Se envía a la dirección MAC de broadcast (ff:ff:ff:ff:ff:ff) para que lo reciban todos los hosts.
Un ARP Reply es la respuesta enviada únicamente por el equipo dueño de esa IP informando su MAC física. Se envía de forma unicast, directamente a la MAC del emisor que hizo la consulta.


#### c) ¿Qué es la caché ARP y por qué existe?

La caché ARP es una tabla en memoria donde el sistema operativo guarda temporalmente las relaciones entre direcciones IP y MAC ya resueltas. Existe para evitar enviar una solicitud por broadcast antes de cada paquete IP, reduciendo el tráfico innecesario en la red y mejorando la velocidad de comunicación.

#### d) Traten de responder con sus palabras: "Tengo la IP de una máquina de mi red local. ¿Cómo sé a qué dirección MAC debo enviarle la trama?"

Primero me fijo si ya tengo esa relación IP-MAC guardada en mi caché ARP. Si está, uso esa MAC directamente. Si no está, envío un ARP Request a la red por broadcast preguntando por esa IP; cuando la máquina destino me conteste con un ARP Reply unicast, guardo su MAC en mi caché y le envío la trama Ethernet.

#### e) Ver la caché ARP de su computadora y buscar la entrada del gateway:
![](images/image.png)
#### ¿La MAC asociada al gateway coincide con la MAC destino que vieron anteriormente?


Al ejecutar arp -a (en Windows) o ip neigh show (en Linux), la dirección MAC asociada a la IP del gateway coincide exactamente con la dirección MAC de destino que se observa en las tramas Ethernet al hacer ping a un servidor de Internet (como 8.8.8.8), ya que los paquetes hacia redes externas deben entregarse físicamente al router.

#### f) Generar tráfico ARP y capturarlo. Capturen en la interfaz Wi-Fi/Ethernet con el filtro arp. Como las entradas quedan guardadas en la caché, un ping a un equipo con el que ya hablaron puede no generar ningún ARP. [...]
#### Analizar un ARP Request y su ARP Reply. Para cada uno completar una tabla como la siguiente:


| Campo | ARP Request | ARP Reply |
| --- | --- | --- |
| MAC Destino | ff:ff:ff:ff:ff:ff | MAC del emisor |
| MAC origen | MAC del emisor | MAC del equipo que responde |
| Opcode | 1 | 2 |
| Sender MAC address | MAC del emisor | MAC del equipo que responde |
| Sender IP address | IP del emisor | IP del equipo que responde |
| Target MAC address | 00:00:00:00:00:00 | MAC del emisor original |
| Target IP address | IP a resolver | IP del emisor original|

---

# Segunda Parte

#### a) ¿Por qué el Request va a una dirección broadcast y el Reply no? ¿Qué valor tiene Target MAC address en el Request y por qué?

El ARP Request va a broadcast (ff:ff:ff:ff:ff:ff) porque el emisor conoce la IP de destino pero no sabe qué máquina de la red local tiene esa dirección ni cuál es su MAC, así que le pregunta a todos los hosts. En cambio, el Reply va por unicast porque el equipo que responde ya sabe exactamente la MAC del emisor original (vino en la cabecera y en el cuerpo del Request), así que le contesta directo a él sin generar tráfico innecesario en el resto de la red.

En el Request, el campo Target MAC address viene con el valor 00:00:00:00:00:00 porque es justamente la incógnita que se busca averiguar; se rellena en ceros como valor provisional mientras que a nivel Ethernet la trama se manda a broadcast.

#### b) En el encabezado Ethernet de la trama ARP, ¿qué valor tiene el campo Type? ¿Hay un encabezado IP? ¿Qué les dice eso sobre dónde "vive" ARP?

En el encabezado Ethernet el campo Type vale 0x0806. No hay ningún encabezado IP en el paquete; el mensaje ARP va metido directamente dentro de la carga útil de la trama Ethernet.

Esto demuestra que ARP trabaja justo en el límite entre las capas 2 y 3 (muchas veces llamada capa 2.5): a nivel de encapsulación vive en la capa de enlace (capa 2) porque se transporta directamente sobre Ethernet sin usar IP, pero funcionalmente existe para dar soporte a la capa de red (capa 3), ya que su único objetivo es asociar direcciones IP con direcciones MAC.

#### c) Con la Opción A (IP inexistente): ¿cuántos ARP Request aparecieron? ¿Hubo Reply? ¿Apareció algún ICMP Echo Request en la captura? Expliquen por qué.

Aparecieron 3 ARP Requests seguidos (los reintentos típicos que hace el sistema operativo por timeout) y no hubo ningún Reply porque nadie en la red tiene asignada esa IP.

En la captura de Wireshark no apareció ningún paquete ICMP Echo Request. Esto ocurre porque para poder mandar una trama por el medio físico, la capa de enlace necesita obligatoriamente conocer la dirección MAC de destino. Como ARP nunca obtuvo respuesta, la computadora no pudo armar la cabecera Ethernet y el paquete ICMP se descartó localmente en la máquina antes de poder salir al cable o al Wi-Fi, mostrando en la terminal el error de host inaccesible.

#### d) Volvieron a hacer ping al mismo destino un minuto después: ¿apareció ARP de nuevo? Revisen la caché ARP. ¿Qué ventaja tiene la caché y qué problema podría causar si una entrada quedara vieja?

Al repetir el ping un minuto después no apareció ningún paquete ARP en la captura, salieron directamente los paquetes ICMP. Al mirar la tabla con `arp -a` (o `ip neigh show`), la entrada de esa IP ya estaba guardada como dinámica en la caché de la máquina, por lo que el sistema usó esa MAC directamente sin consultar a la red.

La ventaja de la caché es que reduce la latencia al mandar datos y evita inundar la red local con broadcasts a cada rato. El problema de que una entrada quede vieja es que si un equipo cambia de MAC o de IP, la computadora le seguiría enviando tramas a una dirección física desactualizada, provocando pérdida de conectividad o abriendo la puerta a problemas de seguridad (como ataques de ARP spoofing). Por eso las entradas dinámicas vencen solas después de unos minutos.
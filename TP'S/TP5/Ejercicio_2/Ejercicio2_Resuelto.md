# 

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
# Ejercicio 3: TCP y UDP "a mano" con ncat (Segunda Parte)

Capturas realizadas en la interfaz de loopback, con los filtros `tcp.port == 12000` (TCP) y `udp.port == 12001` (UDP).

#### a) ¿Qué pasó en la red cuando ejecutaron el comando del cliente, antes de escribir el primer mensaje? Compárenlo con TCP.

**UDP:** no pasó nada. Al ejecutar `ncat -v -u 127.0.0.1 12001` el cliente solo crea el socket y deja anotado el destino en el sistema operativo; no se envía ningún paquete porque UDP no tiene conexión ni handshake. El primer paquete en la captura aparece recién cuando se escribe el primer mensaje y se presiona Enter. Por eso ncat muestra el mensaje de "conectado" sin que el servidor se entere de nada.

**TCP:** apenas se ejecuta `ncat -v 127.0.0.1 12000` ya aparecen tres segmentos, sin haber escrito nada: el *three-way handshake*.

1. Cliente → Servidor: `SYN`
2. Servidor → Cliente: `SYN, ACK`
3. Cliente → Servidor: `ACK`

Es decir que TCP necesita establecer la conexión antes de transportar datos, y UDP no.

#### b) ¿Cuántos datagramas generó cada mensaje? ¿Hay algo parecido a un ACK?

Cada mensaje generó **un solo datagrama UDP**, en el sentido en que se envió (cliente → servidor, o servidor → cliente). No hay nada parecido a un ACK: UDP no confirma la recepción, el emisor manda el datagrama y se olvida. Los datagramas que se ven en sentido contrario no son confirmaciones, son los mensajes que escribimos nosotros desde el otro lado, que transportan datos propios.

#### c) Comparen el encabezado UDP con el encabezado TCP de un segmento con datos: ¿qué campos tiene cada uno? ¿Cuántos bytes ocupa cada encabezado?

**UDP: 8 bytes**, con 4 campos de 2 bytes cada uno:

- Source Port (puerto origen)
- Destination Port (puerto destino)
- Length (longitud del encabezado más los datos)
- Checksum

**TCP: 20 bytes como mínimo** (hasta 60 si se agregan opciones). Campos:

- Source Port y Destination Port
- Sequence Number (32 bits)
- Acknowledgment Number (32 bits)
- Header Length (largo del encabezado)
- Flags (URG, ACK, PSH, RST, SYN, FIN, entre otros)
- Window Size (tamaño de ventana)
- Checksum
- Urgent Pointer
- Opciones (si las hay)

El de TCP es mucho más grande porque tiene que sostener todo lo que UDP no ofrece: los números de secuencia y de confirmación sirven para ordenar y confirmar los datos, los flags manejan la conexión (SYN, FIN, RST), y la ventana controla el flujo. UDP solo agrega los puertos, el largo y el checksum.

#### d) ¿Qué pasó en la red al cerrar el cliente con Ctrl+C? ¿Y en TCP?

**UDP:** no pasó nada en la red. Como no hay conexión, no hay nada que cerrar: el cliente simplemente deja de existir y el servidor nunca se entera de que se fue (queda esperando datagramas).

**TCP:** se produjo el cierre de la conexión (*connection termination*). El cliente envía un `FIN, ACK`, el servidor lo confirma con un `ACK`, y como ncat en modo servidor también termina cuando el otro extremo cierra, el servidor envía su propio `FIN, ACK`, que el cliente confirma con un último `ACK`. Son 4 segmentos, o 3 si el servidor junta su `ACK` y su `FIN` en uno solo. De esta forma los dos extremos saben que la conexión terminó y pueden liberar sus recursos.

#### e) Para enviar la misma frase, ¿cuántos paquetes necesitaron en total con TCP y cuántos con UDP? ¿Qué "compran" con los paquetes extra de TCP?

Para enviar una frase en un solo sentido:

| | TCP | UDP |
| --- | --- | --- |
| Establecer la conexión | 3 (SYN, SYN-ACK, ACK) | 0 |
| Enviar la frase | 1 (`PSH, ACK` con los datos) | 1 (el datagrama con los datos) |
| Confirmar la recepción | 1 (`ACK` del servidor) | 0 |
| Cerrar la conexión | 3 o 4 (FIN, ACK, FIN, ACK) | 0 |
| **Total** | **8 o 9** | **1** |

Con los paquetes extra, TCP "compra" **confiabilidad y control**:

- Que los dos extremos estén listos antes de empezar a transmitir.
- Entrega **confirmada** (los ACK), y **retransmisión** automática si algún segmento se pierde.
- Entrega de los datos **en orden y sin duplicados** (gracias a los números de secuencia).
- **Control de flujo y de congestión**, para no saturar al receptor ni a la red.
- Un cierre ordenado, donde ambos saben que no queda nada pendiente.

UDP no ofrece nada de esto: es más liviano y rápido, pero si el datagrama se pierde, llega repetido o desordenado, es la aplicación la que se tiene que encargar.

#### f) ¿Y si nadie escucha? (`ncat -v 127.0.0.1 12000` y `ncat -v -u 127.0.0.1 12001`, sin servidores corriendo)

**TCP a un puerto cerrado:** el cliente envía un `SYN` y el sistema operativo del destino, al ver que no hay ningún proceso escuchando en ese puerto, le contesta enseguida con un `RST, ACK`. Son solo 2 paquetes, la conexión nunca se establece y ncat muestra `Connection refused`. Es la forma que tiene TCP de avisar "acá no hay nadie".

**UDP a un puerto cerrado:** el cliente envía el datagrama y, como el puerto está cerrado, el sistema operativo del destino contesta con un mensaje **ICMP `Destination unreachable (Port unreachable)`** (tipo 3, código 3), que incluye el encabezado del datagrama original. Por eso hace falta el filtro `icmp` en este caso. UDP no tiene un mecanismo propio para avisar el error, así que lo hace la capa de red con ICMP (el protocolo del Ejercicio 1). El aviso llega después de que se envió el datagrama y es el sistema operativo quien se lo informa al programa, por lo que ncat puede mostrar el error recién al intentar enviar el mensaje siguiente.

En los dos casos el que está del otro lado "responde" aunque no haya nadie escuchando, y gracias a eso el cliente se entera enseguida de que no hay servicio. Si un firewall descartara los paquetes en silencio, no se vería ni el `RST` ni el ICMP, y el cliente solo notaría que no hay respuesta (timeout).

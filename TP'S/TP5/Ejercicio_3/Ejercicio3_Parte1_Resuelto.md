
# Ejercicio 3: TCP y UDP "a mano" con ncat (Primera Parte)

#### a) ¿Qué significa "establecer una conexión"? ¿Dónde "existe" una conexión TCP: en los cables, en los routers o en los extremos?

Establecer una conexión significa que los dos extremos se ponen de acuerdo antes de enviar datos, mediante (SYN, SYN-ACK, ACK). Así se aseguran de que el otro existe, negocian parámetros (como el tamaño máximo de segmento) y reservan recursos (buffers y una entrada en la tabla de conexiones).

La conexión existe solo en los extremos: cada sistema operativo guarda su propio estado de la conexión. Los cables solo transportan bits y los routers solo reenvían paquetes, así que no participan de la conexión.

#### b) ¿Qué es un puerto? ¿Qué identifica el par (IP, puerto)?

Un puerto es un número de 16 bits que identifica a una aplicación dentro de un equipo, para que el sistema operativo sepa a qué programa entregarle cada segmento o datagrama que llega.

El par (IP, puerto) se llama socket e identifica a un extremo de la comunicación: la IP identifica al equipo y el puerto, a la aplicación. Una conexión TCP se identifica con los dos sockets (IP y puerto de origen, IP y puerto de destino).

#### c) ¿Qué significa que un proceso esté "escuchando" en un puerto?

Significa que el proceso le pidió al sistema operativo que acepte conexiones entrantes en ese puerto (en el código, `bind()` y `listen()`). El puerto queda en estado LISTEN y, cuando llega un SYN, el sistema operativo responde con SYN-ACK y completa el handshake. Si nadie escucha, lo habitual es que responda con un RST y el cliente reciba "conexión rechazada".

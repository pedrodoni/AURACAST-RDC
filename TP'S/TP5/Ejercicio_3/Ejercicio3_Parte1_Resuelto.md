# Ejercicio 3: TCP y UDP "a mano" con ncat (Primera Parte)

#### a) ¿Qué significa "establecer una conexión"? ¿Dónde "existe" una conexión TCP: en los cables, en los routers o en los extremos?

Establecer una conexión TCP significa que los dos extremos se ponen de acuerdo, **antes de mandar datos**, en que van a comunicarse. Esto se hace con el *three-way handshake* (SYN, SYN-ACK, ACK), en el que cada lado:

- Avisa que quiere comunicarse y confirma que el otro también.
- Elige y sincroniza sus **números de secuencia iniciales**, que después se usan para ordenar los datos y confirmar su recepción.
- Intercambia parámetros de la conexión (tamaño máximo de segmento, tamaño de ventana, etc.).
- Reserva en el sistema operativo la memoria y el estado necesarios para la conexión (buffers, contadores, temporizadores).

La conexión **existe únicamente en los extremos**: es el estado que guardan el sistema operativo del cliente y el del servidor (cada uno tiene su propia "foto" de la conexión: en qué estado está, qué número de secuencia espera, qué datos faltan confirmar). No existe en los cables, que solo transportan bits, ni en los routers, que solo miran la IP de destino y reenvían cada paquete de forma independiente, sin saber que ese paquete pertenece a una conexión TCP. Por eso dos paquetes de la misma conexión podrían incluso viajar por caminos distintos.

(Una excepción son los dispositivos con estado como un NAT o un firewall, que sí recuerdan las conexiones que pasan por ellos, pero lo hacen para traducir o filtrar tráfico; no son parte de la conexión, que sigue siendo entre los dos extremos.)

#### b) ¿Qué es un puerto? ¿Qué identifica el par (IP, puerto)?

Un puerto es un número de **16 bits** (de 0 a 65535) que usa la capa de transporte (TCP o UDP) para saber **a qué programa o servicio, dentro de un equipo, pertenece cada segmento o datagrama**. La dirección IP solo identifica al equipo (más precisamente, a una de sus interfaces); como en un mismo equipo corren muchas aplicaciones a la vez (navegador, cliente de mail, un servidor, etc.), el puerto permite repartir el tráfico que llega entre ellas (multiplexación y demultiplexación).

El par **(IP, puerto)** identifica un **extremo de la comunicación**, es decir, a un proceso concreto de un equipo concreto (es lo que representa un socket). Una conexión TCP se identifica con los dos extremos juntos: **(IP origen, puerto origen, IP destino, puerto destino)**. Por eso un servidor puede atender a muchos clientes a la vez en el mismo puerto (por ejemplo el 12000): cada conexión se distingue por la IP y el puerto del cliente, que son distintos para cada una.

En este TP usamos el puerto 12000 para TCP y el 12001 para UDP; el puerto del cliente, en cambio, no lo elegimos nosotros: lo asigna el sistema operativo (un puerto efímero, por lo general alto).

#### c) ¿Qué significa que un proceso esté "escuchando" en un puerto?

Significa que el proceso le pidió al sistema operativo que **acepte conexiones entrantes en esa IP y ese puerto** (en código: `bind()` para asociar el socket a la IP y el puerto, y `listen()` para dejarlo en estado de escucha). Desde ese momento el puerto queda en estado **LISTEN**, y si llega un SYN dirigido a él, es el propio sistema operativo el que responde con el SYN-ACK y completa el handshake; el proceso después toma la conexión ya establecida con `accept()`.

Si en cambio **nadie escucha** en ese puerto, el sistema operativo rechaza el intento de conexión respondiendo con un segmento RST, y el cliente recibe un error de "conexión rechazada".

En UDP no hay conexión, así que no existe el estado de "escuchar" en ese sentido: el proceso asocia el socket al puerto y simplemente queda esperando a que lleguen datagramas.

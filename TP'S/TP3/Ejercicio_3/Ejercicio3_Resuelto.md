# Ejercicio 3

## a) ¿Qué problema(s) resuelve TCP que no resuelven la capa de Acceso a la Red ni la capa de Internet?

- La **capa de Acceso a la Red** (donde vive Ethernet) solo mueve tramas entre dispositivos conectados directamente en el mismo segmento local, usando direcciones MAC. No tiene noción de "extremo a extremo" ni de qué aplicación está usando esos datos.
- La **capa de Internet** (donde vive IP) rutea paquetes entre redes distintas usando direcciones IP, pero de forma **best-effort**: no garantiza entrega, ni orden, ni evita duplicados.

La **capa de Transporte**, mediante **TCP**, resuelve lo que las capas inferiores no cubren:

- **Confiabilidad**: garantiza que los datos lleguen, retransmitiendo si se pierden (usando ACKs).
- **Orden**: reordena los segmentos si llegan desordenados.
- **Control de flujo**: evita que el emisor sature al receptor (campo Ventana).
- **Control de congestión**: evita saturar la red, ajustando dinámicamente el ritmo de envío.
- **Multiplexación por puertos**: identifica qué aplicación específica del host está usando la red.
- **Orientación a conexión**: establece y cierra una conexión formal entre extremos (handshakes).

## b) Campos de la metadata TCP vs UDP

A diferencia de TCP, **UDP** es un protocolo de transporte mucho más simple: no orientado a conexión, sin garantías de entrega, orden ni control de flujo/congestión. Por eso su header es mínimo, mientras que el de TCP es mucho más rico en información de control.

| Campo | TCP | UDP | Para qué sirve |
|---|---|---|---|
| **Puerto de origen** | ✅ | ✅ | Identifica la aplicación/proceso emisor |
| **Puerto de destino** | ✅ | ✅ | Identifica la aplicación/proceso receptor |
| **Número de secuencia** | ✅ | ❌ | Numera los bytes enviados; permite reordenar y detectar pérdidas. UDP no lo tiene porque no garantiza orden |
| **Número de ACK** | ✅ | ❌ | Confirma qué bytes fueron recibidos. UDP no confirma nada |
| **Longitud de cabecera** | ✅ | ❌ (tiene "largo de segmento" en su lugar) | En TCP indica dónde termina el header variable (por las Opciones). UDP tiene header fijo, así que en vez de esto usa el largo total del segmento |
| **Flags (SYN, ACK, FIN, RST, PSH, URG)** | ✅ | ❌ | Controlan el estado de la conexión (abrir, cerrar, resetear, urgente). UDP no tiene conexión que gestionar |
| **Ventana (Window)** | ✅ | ❌ | Control de flujo: cuántos bytes puede recibir el receptor sin saturarse. UDP no controla flujo |
| **Checksum** | ✅ | ✅ | Verifica integridad del segmento. En UDP es el único mecanismo de control de errores, y encima es opcional en IPv4 |
| **Puntero urgente** | ✅ | ❌ | Indica dónde termina un dato marcado como urgente (poco usado hoy) |
| **Opciones** | ✅ | ❌ | Extensiones como MSS, Window Scaling, SACK, timestamps |
| **Largo de segmento** | (implícito en long. de cabecera + IP) | ✅ | Indica el tamaño total del segmento UDP (header + datos) |


El header de TCP es mucho más pesado (mínimo 20 bytes, puede crecer con Opciones) porque necesita sostener una **conexión confiable, ordenada y con control de flujo/congestión**. El header de UDP es fijo y liviano (8 bytes: puerto origen, puerto destino, largo, checksum) porque **no establece conexión ni garantiza nada**: simplemente envía el datagrama y confía en que la capa de Aplicación se encargue de cualquier confiabilidad adicional si la necesita (por eso UDP se usa en casos donde la velocidad importa más que la garantía de entrega, como streaming, VoIP o DNS).

## c) Three-way handshake y Four-way handshake

**Three-way handshake** (apertura de conexión — exclusivo de TCP, UDP no tiene equivalente):
 
Antes de ver los pasos, una aclaración clave: en cada segmento TCP hay **dos campos distintos** que se llaman "ACK", y no hay que confundirlos:
- El **flag ACK** (1 bit): solo indica si el campo de número de ACK es válido o no (`1` = sí, prestale atención; `0` = ignoralo).
- El **número de ACK** (32 bits): indica exactamente qué byte se está confirmando como recibido.
Con eso en claro, los pasos son:
 
1. **SYN**: el cliente envía un segmento con flag SYN=1 y un número de secuencia inicial (ISN_cliente), solicitando abrir la conexión. El flag ACK va en 0, porque todavía no hay nada que confirmar.
2. **SYN-ACK**: el servidor responde con **ambos flags activados a la vez** (SYN=1 y ACK=1) en el mismo segmento:
   - SYN=1 y Número de secuencia = ISN_servidor → "acá arranca mi propia numeración"
   - ACK=1 y Número de ACK = ISN_cliente + 1 → "confirmo que recibí tu ISN, espero el siguiente byte"
3. **ACK**: el cliente responde con flag ACK=1 y Número de ACK = ISN_servidor + 1, confirmando el ISN del servidor.

| Paso | Flags | Seq | Ack (número) |
|---|---|---|---|
| 1. Cliente → Servidor | SYN | ISN_cliente | — |
| 2. Servidor → Cliente | SYN, ACK | ISN_servidor | ISN_cliente + 1 |
| 3. Cliente → Servidor | ACK | ISN_cliente + 1 | ISN_servidor + 1 |
 
Con esto ambos extremos confirman que pueden enviar y recibir, y sincronizan sus números de secuencia iniciales. En Wireshark se ve en la columna Info como `[SYN]`, `[SYN, ACK]`, `[ACK]`.
 
**Four-way handshake** (cierre de conexión):
 
1. Un extremo (A) envía **FIN** (con flag ACK=1 también, confirmando lo último que recibió), indicando que no tiene más datos para enviar.
2. El otro extremo (B) responde con **ACK**, confirmando el FIN recibido (Número de ACK = Seq_FIN + 1).
3. Cuando B también termina de enviar sus datos, envía su propio **FIN**.
4. A responde con **ACK**, confirmando ese FIN.
Se necesitan 4 pasos (en vez de 3) porque la conexión TCP es **full-duplex**: cada extremo cierra su propio sentido de comunicación de forma independiente. En la práctica, el ACK del paso 2 y el FIN del paso 3 muchas veces viajan juntos en el mismo segmento (con ambos flags activados), quedando como 3 pasos visibles en la captura en vez de 4.
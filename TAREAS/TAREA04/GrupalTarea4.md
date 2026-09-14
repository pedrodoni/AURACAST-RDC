# Tarea 4

## CUESTIONARIO

### 15.1. ¿Qué diferencias hay entre los requisitos clave para las redes existentes en salas de computadores de aquellos necesarios para redes de área local de computadores personales?
Las redes de salas de computadores requieren velocidades de transmisión muy altas. Operan en distancias cortas y manejan transferencias continuas de grandes bloques de datos. Por otro lado, las LAN de computadores personales priorizan el bajo costo por conexión, abarcan distancias mayores (un edificio entero) y manejan tráfico en ráfagas más pequeñas de datos.

### 15.2. ¿Qué diferencias hay entre una red LAN de respaldo, una red SAN y una red LAN troncal?

LAN de respaldo: Conecta equipos de gran escala, como mainframes y grandes dispositivos de almacenamiento masivo.

Red SAN: Es una red separada y dedicada exclusivamente a conectar servidores con dispositivos de almacenamiento, liberando a la red principal de este tráfico pesado.

LAN troncal: Conecta y enlaza múltiples redes LAN de menor capacidad dentro de un edificio o campus para permitir la comunicación entre ellas.

### 15.3. ¿Qué es la topología de una red?
Es la disposición física o lógica de las estaciones y de los enlaces de transmisión que las conectan.

### 15.4. Enumere cuatro topologías comunes para redes LAN y describa brevemente su principio de funcionamiento.

Bus: Todas las estaciones se conectan a un único medio de transmisión lineal compartido. Una transmisión se propaga en ambas direcciones y es recibida por todas las demás estaciones.

Árbol: Es una generalización de la topología en bus. El medio se ramifica desde un punto raíz y las transmisiones se propagan por todas las ramas.

Anillo: Las estaciones se conectan formando un bucle cerrado. La señal pasa secuencialmente de un nodo al siguiente en una única dirección.

Estrella: Cada estación se conecta mediante un enlace dedicado a un nodo central, como un concentrador o conmutador, que distribuye el tráfico.

### 15.5. ¿Cuál es el propósito del comité IEEE 802?
Desarrollar estándares para arquitecturas, protocolos y tecnologías de Redes de Área Local (LAN) y Redes de Área Metropolitana (MAN), enfocándose específicamente en las capas física y de enlace de datos del modelo OSI.

### 15.6. ¿Por qué existen diferentes normativas para redes LAN?
Porque no existe un único diseño que sea óptimo para todos los escenarios. Las normativas varían para adaptarse a diferentes requerimientos de costo, velocidad, distancia, medios de transmisión y tolerancia a fallos de los usuarios.

### 15.7. Enumere y describa brevemente los servicios proporcionados por LLC.
El control de enlace lógico ofrece tres servicios a las capas superiores:

Servicio sin conexión no reconocido: Envía tramas sin establecer conexión previa y sin acuse de recibo. Es rápido pero no garantiza la entrega.

Servicio orientado a conexión: Establece un enlace lógico antes de transmitir, garantizando la entrega ordenada y sin errores mediante control de flujo y acuses de recibo.

Servicio sin conexión reconocido: Envía datagramas independientes pero requiere un acuse de recibo para cada uno, confirmando su entrega sin la sobrecarga de mantener una conexión activa.

### 15.8. Enumere y describa brevemente los modos de operación proporcionados por el protocolo LLC.

Operación de Tipo 1: Soporta el servicio sin conexión no reconocido.

Operación de Tipo 2: Utiliza mecanismos similares a HDLC para control de flujo y errores.

Operación de Tipo 3: Soporta el servicio sin conexión reconocido (permite enviar una trama y solicitar una confirmación inmediata).

### 15.9. Enumere algunas funciones básicas que se realicen en la capa MAC.
Ensamblado de datos en tramas, desensamblado de tramas, direccionamiento, detección de errores  y control de acceso al medio compartido.

### 15.10. ¿Qué funciones lleva a cabo un puente?
Un puente lee todas las tramas transmitidas en las LAN que conecta, filtra y reenvía las tramas basándose en las direcciones MAC de destino, aísla el tráfico local para que no cruce innecesariamente a otras LAN y permite la conexión de redes que operan con la misma arquitectura MAC.

### 15.11. ¿Qué es un árbol de expansión?
Es un mecanismo utilizado en redes con múltiples puentes o conmutadores para evitar bucles cerrados. Deshabilita lógicamente ciertos enlaces redundantes para crear una topología activa libre de bucles, garantizando que solo exista un camino de datos entre dos nodos cualesquiera.

### 15.12. ¿Qué diferencias existen entre un concentrador y un conmutador de capa 2?
Un concentrador opera en la capa física que actúa como un repetidor que recibe una señal por un puerto y la retransmite a todos los demás, por lo que solo un dispositivo puede transmitir a la vez. Un conmutador opera en la capa de enlace, lee la dirección MAC destino y reenvía la trama únicamente al puerto correspondiente, permitiendo múltiples transmisiones simultáneas sin colisiones.

### 15.13. ¿Cuál es la diferencia entre un conmutador de almacenamiento y envío y uno rápido?

Almacenamiento y envío: El conmutador recibe la trama completa en su memoria, verifica si hay errores y, si es válida, la reenvía al puerto destino.

Rápido: El conmutador lee solo la cabecera de la trama para obtener la dirección MAC de destino y comienza a reenviarla inmediatamente antes de recibir la trama completa. Reduce la latencia, pero puede propagar tramas corruptas.

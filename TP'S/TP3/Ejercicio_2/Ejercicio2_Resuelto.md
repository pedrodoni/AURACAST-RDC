# Ejercicio 2

## Inciso a

**Consigna:** Seleccionar una trama Ethernet e identificar las direcciones MAC de origen y destino. ¿A qué dispositivos creen que corresponden?

![](image/image.png)

MAC origen: 38:d5:7a:c4:89:05, MAC destino: 80:ae:3c:d6:e1:c0 
La direccion de Origen (source: 38:d5:7a:c4:89:05) pertenece a la tarjeta de red de mi laptop y la del Destino (Destination: 80:ae:3c:d6:e1:c0) pertenece a la interfaz del router local.

## Inciso b

**Consigna:** Dentro de la misma trama, identificar el paquete IP. ¿Cuáles son las direcciones IP de origen y destino? (no importa si son versión 4 o versión 6)

![](image/image1.png)

Podemos ver que las direcciones IP son, Source Address 192.168.1.4 que pertenece a una dirección IP privada asignada por el router y la Destination Address 162.159.130.234 es una IP pública de internet.

## Inciso C

**Consigna:**  Comparar las direcciones MAC y las direcciones IP encontradas ¿Representan lo mismo?

No representan lo mismo. El direccionamiento MAC opera en capa 2 (Enlace de datos), es único y estático para cada placa de red (hardware) y sirve para la entrega del paquete dentro del mismo segmento de red.

Mientras que el direccionamiento IP opera en capa 3 (Red), es un direccionamiento lógico que sirve para identificar nodos finales y permitir el enrutamiento extremo a extremo a través de múltiples redes distintas.



## Inciso D

**Consigna:**  Observar el campo EtherType. ¿Qué protocolo está encapsulado dentro de la trama analizada?

Al observar el campo EtherType, el protocolo que se encuentra encapsulado directamente en la trama es IPv4 y los datos transportados dentro de ese paquete IP utilizan el protocolo TCP.

# Ejercicio 1 Resuelto

## Inciso a
Se encarga de enviar datos de forma confiable a través del medio físico, agrupándolos en bloques llamados "tramas". Resuelve la comunicación local nodo a nodo (por ejemplo, de tu computadora al switch) dentro de una misma red.

## Inciso b
La MAC es una dirección física que viene grabada en tu placa de red y solo sirve para comunicarse a nivel local. La IP es una dirección lógica y global que permite "rutear" los datos a través de distintas redes (como internet) hasta llegar a su destino final.

## Inciso c
Es la unidad de datos que viaja por el cable en la capa de enlace. Sus campos son:
* **Preámbulo:** Sincroniza la señal.
* **MAC Destino:** A quién va la trama.
* **MAC Origen:** Quién la envía.
* **Tipo (EtherType):** Qué protocolo lleva adentro.
* **Datos:** La información útil (el paquete IP).
* **FCS:** Chequea si hubo errores.

## Inciso d
Simplemente mirando el campo Tipo de la trama. Ese dato le avisa a la placa si lo que trae en la carga útil es un paquete IPv4, un mensaje ARP, etc., para saber a qué proceso entregárselo.

# Ejercicio 1 Resuelto — Alcance de Redes y Virtualización

## Inciso a

> a) Investigar cómo se clasifican las redes según su alcance. Mencionar brevemente las características principales de cada una y colocar en cada cuadro de la Figura el acrónimo de red que corresponda.

**RTA:**

Las redes, según la distancia geográfica que cubren (alcance), se clasifican en:

<u>LAN (Local Area Network):</u></br>
Cubre un alcance geográfico muy limitado, como el interior de un edificio o una oficina. Su infraestructura está diseñada para altas velocidades de transmisión y suele utilizar medios económicos y fáciles de manipular.

<u>MAN (Metropolitan Area Network):</u></br>
Cubre una extensión intermedia que abarca una ciudad o un área metropolitana completa. Se utiliza para interconectar centrales telefónicas o redes locales dentro del casco urbano.

<u>WAN (Wide Area Network):</u></br>
Cubre grandes extensiones geográficas, conectando ciudades, países o incluso continentes. Debido a las enormes distancias, requiere tecnologías de alta capacidad y una infraestructura compleja basada en circuitos troncales de fibra óptica, enlaces de microondas terrestres y comunicaciones vía satélite.

---

## Inciso b

> b) ¿Qué es una vLAN? ¿Cómo se clasifican?

**RTA:**
Una VLAN (Virtual Local Area Network) es una tecnología que permite segmentar de manera lógica una red de computadoras en la capa de enlace de datos, haciendo que un grupo de dispositivos se comporte como si estuviera conectado al mismo cable, independientemente de su ubicación física.

Se clasifican principalmente según el método utilizado para asignar los dispositivos:

**Por puertos**: Los puertos del conmutador se asignan estáticamente a una VLAN específica.
**Por direcciones MAC**: La asignación es dinámica y se basa en la dirección de hardware única del dispositivo.
**Por protocolo o capa de red**: Los paquetes se clasifican según el protocolo o la dirección IP que utilicen.

---

## Inciso c

> c) Investigar y resumir el protocolo IEEE 802.1Q. ¿Cómo se relaciona con las VLAN?

**RTA:**
IEEE 802.1Q es el estándar que permite el funcionamiento de las VLAN en redes Ethernet.

Se relaciona con las VLAN mediante:

<u>Etiquetado (VLAN Tagging):</u></br>
Modifica la trama Ethernet agregando una etiqueta de 4 bytes que incluye el VLAN ID. Esto sirve para identificar a qué red virtual pertenece cada paquete de datos.

<u>Enlaces Troncales:</u></br>
Permite que el tráfico de múltiples VLANs viaje a través de un único enlace físico entre switches, manteniendo los datos separados y organizados.

<u>Dominios de Difusión:</u></br>
Asegura que los paquetes de broadcast se queden solo dentro de su respectiva VLAN, actuando como si fueran redes físicas independientes.

<u>Transparencia:</u></br>
Todo este proceso ocurre a nivel de hardware y es invisible para los dispositivos finales (PCs, servidores), los cuales se comunican de forma normal.

---

## Inciso d

> d) En el contexto de los dos ítems anteriores ¿Qué es el Tagging?

**RTA:**
El Tagging (etiquetado) es el proceso de insertar una marca de identificación (VLAN ID) dentro de la trama Ethernet para indicar a qué red virtual pertenece.

Puntos clave:

**Identificación:** Permite a los switches saber de qué VLAN es cada paquete cuando viaja por un enlace compartido. </br>
**Separación:** Evita que el tráfico de diferentes VLANs se mezcle.</br>
**Transparencia:** El switch añade la etiqueta al enviar los datos y la retira al entregarlos al dispositivo final, por lo que las PCs no notan su existencia.</br>

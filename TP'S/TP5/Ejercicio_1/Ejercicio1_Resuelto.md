# ICMP y primer contacto con Wireshark:

#### a) ¿Qué es ICMP y para qué se usa? ¿Transporta datos de aplicaciones como lo hacen TCP o UDP?

ICMP significa Internet Control Message Protocol (o Protocolo de Mensajes de Control de Internet) y se usa en la capa de red para poder enviar mensajes de errores, de diagnóstico o de información sobre en qué estado están las comunicaciones. Y a diferencia de los protocolos TCP y UDP, el ICMP no esta diseñado para transportar datos de aplicaciones de usuario, sino que es una herramienta de soporte solo para la infraestructura de la red.

#### b) ¿Qué relación tiene con IP? ¿Viaja dentro de IP, al lado de IP o debajo de IP? ¿Cómo sabe el receptor que el contenido de un paquete IP es ICMP?

El ICMP viaja adentro de un paquete IP. La carga que es útil del paquete del protocolo de internet versión 4 (o IPv4) directamente encapsula el mensaje ICMP. El receptor sabe el contenido del paquete gracias a que lee el campo "Protocolo" del encabezado IP, el cual tiene el contenido numérico específico que indica la presencia del ICMP.

#### c) ¿Qué hace ping? ¿Qué son un Echo Request y un Echo Reply? ¿Qué campos de ICMP permiten distinguirlos?

El ping es una herramienta que verifica la conectividad a nivel de red con otro equipo, enviando paquetes de prueba y midiendo el tiempo de respuesta.
El Echo Request es la solicitud de eco inicial que se envía al destino para comprobar si está activo, mientras que el Echo Reply hace lo mismo, solo que es la respuesta del eco que el equipo de destino que devuelve al emisor original confirmando la recepción.
Los campos que permiten distinguirlos son el campo de tipo mensaje de ICMP (icmp.type): un Echo Request utiliza el valor 8, mientras que un Echo Reply usa el valor 0.

#### d) ¿Qué información mínima contiene un mensaje ICMP de tipo Echo?

El encabezado tiene el tipo de mensaje, un código y una suma de comprobación (el checksum) para detectar errores en la transmisión. También tiene un identificador, un número de secuencia para que el emisor original pueda emparejar cada solicitud con su respuesta correspondiente y una sección de datos que va con el mensaje de ida y también en el de vuelta reflejado idénticamente.

# Ejercicio 3 Resuelto — LAN a bordo de una aeronave (VLAN + NAT + ACL)

> Utilizando lo aprendido sobre VLAN, e investigando la configuración de NAT y ACLs, simular el despliegue de una red LAN a bordo de una aeronave con tres segmentos:
>
> - Clase Turista: acceso solo a un sistema de entretenimiento (server local)
> - Clase Business: acceso a sistema de entretenimiento e internet
> - Administración: acceso total
>
> | VLAN | Nombre         | Red IP          | Gateway       | Acceso                    |
> |------|----------------|-----------------|---------------|---------------------------|
> | 10   | Turista        | 10.10.10.0/24   | 10.10.10.1    | Solo servidor             |
> | 20   | Business       | 10.10.20.0/24   | 10.10.20.1    | Servidor + Internet       |
> | 99   | Administración | 10.10.99.0/24   | 10.10.99.1    | Acceso total              |
> | —    | Enlace ISP     | 200.0.0.0/30    | 200.0.0.1–.2  | —                         |

## Diagrama de red

_Topología armada en Packet Tracer._

## Configuración

_Configuración del router (subinterfaces VLAN, DHCP, NAT, ACLs) y de los switches (VLANs, trunk, puertos de acceso)._

## Pruebas

> | Prueba                            | Desde        | Hacia            | Resultado esperado |
> |------------------------------------|--------------|------------------|---------------------|
> | Ping al servidor de entretenimiento | PC Turista   | 10.10.99.10      | Responde            |
> | Acceso HTTP a servidor local        | PC Turista   | http://10.10.99.10 | Carga la página   |
> | Ping a Internet                     | PC Turista   | —                | Bloqueado           |
> | Acceso HTTP a servidor local        | PC Business  | http://10.10.99.10 | Carga             |
> | Ping a Internet (ej: 8.8.8.8)       | PC Business  | —                | Funciona            |
> | Ping entre Admin y todos            | Admin PC     | —                | Todos               |

## Conclusiones

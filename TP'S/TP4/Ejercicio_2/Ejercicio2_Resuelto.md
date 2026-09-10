# Ejercicio 2 Resuelto — Topología VLAN en Packet Tracer

> Topología: SW-1 y SW-2 interconectados, cada uno con su PC (PC-A en SW-1, PC-B en SW-2).
>
> | Device | Interface | IP Address    | Subnet Mask   | Default Gateway |
> |--------|-----------|---------------|---------------|------------------|
> | SW-1   | VLAN 1    | 192.168.1.11  | 255.255.255.0 | N/A              |
> | SW-2   | VLAN 1    | 192.168.1.12  | 255.255.255.0 | N/A              |
> | PC-A   | NIC       | 192.168.10.3  | 255.255.255.0 | 192.168.10.1     |
> | PC-B   | NIC       | 192.168.10.4  | 255.255.255.0 | 192.168.10.1     |

## Inciso a

> a) Desde cada computadora, ingresar a la terminal y configurar los switch. Nombrar a los mismos sw1 y sw2 respectivamente.

## Inciso b

> b) Asignar contraseñas privilegiadas, de consola y vty.

## Inciso c

> c) Encriptar las contraseñas (Ayuda: utilizar `service password-encryption`).

## Inciso d

> d) Configurar las redes VLAN para ambos switch según la tabla de direcciones provista.

## Inciso e

> e) Desconectar todas las interfaces que no estén siendo utilizadas (Ayuda: podés ver las interfaces utilizando `show ip interface brief`).

## Inciso f

> f) Guardar la configuración (`write memory`).

## Inciso g

> g) Testear comunicación usando pings entre las computadoras.

## Inciso h

> h) Crear VLANs en ambos switches (Laboratorio, Bar, Management).

## Inciso i

> i) Utilizar `show vlan brief` para visualizar la lista de VLANs en alguno de los switch. ¿Cuál es la VLAN utilizada por defecto?. Colocar el output en el informe.

## Inciso j

> j) Asignar la PC-A a la VLAN Laboratorio.

## Inciso k

> k) Desde la VLAN 1, remover la ip de Management y configurarla para funcionar en la VLAN 99 (que configuramos como Management).

## Inciso l

> l) Verificar el estado de la VLAN utilizando `show vlan brief` y el estado de las interfaces utilizando `show ip interface brief`. Colocar los output en el informe e interpretar.

## Inciso m

> m) Asignar la PC-B a la VLAN Laboratorio en el sw2. Repetir el inciso k) pero para el sw2.

## Inciso n

> n) Verificar la conectividad entre PC-A y PC-B utilizando pings. Verificar conectividad entre sw1 y sw2 utilizando pings. Interpretar los resultados.

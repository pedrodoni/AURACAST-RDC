# Ejercicio 5 Resuelto
Nuestro grupo se llama Auracast, por lo que buscaremos el paquete cuyo header comience con 'aurac' en ascii.

**Bytes crudos en hex:** ` 61 75 72 61 63 02 01 74`

### Desglose

| Campo   | Tamaño  | Hex              | Valor decodificado |
|---------|---------|------------------|---------------------|
| GROUP   | 5 bytes | `61 75 72 61 63` | `aurac`             |
| SEQ     | 1 byte  | `02`             | 2                   |
| LENGTH  | 1 byte  | `01`             | 1                   |
| PAYLOAD | 1 byte  | `74`             | `t`                 |

Luego, buscamos los nombres de los otros grupos, tomado solo los primeros 5 caracteres en lower case. Pudimos eliminando el ruido de caracteres (TPREDESDECOMPUTADORAAASSSSS) que se coloco entre algunas secuencias obtener lo siguiente:


| SEQ | Grupo | GROUP (5B) | Length | Payload | Hex crudo |
|----|---|---|---|---|---|
| 1  | #hiddenSSID | `#hidd` | 2 | `ht` | `236869646401026874` |
| 2  | Auracast | `aurac` | 1 | `t`  | `6175726163020174` |
| 3  | BitBros | `bitbr` | 1 | `p`  | `6269746272030170` |
| 4  | ClickByte | `click` | 2 | `s:` | `636c69636b0402733a` |
| 5  | Death Net | `death` | 1 | `/`  | `646561746805012f` |
| 6  | Easter egg del profe(?) | `ferne` | 1 | `/`  | `6665726e6506012f` |
| 8  | Grupo | `grupo` | 1 | `w`  | `677275706f080177` |
| 9  | LA LA LAN | `la la` | 2 | `w.` | `6c61206c610902772e` |
| 11 | Los Red(ondos) | `los r` | 2 | `ut` | `6c6f7320720b027574` |
| 12 | Los simuLANdores | `los s` | 2 | `ub` | `6c6f7320730c027562` |
| 13 | LAN-gustia | `lan-g` | 2 | `yo` | `6c616e2d670d02796f` |
| 13 | Los_CondIPcionales | `los_c` | 2 | `e.` | `6c6f735f630d02652e` |
| 14 | Los-Tios-Networks | `los-t` | 1 | `c`  | `6c6f732d740e0163` |
| 15 | Lost-Pointer-2.4 | `lost-` | 1 | `o`  | `6c6f73742d0f016f` |
| 16 | MACac OS | `macac` | 3 | `m/s`| `6d6163616310036d2f73` |
| 17 | MiLANesas | `milan` | 2 | `ho` | `6d696c616e1102686f` |
| 18 | NetRunners | `netru` | 1 | `r`  | `6e65747275120172` |
| 19 | NetRunners | `netru` | 2 | `ts` | `6e6574727513027473` |
| 20 | PandaBasic | `panda` | 1 | `/`  | `70616e646114012f` |
| 21 | Ping Floyd | `ping ` | 2 | `db` | `70696e672015026462` |
| 22 | Red Hot Chilli Packets | `red h` | 2 | `be` | `726564206816026265` |
| 23 | TCPanico | `tcpan` | 2 | `_l` | `746370616e17025f6c` |
| 24 | WAN-direction | `wan-d` | 2 | `n6` | `77616e2d6418026e36` |
| 25 | WireGuardians | `wireg` | 3 | `Lnw`| `776972656719034c6e77` |
| 32 | Group Not Found :( | `group` | 1 | `w`  | `67726f7570200177` |

**Notas:**
- Único grupo sin trama en este archivo: **Bitless**.
- Colisión real en **SEQ=13** entre dos grupos distintos (LAN-gustia y Los_CondIPcionales) — a confirmar con la cátedra.
- SEQ 7, 10, 26-31 no tienen trama detectada, ni sacando el relleno.
- El paquete de **Auracast** (grupo propio) es el de SEQ=2, payload `t`.
- Mensaje reconstruido concatenando por SEQ (con huecos en 7 y 10): `https://ww.utube.com/shorts/dbbe_ln6Lnww`

**Encontramos lo siguiente:**
- El grupo Bitless no parece tener ninguna trama válida.
- Entre dos grupos distintos (LAN-gustia y Los_CondIPcionales) hay una colisión ya que poseen el mismo numero de secuencia(13). 
- Las seq 7, 10, 26-31 no parecen tener una trama válida.
- El mensaje reconstruido concatenando por SEQ (con huecos en 7 y 10): `https://ww.utube.com/shorts/dbbe_ln6Lnww` tomando uno de los 2 frames con secuencia 13. Por intuición nos parece un enlace de youtube. Así que manipulando un poco los  frames recuperados:
    - El frame cuya secuencia es 32 cuyo payload es 'w' suponemos que ocupa en realidad el lugar 7, ya que si le restamos 7 a 32 nos da 25 (nro total de frames del mensaje). 
    - Luego uno de los paquetes con secuencia repetida (13) cuyo payload es 'yo' suponemos que ocupa en realidad el lugar 10 
    - Asi finalmente formamos el enlace `https://www.youtube.com/shorts/dbbe_ln6Lnw` que si es un enlace válido pero llegamos tarde para el chocolate.
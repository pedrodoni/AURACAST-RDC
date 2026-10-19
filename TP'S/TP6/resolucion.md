# Trabajo Práctico N°6 — Resolución

---

## Parte 1: Taller de armado y verificación de cables Cat5/Cat5e bajo estándar T568A/B

### Objetivos

- Tomar contacto con elementos de la capa física y ganar experiencia en armado y verificación de conexiones de red.

---

### Consignas

#### 1) Investigar los pasos para crimpar un cable bajo la norma T568A/B DERECHO (No cruzado).

**Esquema de colores (Norma T568B):**

1. Blanco Naranja
2. Naranja
3. Blanco Verde
4. Azul
5. Blanco Azul
6. Verde
7. Blanco Marrón
8. Marrón

*(Desarrollo de los pasos de crimpado aquí...)*

---

#### 2) Construir 1 (un) cable por grupo (1 - 1.5 m aprox., tipo DERECHO).

- **Cable construido (UTP Cat5e / Norma T568B - Directo):**

![Cable armado - Extremo 1](imagenes/cable_amarillo_1.jpg)
![Cable armado - Extremo 2](imagenes/cable_amarillo_2.jpg)

---

#### 3) VERIFICAR la buena construcción de un cable (intercambio con otro grupo).

##### a) Inspección visual para la calidad constructiva

*(Observamos que el cable de nuestro compañeros tiene desperfectos conforme a nylon del cable UTP, el cual esta atravesado sobre los conductores. Esto puede traer falsos contactos, perdida de velocidad, interferencias o perdida de paquetes. Pero algo positivo que tiene es el recubrimiento, el cual el nuestro no posee)*

![Cable intercambiado - Conector vista 1](imagenes/cable_intercambiado_negro_1.jpg)
![Cable intercambiado - Conector vista 2](imagenes/cable_intercambiado_negro_2.jpg)

##### b) Verificación eléctrica utilizando un tester para cables Ethernet

*(Resultado de la prueba del tester en la carpeta videos)*

---

#### 4) Documentación de intercambio y proceso técnico

- **Grupo con el que se intercambió: PingFloyd**
- **Evidencias fotográficas / videos:**
  - Fotos del cable propio y del cable intercambiado incorporadas en `imagenes/`.
  - Videos del testeo de continuidad disponibles en `videos/`.

---

## Parte 2: Equipamiento físico, verificación y utilización de equipos de red y generación de tráfico

### Objetivos

- Tomar contacto con equipamiento físico, reconocer su anatomía, paneles, indicadores, interfaces y funciones.
- Utilizar un switch empresarial (configurable).
- Análisis de tráfico UDP.
- Asignación de direcciones.

---

### Opcional

#### 1) Características principales del switch Cisco Catalyst 2950 Series

*(Documentación a partir del datasheet oficial...)*

#### 2) Checklists de procedimientos

##### a) Conectar PC al puerto de consola del switch Cisco a 9600 baudios con PuTTY

*(Paso a paso, parámetros de conexión serie y verificación...)*

##### b) Acceder a las opciones de administración del switch y levantar varias interfaces

*(Comandos de configuración Cisco IOS...)*

---

### Levantar y testear una LAN

#### 1) Configuración MANUAL de la interfaz de red

- **a) Dirección IPv4:**
- **b) Máscara de subred:**
- **c) Default gateway:**
- **d) Justificación de las direcciones elegidas:**

---

#### 2) Conexión y prueba de conectividad mediante Switch

- Conexión al switch Cisco mediante los cables armados en la Parte 1.
- Prueba de conectividad con `ping` hacia la PC del otro grupo:
  *(Capturas de pantalla / terminal...)*

---

#### 3) Establecimiento de receptor y emisor UDP con `ncat`

- Receptor:
  ```bash
  ncat -u -l 5000
  ```
- Emisor:
  ```bash
  ncat -u <IP_DESTINO> 5000
  ```

*(Documentación y capturas del intercambio de mensajes...)*

---

#### 4) Captura de paquetes UDP con Wireshark

*(Capturas e inspección de tramas UDP...)*

---

#### 5) Preguntas teóricas y análisis

##### a) ¿Se observa algún procedimiento de establecimiento de conexión antes de enviar los datos?

*(Respuesta...)*

##### b) ¿Existe algún mecanismo de confirmación de recepción equivalente a los ACK de TCP?

*(Respuesta...)*

##### c) ¿Qué ocurre si se envían mensajes mientras el receptor UDP no está ejecutándose?

*(Respuesta...)*

##### d) ¿UDP garantiza que los mensajes lleguen en el mismo orden en que fueron enviados?

*(Respuesta...)*

##### e) ¿Qué aplicaciones reales utilizan UDP y por qué?

*(Respuesta...)*

---

### Desarrollar un pequeño servidor

#### 1) Iniciar servidor HTTP con Python

```bash
python3 -m http.server 8000
```

*(Archivos preparados en el directorio: TXT, PDF e imagen...)*

---

#### 2) Acceso y descarga mediante navegador web

*(Acceso desde la segunda PC a `http://<IP>:8000` y descarga...)*

---

#### 3) Transferencia utilizando `curl` desde la terminal

```bash
curl -O http://<IP>:8000/<archivo>
```

*(Captura de la ejecución y transferencia...)*

---

#### 4) Captura del tráfico con Wireshark

- **¿De qué tipo de tráfico se trata?**
  *(Análisis de las capas TCP, HTTP y paquetes capturados...)*

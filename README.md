# 🛰️ Misiones de Comunicación Galáctica – Base Rebelde

## 🧩 Misión 1: Reconexión en la Base Eco (Hoth) – Direccionamiento IP y Subredes

**Red asignada:** `172.16.0.0/24`

### Requisitos de hosts por departamento:

| Departamento         | Hosts requeridos | Potencia de 2 | Hosts útiles |
|----------------------|------------------|----------------|---------------|
| Comando central      | 50               | 2⁶ = 64        | 62            |
| Defensa perimetral   | 30               | 2⁵ = 32        | 30            |
| Centro médico        | 20               | 2⁵ = 32        | 30            |
| Hangar y taller      | 14               | 2⁴ = 16        | 14            |
| Enlace Troncal Antena| 6                | 2³ = 8         | 6             |

### Asignación de subredes:

| Departamento         | Subred              | Máscara CIDR         | Hosts útiles | Rango de Hosts                   |
|----------------------|---------------------|-----------------------|--------------|----------------------------------|
| Comando Central      | 172.16.0.0/26       | 255.255.255.192       | 62           | 172.16.0.1 – 172.16.0.62         |
| Defensa Perimetral   | 172.16.0.64/27      | 255.255.255.224       | 30           | 172.16.0.65 – 172.16.0.94        |
| Centro Médico        | 172.16.0.96/27      | 255.255.255.224       | 30           | 172.16.0.97 – 172.16.0.126       |
| Hangar y Taller      | 172.16.0.128/28     | 255.255.255.240       | 14           | 172.16.0.129 – 172.16.0.142      |
| Enlace Troncal Antena| 172.16.0.144/29     | 255.255.255.248       | 6            | 172.16.0.145 – 172.16.0.150      |

---

## 🧙‍♂️ Misión 2: Sabiduría de Yoda – Algoritmos de Enrutamiento y Rutas

### Comparación entre enrutamiento estático y dinámico:

| Característica        | Enrutamiento Estático         | Enrutamiento Dinámico              |
|------------------------|-------------------------------|-------------------------------------|
| Configuración         | Manual                        | Automática (protocolos)             |
| Adaptabilidad         | Fija                          | Se adapta a cambios                 |
| Uso de recursos       | Bajo                          | Alto (más CPU, RAM, ancho de banda)|
| Escalabilidad         | Limitada                      | Alta (ideal para redes grandes)     |
| Seguridad/control     | Muy alto                      | Requiere protección adicional       |
| Ejemplo de uso        | Redes pequeñas                | Redes medianas/grandes              |

### Ejemplo de protocolo dinámico: RIP (Routing Information Protocol)

- Protocolo de vector de distancia.
- Anuncia rutas periódicamente a vecinos.
- Métrica: número de saltos (máx. 15).
- Fácil de configurar, pero lento y propenso a bucles.

### Diferencia: Vector de distancia vs Estado de enlace

| Tipo de Protocolo      | Vector de Distancia (RIP)        | Estado de Enlace (OSPF)              |
|------------------------|----------------------------------|--------------------------------------|
| Funcionamiento         | Envía tabla completa a vecinos   | Envía estado de enlaces a todos      |
| Convergencia           | Lenta                            | Rápida                               |
| Visión de red          | Parcial                          | Global                               |
| Escalabilidad          | Limitada                         | Alta                                 |
| Complejidad            | Baja                             | Alta                                 |

---

## 🌐 Misión 3: Los Nombres del Holonet – DNS y Resolución de Nombres

### ¿Qué es DNS?

El **DNS (Domain Name System)** es como la guía telefónica galáctica: traduce nombres de dominio como `holonet.rebelion.org` en direcciones IP como `192.0.2.15`.

### Proceso de resolución:

1. **Caché local**: Si ya fue resuelto antes, se reutiliza.
2. **Servidor DNS configurado**: Revisa su caché.
3. **Resolución en cascada**:
   - Servidor raíz `.`
   - Servidor TLD `.org`
   - Servidor autoritativo `rebelion.org`
4. **Respuesta al cliente** con la IP correspondiente.

### Registro DNS común: **Registro A**

- Asocia nombre de dominio con dirección IPv4.

### ¿Qué pasa si el servidor DNS falla?

- No se puede navegar ni acceder por nombre.
- Aunque la red física funcione, parecerá “caída”.

---

## ⚠️ Misión 4: “¡Es una trampa… de protocolos!” – TCP vs UDP

### Comparación TCP vs UDP:

| Característica      | TCP                                | UDP                                 |
|---------------------|-------------------------------------|--------------------------------------|
| Orientación         | Conexión orientada                 | No orientada a conexión              |
| Fiabilidad          | Alta (entrega completa y ordenada) | Baja (no garantiza entrega)          |
| Control de flujo    | Sí                                 | No                                   |
| Retransmisión       | Sí (retransmite paquetes perdidos) | No (paquetes perdidos se descartan)  |
| Rendimiento         | Más lento                          | Más rápido                           |
| Encabezado          | 20-60 bytes                        | 8 bytes                              |
| Ejemplos de uso     | Transferencias, web, banca         | Video en tiempo real, juegos, VoIP   |

### ¿Por qué TCP es confiable?

- Establece conexión antes de enviar datos.
- Garantiza orden y entrega mediante confirmaciones.
- Retransmite si hay errores.
- Ideal para datos críticos como **planos de la Estrella de la Muerte**.

### ¿Por qué UDP es rápido?

- Envía sin establecer conexión.
- No espera confirmación.
- Útil en situaciones donde **la velocidad es prioridad** como en:
  - Transmisiones desde X-Wings
  - Coordenadas de combate en tiempo real

---

## 🔐 Misión 5: Comunicación Segura o Lado Oscuro – Criptografía y Seguridad de la Red

### ¿Qué es la criptografía?

Arte de cifrar mensajes para que **solo el receptor autorizado** pueda leerlos, incluso si son interceptados.

---

### 🔒 Cifrado Simétrico (una sola clave compartida)

- **Funcionamiento:**  
  Leia y Luke comparten una clave como `"ElSolDeEndor42"`  
  Leia cifra → Luke descifra con la misma clave.

- **Ventajas:**
  - Muy rápido
  - Ideal para grandes volúmenes de datos

- **Ejemplo rebelde:**  
  Comunicación segura entre Leia y Luke.

---

### 🛡️ Cifrado Asimétrico (clave pública/privada)

- **Funcionamiento:**
  - Cada nodo tiene una clave pública y una privada.
  - Mon Mothma cifra con la **clave pública** del destinatario.
  - Solo el receptor con su **clave privada** puede descifrar.

- **Ventajas:**
  - No requiere compartir claves antes.
  - Escalable y seguro para nuevos aliados.

- **Ejemplo rebelde:**  
  Primer contacto con un planeta nuevo, sin clave previa.

---



¡Que la red te acompañe! 🚀

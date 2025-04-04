# Parte 1

## Ejercicio 1

### **Modelo OSI (7 Capas)**

| Capa | Nombre           | Función Principal                                      | Ejemplos/Protocolos                  |
|------|------------------|-------------------------------------------------------|---------------------------------------|
| 7    | Aplicación       | Interfaz para aplicaciones de usuario                 | HTTP, FTP, SMTP, DNS                 |
| 6    | Presentación     | Traducción/formato de datos (encriptación, compresión)| SSL/TLS, JPEG, ASCII                  |
| 5    | Sesión           | Gestión de conexiones/diálogos entre dispositivos     | NetBIOS, RPC                          |
| 4    | Transporte       | Control de flujo, confiabilidad y segmentación de datos | TCP (confiable), UDP (no confiable)  |
| 3    | Red              | Enrutamiento de datos entre redes (direcciones IP)    | IP, ICMP, Routers                     |
| 2    | Enlace de Datos  | Control de acceso al medio físico y direccionamiento MAC | Ethernet, Switches                  |
| 1    | Física           | Transmisión de bits crudos a través de medios físicos | Cables, Wi-Fi, Hubs, Señales eléctricas/ópticas |

---

### **Relación entre OSI y TCP/IP**
- **Modelo OSI**:  
  Teórico (7 capas): Física, Enlace de Datos, Red, Transporte, Sesión, Presentación, Aplicación.  

- **Modelo TCP/IP**:  
  Práctico (4 capas agrupadas):  
  | **Capa TCP/IP**   | **Capas OSI equivalentes**       |
  |--------------------|-----------------------------------|
  | Acceso a la Red    | Física + Enlace de Datos         |
  | Internet           | Red                              |
  | Transporte         | Transporte                       |
  | Aplicación         | Sesión + Presentación + Aplicación |

**Concepto común**: Ambos usan **encapsulación** para estructurar la comunicación.

---

## Ejercicio 2

### **TCP (Mensajero Confiable)**  
**Ventajas**:  
- ✅ Alta fiabilidad: Ideal para transferencias críticas (páginas web, correos, archivos).  
- ✅ Garantiza entrega ordenada y sin errores.  

**Desventajas**:  
- ❌ Mayor latencia por control de errores y confirmaciones.  
- ❌ Sobrecarga de tráfico por establecimiento de conexión.  

---

### **UDP (Mensajero Veloz)**  
**Ventajas**:  
- ✅ Baja latencia: Ideal para tiempo real (streaming, VoIP).  
- ✅ Eficiente en ancho de banda.  

**Desventajas**:  
- ❌ Sin garantía de entrega o orden de paquetes.  
- ❌ Riesgo de datos incompletos/desordenados.  

---

### **Resumen de Uso**  
| **Protocolo** | **Mejor para**                  | **No recomendado para**             |
|---------------|----------------------------------|--------------------------------------|
| TCP           | Datos críticos, precisión       | Aplicaciones sensibles a la latencia |
| UDP           | Transmisiones rápidas en tiempo real | Datos que requieren integridad absoluta |

## Ejercicio 3

#### ** Explicación Detallada del Cálculo**  

**Paso 1: Determinar los bits necesarios para 4 subredes**  
- Para dividir la red en **4 subredes**, se necesitan: log2(4) = 2 bits prestados de la parte de host.
- La máscara original de la red base (`192.168.50.0`) es **/24** (`255.255.255.0`).  
- Al prestar **2 bits**, la nueva máscara será:  24 (original) + 2 (prestados) = /26 (255.255.255.192).

- 
**Paso 2: Calcular las direcciones por subred**  
- Con una máscara **/26**, los **6 bits restantes** (32 bits totales - 26 bits para red = 6 bits para hosts) se usan para hosts: 2^6 = 64 direcciones por subred (totales).
-  Direcciones **utilizables** (se restan dirección de red y broadcast): 64 - 2 = 62 hosts por subred.


**Paso 3: Identificar las subredes resultantes**  
Las 4 subredes serían:  

| **Subred**         | **Rango Utilizable**                 |
|---------------------|--------------------------------------|
| `192.168.50.0/26`    | `192.168.50.1` – `192.168.50.62`    |
| `192.168.50.64/26`   | `192.168.50.65` – `192.168.50.126`  |
| `192.168.50.128/26`  | `192.168.50.129` – `192.168.50.190` |
| `192.168.50.192/26`  | `192.168.50.193` – `192.168.50.254` |


| **Aspecto**               | **Detalle**                              |
|---------------------------|------------------------------------------|
| Máscara de subred         | `255.255.255.192` (/26)                  |
| Direcciones totales/subred| 64                                       |
| Direcciones útiles/subred | 62                                       |
| Subredes creadas          | 4                                        |

**Conclusión**:  
Los antiguos lograron dividir su "reino digital" en 4 subredes iguales usando una máscara `/26`, asignando **62 direcciones útiles** a cada gremio.

### **EJERCICIO 4 **

#### **1. Concepto Moderno Representado por el Tótem**  
El tótem con flechas simboliza una **tabla de enrutamiento** (*routing table*), un componente clave en los routers actuales que decide cómo dirigir el tráfico de datos hacia su destino.

---

#### **2. ¿Qué es una Tabla de Enrutamiento?**  
- **Definición**: Es una base de datos almacenada en un router que contiene las "rutas" hacia diferentes redes. Cada entrada indica:  
  - **Destino**: Dirección IP o red de destino.  
  - **Máscara de subred**: Define el alcance de la red destino.  
  - **Gateway**: Dirección del próximo salto (router) hacia el destino.  
  - **Interfaz**: Puerto físico por donde enviar el paquete.  
  - **Métrica**: "Costo" de la ruta (ej: distancia, retraso).  

- **Funcionamiento**:  
  Cuando un paquete llega al router, este:  
  - Consulta la tabla de enrutamiento.  
  - Compara la dirección IP destino con las entradas de la tabla.  
  - Elige la ruta más eficiente (menor métrica o coincidencia más específica).  
  - Reenvía el paquete por el puerto/gateway correspondiente.  


---

#### **3. Flechas Talladas vs. Flechas Móviles**  

| **Característica**       | **Flechas Talladas en Piedra**         | **Flechas Móviles**                   |  
|--------------------------|---------------------------------------|---------------------------------------|  
| **Tipo de Enrutamiento** | **Enrutamiento Estático**             | **Enrutamiento Dinámico**             |  
| **Definición**           | Rutas configuradas manualmente.       | Rutas aprendidas automáticamente mediante protocolos (OSPF, BGP). |  
| **Flexibilidad**         | Inmutables (requieren intervención humana para cambiar). | Se adaptan a cambios en la red (ej: caída de enlaces). |  
| **Ejemplo**              | Una ruta fija a una red corporativa.  | Rutas en Internet que se ajustan según congestión o fallos. |  
| **Ventajas**             | - Bajo consumo de recursos. <br> - Mayor seguridad. | - Escalabilidad. <br> - Autonomía.    |  
| **Desventajas**          | - No se adapta a cambios. <br> - Inviable en redes grandes. | - Mayor complejidad. <br> - Consumo de ancho de banda para actualizaciones. |  

---

#### **4. Conclusión**  
- **Tótem = Tabla de Enrutamiento**: Las flechas son las rutas almacenadas en el router.  
- **Flechas Talladas**: Rutas estáticas, ideales para redes pequeñas o rutas críticas que no cambian.  
- **Flechas Móviles**: Rutas dinámicas, esenciales en redes grandes como Internet, donde la topología es cambiante.  

Este sistema garantiza que los "mensajes" (paquetes de datos) siempre encuentren el mejor camino hacia su destino, ya sea fijo o adaptable.

## Ejercicio 5

#### **1. Técnica de Redes Moderna**  
La leyenda representa **NAT (Network Address Translation)** o **Traducción de Direcciones de Red**.

---

#### **2. Descripción del Mecanismo**  
- **¿Qué es NAT?**  
  Es un protocolo que permite que múltiples dispositivos en una red privada compartan una **única dirección IP pública** al comunicarse con redes externas (como Internet).  

- **¿Cómo funciona?**  
  - **Direcciones privadas**: Los dispositivos internos usan IPs privadas (ej: `192.168.1.2`, `10.0.0.3`), que no son enrutables en Internet.  
  - **Traducción**: Cuando un dispositivo envía datos al exterior, el router (el "guardián") reemplaza la IP privada por su propia IP pública.  
  - **Registro**: El router guarda en una tabla la correspondencia entre la IP:puerto interno y la IP:puerto externo.  
  - **Respuesta**: Al recibir una respuesta, el router consulta su tabla y reenvía los datos al dispositivo interno correcto.  


---

#### **3. Beneficios de NAT**  

| **Beneficio**                | **Explicación**                                                                 |  
|------------------------------|---------------------------------------------------------------------------------|  
| **Conservación de IPs**       | Permite que cientos de dispositivos usen una sola IP pública, mitigando la escasez de IPv4. |  
| **Seguridad**                 | Oculta las direcciones IP internas, dificultando ataques directos a dispositivos de la red local. |  

---

#### **4. Ejemplo Práctico**  
- **Escenario**: Una casa con 10 dispositivos (PC, móviles, tablets) conectados a un router con IP pública `85.120.20.45`.  
- **Funcionamiento**:  
  - Todos los dispositivos envían solicitudes a Internet usando la IP `85.120.20.45`.  
  - El router traduce y registra cada conexión (ej: `192.168.1.2:5000` → `85.120.20.45:60001`).  
  - Las respuestas se redirigen al dispositivo correcto basándose en el puerto.  

---

#### **5. Conclusión**  
El Guardián de la Máscara es una metáfora perfecta de **NAT**:  
- **Máscara única**: Todos los dispositivos parecen tener la misma IP pública.  
- **Traducción**: El router actúa como intermediario, recordando "quién es quién" en la red interna.  
- **Ventajas**: Ahorro de IPs y protección de la red interna, pilares clave en redes domésticas y empresariales.

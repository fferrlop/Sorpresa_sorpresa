### **Respuesta al Enigma de las Subredes**

#### **1. Máscara de Subred Utilizada**  
La máscara de subred que habrían usado los antiguos es **255.255.255.192** (o **/26** en notación CIDR).

---

#### **2. Direcciones de Host Utilizables por Subred**  
Cada subred tendría **62 direcciones de host utilizables**.

---

#### **3. Explicación Detallada del Cálculo**  

**Paso 1: Determinar los bits necesarios para 4 subredes**  
- Para dividir la red en **4 subredes**, se necesitan:  
  \[
  \log_2(4) = 2 \ \text{bits prestados de la porción de host}.
  \]
- La máscara original de la red base (192.168.50.0) es **/24** (255.255.255.0).  
- Al prestar **2 bits**, la nueva máscara será:  
  \[
  24 \, (\text{original}) + 2 \, (\text{prestados}) = \textbf{/26} \, (\text{255.255.255.192}).
  \]

**Paso 2: Calcular las direcciones por subred**  
- Con una máscara **/26**, los **6 bits restantes** (32 bits totales - 26 bits para red = 6 bits para hosts) se usan para hosts:  
  \[
  2^6 = 64 \ \text{direcciones por subred (totales)}.
  \]
- Direcciones **utilizables** (se restan dirección de red y broadcast):  
  \[
  64 - 2 = \textbf{62 hosts por subred}.
  \]

**Paso 3: Identificar las subredes resultantes**  
Las 4 subredes serían:  

| **Subred**         | **Rango Utilizable**                 |
|---------------------|--------------------------------------|
| 192.168.50.0/26    | 192.168.50.1 – 192.168.50.62        |
| 192.168.50.64/26   | 192.168.50.65 – 192.168.50.126      |
| 192.168.50.128/26  | 192.168.50.129 – 192.168.50.190     |
| 192.168.50.192/26  | 192.168.50.193 – 192.168.50.254     |

---

#### **4. Resumen Final**  
| **Aspecto**               | **Detalle**                              |
|---------------------------|------------------------------------------|
| Máscara de subred         | 255.255.255.192 (/26)                    |
| Direcciones totales/subred| 64                                       |
| Direcciones útiles/subred | 62                                       |
| Subredes creadas          | 4                                        |

**Conclusión**:  
Los antiguos lograron dividir su "reino digital" en 4 subredes iguales usando una máscara /26, asignando 62 direcciones útiles a cada gremio. Esto resolvía la demanda de equidad y organización descrita en la losa. 🔢




### **Respuesta: La Encrucijada de las Rutas**

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
  1. Consulta la tabla de enrutamiento.  
  2. Compara la dirección IP destino con las entradas de la tabla.  
  3. Elige la ruta más eficiente (menor métrica o coincidencia más específica).  
  4. Reenvía el paquete por el puerto/gateway correspondiente.  

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

Este sistema garantiza que los "mensajes" (paquetes de datos) siempre encuentren el mejor camino hacia su destino, ya sea fijo o adaptable. 🌐  

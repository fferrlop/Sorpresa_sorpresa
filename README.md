### **Respuesta al Enigma de las Subredes**

#### **1. Máscara de Subred Utilizada**  
La máscara de subred que habrían usado los antiguos es **255.255.255.192** (en notación CIDR: **/26**).

---

#### **2. Direcciones de Host Utilizables por Subred**  
Cada subred tendría **62 direcciones de host utilizables**.

---

#### **3. Explicación Detallada del Cálculo**  

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

---

#### **4. Resumen Final**  
| **Aspecto**               | **Detalle**                              |
|---------------------------|------------------------------------------|
| Máscara de subred         | `255.255.255.192` (/26)                  |
| Direcciones totales/subred| 64                                       |
| Direcciones útiles/subred | 62                                       |
| Subredes creadas          | 4                                        |

**Conclusión**:  
Los antiguos lograron dividir su "reino digital" en 4 subredes iguales usando una máscara `/26`, asignando **62 direcciones útiles** a cada gremio. 🔢

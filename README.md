## Ejercicio 1: La Ruta Perdida entre Dos Reinos

### **Topología**
- **Ciudad A**:  
  - R_A (Router 1841)  
  - SW_A (Switch 2960)  
  - AP_A (Access Point)  
  - PC_A_1 y PC_A_2  
  - Conexiones: Cobre (física) + WiFi  

- **Ciudad B**:  
  - R_B (Router 1841)  
  - SW_B (Switch 2960)  
  - AP_B (Access Point)  
  - PC_B_1 y PC_B_2  
  - Conexiones: Cobre (física) + WiFi  

- **Red WAN**:  
  - Cloud (simulación WAN con Frame-Relay)  
  - Enlaces seriales DTE  

---

### **Configuración de Red**

#### **Conexiones WAN**
| Dispositivo | Interfaz        | IP              | Máscara            | DLCI  |
|-------------|-----------------|------------------|--------------------|-------|
| R_A         | Serial 0/0/0    | 192.168.30.1     | 255.255.255.252    | 101   |
| R_B         | Serial 0/0/0    | 192.168.30.2     | 255.255.255.252    | 102   |
| **Cloud**   | Serial5 ↔ Serial6 | -                | -                  | -     |

- **Frame-Relay**: Mapeo Serial5 a Serial6 en la nube.

#### **Conexiones LAN**
| Ciudad | Red           | Máscara          | SSID        | Password     |
|--------|---------------|------------------|-------------|--------------|
| A      | 192.168.10.0  | 255.255.255.0    | LaMasia     | ViscaBarsa   |
| B      | 192.168.20.0  | 255.255.255.0    | LaFabrica   | AlaMadrid    |

---

### **Tabla de Dispositivos**
| Dispositivo | Interfaz          | IP              | Máscara            |
|-------------|-------------------|------------------|--------------------|
| R_A         | FastEthernet0/0   | 192.168.10.1     | 255.255.255.0      |
| R_A         | Serial0/0/0       | 192.168.30.1     | 255.255.255.252    |
| R_B         | FastEthernet0/0   | 192.168.20.1     | 255.255.255.0      |
| R_B         | Serial0/0/0       | 192.168.30.2     | 255.255.255.252    |

#### **Rutas Estáticas**
- **R_A**: `192.168.20.0/24` vía `192.168.30.2`  
- **R_B**: `192.168.10.0/24` vía `192.168.30.1`  

---

### **Resultado**
- Paquetes enviados exitosamente:  
  - PC_A_1 → PC_B_1  
  - PC_A_2 → PC_B_2  

---

## Ejercicio 2: La Ciudad de las Redes Aisladas

### **Topología**
- **Dispositivos Principales**:  
  - Router "Gran_Torre_Central" (1941)  
  - Switch (2960)  
  - **Gremio de Arquitectos**:  
    - AP  
    - PC_A_1 (WiFi) y PC_A_2 (Cable)  
  - **Gremio de Escribas**:  
    - AP  
    - PC_E_1 (WiFi), PC_E_2 (Cable), Printer_E (WiFi)  

---

### **Configuración de Red**

#### **VLANs en el Switch**
| VLAN  | Nombre         | Puertos (Modo Access)    |
|-------|----------------|--------------------------|
| 10    | Arquitectos    | Fa0/1 – Fa0/12           |
| 20    | Escribas       | Fa0/13 – Fa0/24          |
| -     | **Trunk**      | Gig0/1 (conexión al router) |

#### **Router "Gran Torre Central"**
| Interfaz          | IP              | Función                   |
|-------------------|------------------|---------------------------|
| Gig0/0.10         | 192.168.10.1     | Subinterfaz para VLAN 10  |
| Gig0/0.20         | 192.168.20.1     | Subinterfaz para VLAN 20  |

#### **Dispositivos Finales**
| Dispositivo   | Interfaz       | IP              |
|---------------|----------------|------------------|
| PC_A_1        | Wireless       | 192.168.10.2    |
| PC_A_2        | FastEthernet   | 192.168.10.3    |
| PC_E_1        | Wireless       | 192.168.20.2    |
| PC_E_2        | FastEthernet   | 192.168.20.3    |
| Printer_E     | Wireless       | 192.168.20.4    |

---

### **Resultado**
- Conexiones exitosas entre dispositivos de ambas VLANs.  
- Pruebas de envío de paquetes confirmadas como funcionales.  

## Paso 4: Capa de Transporte – Selección y Cálculo de Ventana

### 🔹 Decisión de Protocolos

En la red diseñada, se seleccionan los protocolos de la capa de transporte en función del tipo de servicio requerido:

- *TCP* se utiliza para la *transferencia segura de archivos* (por ejemplo, mediante servicios como *FTP o SFTP*) debido a su control de flujo, fiabilidad y retransmisión en caso de pérdida.
- *UDP* se utiliza para el *streaming multimedia* (como conferencias en vídeo o material audiovisual), ya que permite una transmisión más rápida al no requerir confirmación de entrega, ideal para comunicaciones en tiempo real.

---

### 🔹 Cálculo de la Ventana de Transmisión

Para mejorar el rendimiento de TCP, es importante dimensionar correctamente la *ventana de transmisión*. Esta ventana indica cuánto puede enviar el emisor antes de necesitar una confirmación del receptor.

El tamaño óptimo de la ventana (en bits) se calcula con la fórmula:


Ventana = RTT × Ancho de banda


> Donde:
> - *RTT (Round Trip Time)*: Tiempo total de ida y vuelta de un paquete.
> - *Ancho de banda*: Capacidad del enlace en bits por segundo.

---

### 🔸 Ejemplo de Cálculo:

Supongamos un *RTT de 50 ms (0.05 s)* y un *ancho de banda de 10 Mbps*:


Ventana = 0.05 s × 10 × 10^6 bps = 500,000 bits


Convertido a bytes:


500,000 bits ÷ 8 = 62,500 bytes


Es decir, la ventana óptima sería de *62.5 KB*.

---

### 🔹 Relación con MSS (Maximum Segment Size)

Dado un *MSS típico de 1460 bytes*, se puede calcular cuántos segmentos pueden transmitirse antes de requerir una ACK:


62,500 bytes ÷ 1460 ≈ 42.8 segmentos


Esto permite ajustar el tamaño de la ventana TCP y prever el rendimiento de la red para transferencias de archivos, especialmente en los enlaces críticos entre routers.

---

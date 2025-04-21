## Paso 1: Calcular el MSS

```
MSS = MTU - Encabezados IP/TCP
MSS = 1500 bytes - 40 bytes
MSS = 1460 bytes
```

---

## Paso 2: Calcular el Bandwidth-Delay Product (BDP)

```
BDP (bits) = Ancho de Banda × RTT
BDP (bits) = 1,000,000,000 bits/s × 0.012 s
BDP (bits) = 12,000,000 bits

BDP (bytes) = BDP (bits) ÷ 8
BDP (bytes) = 12,000,000 bits ÷ 8
BDP (bytes) = 1,500,000 bytes
```

---

## Paso 3: Determinar el Tamaño de la Ventana TCP

```
Ventana Óptima (bytes) = BDP
Ventana Óptima (bytes) = 1,500,000 bytes

Ventana Óptima (segmentos) = BDP ÷ MSS
Ventana Óptima (segmentos) = 1,500,000 bytes ÷ 1460 bytes/segmento
Ventana Óptima (segmentos) ≈ 1027 segmentos
```

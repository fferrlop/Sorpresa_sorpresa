## Paso 5: Capa de Aplicación – Servicios y Multiplexación


### Streaming Multimedia

En un entorno académico con transmisión de contenido multimedia, como videoconferencias o clases grabadas, es fundamental garantizar una experiencia fluida para todos los usuarios, incluso si cuentan con diferentes calidades de conexión. Para ello, una técnica adecuada es el *Adaptive HTTP Streaming, concretamente **DASH (Dynamic Adaptive Streaming over HTTP)*.

DASH divide el contenido multimedia en pequeños segmentos de distintos niveles de calidad. El cliente selecciona y descarga dinámicamente la versión más adecuada en función del *ancho de banda disponible en tiempo real*. Si la conexión es estable, se reproducen segmentos de mayor calidad; si hay congestión o caídas, se cambia automáticamente a una calidad inferior para evitar interrupciones.

Este enfoque optimiza el rendimiento de la red, mejora la experiencia del usuario y se adapta bien a entornos heterogéneos como el planteado en este proyecto, donde coexisten conexiones cableadas y WiFi con distintos niveles de velocidad y estabilidad.

---

### Diseño de Servicios

En un diseño de red como el del presente proyecto, se contempla la *implementación de servicios FTP/SFTP* para permitir la transferencia segura de archivos grandes entre nodos, y *servicios HTTP/HTTPS* para ofrecer contenido multimedia como conferencias grabadas o materiales interactivos.

La *resolución de nombres DNS* cumple un papel clave, permitiendo que los usuarios accedan a recursos mediante nombres de dominio en lugar de direcciones IPv6, lo cual mejora la usabilidad del sistema. Esta resolución es gestionada por un servidor DNS, que responde a las consultas de los clientes indicando la dirección correspondiente al nombre solicitado.

Para soportar *múltiples solicitudes simultáneas, se aplican técnicas de **multiplexación*, que permiten que un único servidor atienda varios clientes al mismo tiempo. Esto se logra utilizando diferentes puertos o identificadores de sesión, garantizando una comunicación eficiente y sin interferencias entre usuarios.

# Estimación de Costes del Proyecto de Red (Actualizada)

| Elemento                             |   Cantidad |   Precio Unitario (€) |   Subtotal (€) |
|:-------------------------------------|-----------:|----------------------:|---------------:|
| Routers Cisco 2911                   |          5 |                 850   |           4250 |
| Switches Cisco Catalyst 2960 (PT)    |          5 |                 400   |           2000 |
| Switch Central PT (Core)             |          1 |                 400   |            400 |
| Access Points                        |          3 |                 250   |            750 |
| PCs / Laptops / Dispositivos Cliente |         10 |                 500   |           5000 |
| Servidores (DNS, Web, FTP)           |          3 |                 900   |           2700 |
| ASA 5506-X (Firewall)                |          1 |                 800   |            800 |
| Cables de fibra multimodo (LC-LC)    |        200 |                   0.8 |            160 |
| Cables de cobre Cat6                 |       2500 |                   0.4 |           1000 |
| Rack y montaje                       |          1 |                1000   |           1000 |
| Home Gateway IoT                     |          5 |                 150   |            750 |
| Detectores de Humo IoT               |          5 |                  50   |            250 |
| Cámaras de Videovigilancia IoT       |          3 |                 180   |            540 |
| Altavoces Inteligentes IoT           |          4 |                 120   |            480 |
| Servidor de Correo Electrónico       |          1 |                 900   |            900 |

*Coste total estimado: 23000.00 €*

# Manual Técnico Proyecto 1

## Enunciado

La empresa "Tech Solutions S.A." necesita una red que permita la comunicación
eficiente entre sus departamentos. Debido a las limitaciones presupuestarias, se
utilizará un mismo medio físico para conectar las áreas, pero se segmentará
lógicamente mediante VLANs. Además, se requiere redundancia en la conexión
para evitar fallas críticas.
Se debe diseñar e implementar la red con la siguiente estructura de 5 secciones:
1. Área central (backbone).
2. Área de administración
3. Área de desarrollo
4. Área de infraestructura
5. Área de gerencia
Dentro de las secciones anteriormente mencionadas se debe de segmentar la red
con diferentes departamentos y vlans.


Departamentos y VLANs
|Departamento |Vlan |ID de red|
|-|-|-|
|Ventas| 1X| 192.168.1x.0/24|
|Soporte| 2X| 192.168.2x.0/24|
|Gerencia| 3X| 192.168.3x.0/24|
|Seguridad| 4X| 192.168.4x.0/24|



## Solución propuesta

### Segmentación de IP por área.
Se toma de base el último digito de cada carnet del equipo y la suma de ambos nos da el valor de vlan y de inicio de red.
Lo cual nos da el resultado de "2"

Departamentos y VLANs
|Departamento |Vlan |ID de red|
|-|-|-|
|Ventas| 12| 192.168.12.0/24|
|Soporte| 22| 192.168.22.0/24|
|Gerencia| 32| 192.168.32.0/24|
|Seguridad| 42| 192.168.42.0/24|

### Bosquejo imagen
-   Mensaje ARP e ICMP en simulación con los host AUPC1 y RMPC6
![alt text](imagenes/imagen-10.jpg)
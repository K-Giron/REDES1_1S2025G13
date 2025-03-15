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

### CONFIGURACIONES DE LOS SWITCH MODO CLIENTE


##### MSW1 CLIENTE
<img src="./imagenes/CONFIGURACION MSW1.GIF">


##### SERVER
<img src="./imagenes/CONFIGURACION SERVER.GIF">

##### MSW2 CLIENTE
<img src="./imagenes/CONFIGURACION MSW2.GIF">

##### MSW3 CLIENTE
<img src="./imagenes/CONFIGURACION MSW3.GIF">

##### MSW4 CLIENTE
<img src="./imagenes/CONFIGURACION MSW4.GIF">

##### MSW9 CLIENTE
<img src="./imagenes/CONFIGURACION MSW9.GIF">

##### MSW10 CLIENTE
<img src="./imagenes/CONFIGURACION MSW10.GIF">

##### SW0 CLIENTE
<img src="./imagenes/CONFIGURACION SW0.GIF">

##### SW1 CLIENTE
<img src="./imagenes/CONFIGURACION SW1.GIF">

##### SW2 CLIENTE
<img src="./imagenes/CONFIGURACION SW2.GIF">

##### SW3 CLIENTE
<img src="./imagenes/CONFIGURACION SW3.GIF">

##### SW4 CLIENTE
<img src="./imagenes/CONFIGURACION SW4.GIF">

##### MSW6 CLIENTE
<img src="./imagenes/CONFIGURACION MSW6.GIF">

##### MSW7 CLIENTE
<img src="./imagenes/CONFIGURACION MSW7.GIF">

##### SW8 CLIENTE
<img src="./imagenes/CONFIGURACION SW8.GIF">

##### SW9 CLIENTE
<img src="./imagenes/CONFIGURACION SW9.GIF">

##### SW10 CLIENTE
<img src="./imagenes/CONFIGURACION SW10.GIF">

##### MSW11 CLIENTE
<img src="./imagenes/CONFIGURACION MSW11.GIF">

##### SW6 CLIENTE
<img src="./imagenes/CONFIGURACION SW6.GIF">

##### SW7 CLIENTE
<img src="./imagenes/CONFIGURACION SW7.GIF">

##### MSW8 CLIENTE
<img src="./imagenes/CONFIGURACION MSW8.GIF">

##### SW11 CLIENTE
<img src="./imagenes/CONFIGURACION SW11.GIF">

##### SW12 CLIENTE
<img src="./imagenes/CONFIGURACION SW12.GIF">

##### SW13 CLIENTE
<img src="./imagenes/CONFIGURACION SW13.GIF">







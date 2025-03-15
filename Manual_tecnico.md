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
|Recepcion|52|192.168.52.0/24|

### Tabla de direcciones IP por área.

#### Área de Ventas

Direccionamiento del área de ventas

##### Rangos de direccionamiento asignados

192.168.12.0- 192.168.12.255

| Hostname             | Dirección IP | Puerto         |
| -------------------- | ------------ | -------------- |
| Ventas1 192.168.12.1 | 192.168.12.1 | FasthEthernet0 |
| Ventas2 192.168.12.2 | 192.168.12.2 | FasthEthernet0 |
| Ventas3 192.168.12.3 | 192.168.12.3 | FasthEthernet0 |
| Ventas4 192.168.12.4 | 192.168.12.4 | FasthEthernet0 |

#### Área de Soporte

Direccionamiento del área de soporte

##### Rangos de direccionamiento asignados

192.168.22.0- 192.168.22.255

| Hostname                      | Dirección IP | Puerto         |
| ----------------------------- | ------------ | -------------- |
| Soporte_tecnico1 192.168.22.1 | 192.168.22.1 | FasthEthernet0 |
| Soporte_tecnico2 192.168.22.2 | 192.168.22.2 | FasthEthernet0 |
| Soporte_tecnico3 192.168.22.3 | 192.168.22.3 | FasthEthernet0 |
| Soporte_tecnico4 192.168.22.4 | 192.168.22.4 | FasthEthernet0 |
| Soporte_tecnico5 192.168.22.5 | 192.168.22.5 | FasthEthernet0 |

#### Área de Gerencia

Direccionamiento del área de Gerencia

##### Rangos de direccionamiento asignados

192.168.32.0- 192.168.32.255

| Hostname               | Dirección IP | Puerto         |
| ---------------------- | ------------ | -------------- |
| Gerencia1 192.168.32.1 | 192.168.32.1 | FasthEthernet0 |
| Gerencia2 192.168.32.2 | 192.168.32.2 | FasthEthernet0 |
| Gerencia3 192.168.32.3 | 192.168.32.3 | FasthEthernet0 |
| Gerencia4 192.168.32.4 | 192.168.32.4 | FasthEthernet0 |
| Gerencia5 192.168.32.5 | 192.168.32.5 | FasthEthernet0 |

#### Área de Seguridad

Direccionamiento del área de seguridad

##### Rangos de direccionamiento asignados

192.168.42.0- 192.168.42.255

| Hostname                | Dirección IP | Puerto         |
| ----------------------- | ------------ | -------------- |
| Seguridad1 192.168.42.1 | 192.168.42.1 | FasthEthernet0 |
| Seguridad2 192.168.42.2 | 192.168.42.2 | FasthEthernet0 |
| Seguridad3 192.168.42.3 | 192.168.42.3 | FasthEthernet0 |
| Seguridad4 192.168.42.4 | 192.168.42.4 | FasthEthernet0 |
| Seguridad5 192.168.42.5 | 192.168.42.5 | FasthEthernet0 |
| Seguridad6 192.168.42.6 | 192.168.42.6 | FasthEthernet0 |
| Seguridad7 192.168.42.7 | 192.168.42.7 | FasthEthernet0 |

#### Área de Recepción

Direccionamiento del área conectada al Switch SW5

##### Rangos de direccionamiento asignados

192.168.52.0- 192.168.52.255

| Hostname                | Dirección IP | Puerto         |
| ----------------------- | ------------ | -------------- |
| Recepcion1 192.168.52.1 | 192.168.52.1 | FasthEthernet0 |
| Recepcion2 192.168.52.2 | 192.168.52.2 | FasthEthernet0 |
| Recepcion3 192.168.52.3 | 192.168.52.3 | FasthEthernet0 |
| Recepcion4 192.168.52.4 | 192.168.52.4 | FasthEthernet0 |

### Implementación de topologías

#### Área de infraestructura

![alt text](/imagenes/areaInfra.png)

#### Área de Administración

![alt text](/imagenes/areaAdmin.png)

#### Área de Desarrollo

![alt text](/imagenes/areaDesarrollo.png)

#### Área de Gerencia

![alt text](/imagenes/areaGeren.png)

#### Área Central

![alt text](/imagenes/areaCentral.png)

#### Área Recepción

![alt text](/imagenes/areaRecep.png)

### Presupuesto de Proyecto: Implementación de Red Local para Tech Solutions S.A.

#### Descripción General

El proyecto consistirá en el diseño e implementación de una red local para "Tech Solutions S.A.", la cual contará con segmentación mediante VLANs, redundancia usando STP y Etherchannel, y administración centralizada mediante VTP. Además, se utilizará Packet Tracer para la simulación y configuración de la red.

---

#### 1. **Equipos de Red Requeridos**

##### **A. Switches**

Se requieren switches de alta calidad que soporten VLANs, STP, VTP y Etherchannel.

| **Equipo**                                         | **Cantidad** | **Precio Unitario (Q)** | **Costo Total (Q)** |
| -------------------------------------------------- | ------------ | ----------------------- | ------------------- |
| Cisco Catalyst 2960-X (Switch Layer 2)             | 12           | 3,875                   | 46,500              |
| Cisco Catalyst 9300 (Switch Layer 3 para Backbone) | 2            | 27,125                  | 54,250              |

###### **B. Ruteadores**

Se requiere un ruteador para administrar las conexiones inter-VLAN.

| **Equipo**                                 | **Cantidad** | **Precio Unitario (Q)** | **Costo Total (Q)** |
| ------------------------------------------ | ------------ | ----------------------- | ------------------- |
| Cisco ISR 4331 (Router para Interconexión) | 1            | 9,300                   | 9,300               |

###### **C. Servidores**

Un servidor dedicado para la administración de VTP y otros servicios de red.

| **Equipo**                                  | **Cantidad** | **Precio Unitario (Q)** | **Costo Total (Q)** |
| ------------------------------------------- | ------------ | ----------------------- | ------------------- |
| Servidor Dell PowerEdge R440 (Servidor VTP) | 1            | 15,500                  | 15,500              |

###### **D. Cables y Conectividad**

Incluye cables de red y conectores para las conexiones físicas entre los dispositivos.

| **Equipo**                                   | **Cantidad** | **Precio Unitario (Q)** | **Costo Total (Q)** |
| -------------------------------------------- | ------------ | ----------------------- | ------------------- |
| Cable de red CAT6 (100 metros)               | 5            | 620                     | 3,100               |
| Transceivers SFP+ (para conexiones de fibra) | 6            | 1,160                   | 6,960               |

###### **E. Equipos de Red para Redundancia**

El diseño incluye redundancia para las conexiones del Backbone e interconexión entre áreas, lo que requiere la implementación de Etherchannel.

| **Equipo**                         | **Cantidad** | **Precio Unitario (Q)** | **Costo Total (Q)** |
| ---------------------------------- | ------------ | ----------------------- | ------------------- |
| Módulos Etherchannel (LACP y PAGP) | 2            | 775                     | 1,550               |

---

##### 2. **Software y Licencias**

### **A. Software de Simulación (Packet Tracer)**

El software utilizado para la simulación de la red será Packet Tracer, que es gratuito y accesible para fines educativos.

| **Equipo**                               | **Cantidad** | **Precio Unitario (Q)** | **Costo Total (Q)** |
| ---------------------------------------- | ------------ | ----------------------- | ------------------- |
| Cisco Packet Tracer (Licencia Educativa) | 1            | 0                       | 0                   |

###### **B. Licencias de Cisco para Switches y Ruteadores**

Para la correcta implementación de VTP, STP y Etherchannel, se requerirán licencias específicas para los switches y ruteadores de Cisco.

| **Equipo**                               | **Cantidad** | **Precio Unitario (Q)** | **Costo Total (Q)** |
| ---------------------------------------- | ------------ | ----------------------- | ------------------- |
| Licencia Cisco IOS (por switch y router) | 1            | 775                     | 775                 |

---

##### 3. **Trabajo y Consultoría**

Este presupuesto incluye el tiempo necesario para la planificación, configuración y pruebas de la red, así como la consultoría para optimizar el rendimiento de la red.

| **Servicio**                       | **Horas** | **Costo por Hora (Q)** | **Costo Total (Q)** |
| ---------------------------------- | --------- | ---------------------- | ------------------- |
| Consultoría y Planificación de Red | 30        | 387.50                 | 11,625              |
| Configuración y Pruebas de Red     | 40        | 465                    | 18,600              |

---

##### 4. **Costo Total Estimado**

| **Descripción**                                | **Costo Total (Q)** |
| ---------------------------------------------- | ------------------- |
| Equipos de Red (Switches, Routers, Servidores) | 129,560             |
| Cables y Conectividad                          | 10,060              |
| Software y Licencias                           | 775                 |
| Trabajo y Consultoría                          | 30,225              |
| **Total del Proyecto**                         | **170,620 Q**       |

---

##### 5. **Resumen**

El presupuesto estimado para la implementación de la red local para "Tech Solutions S.A." es de **170,620 Q**. Este incluye todos los equipos de red necesarios, software, licencias, y el costo por la configuración y pruebas de la red. Los costos pueden variar según la elección de proveedores y ofertas actuales, pero este presupuesto proporciona una guía para la ejecución del proyecto.

Si necesitas más detalles sobre el presupuesto o ajustes en los equipos, no dudes en indicarlo.

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

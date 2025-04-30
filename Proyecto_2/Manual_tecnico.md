# Manual Técnico Proyecto 1

## Enunciado

El proyecto tiene como objetivo diseñar y configurar una red de comunicaciones que interconecte los centros de la Universidad de San Carlos de Guatemala (USAC). El estudiante deberá crear una topología de red utilizando Cisco Packet Tracer, simulando la interconexión de los siguientes centros: Sede Central, Centro Universitario de Nor Occidente (CUNOROC), Centro Universitario de Occidente (CUNOC), Centro Universitario de Chimaltenango (CUNDECH), y el Centro Universitario Metropolitano (CUM). El proyecto incluirá la segmentación de la red mediante la creación de VLANs para distintas áreas de la universidad, como Estudiantes, Docentes, Biblioteca, y Seguridad. Además, se implementará el ruteo inter-VLAN utilizando la técnica de Router on a Stick y configurando interfaces virtuales. El estudiante también deberá aplicar VLSM y FLSM para la asignación eficiente de direcciones IP, y configurar el ruteo estático y dinámico para asegurar la conectividad entre los centros.

## Solución

### Subneteo de Áreas

#### VLSM AREA DE CUNDECH

| VLAN        | ID DE VLAN | HOST REQUERIDOS | ID             | MASCARA | PRIMER HOST    | ULTIMO HOST    | BROADCAST      | HOST UTILIZABLES |
| ----------- | ---------- | --------------- | -------------- | ------- | -------------- | -------------- | -------------- | ---------------- |
| Biblioteca  | 42         | 100             | 192.168.13.0   | /25     | 192.168.13.2   | 192.168.13.126 | 192.168.13.127 | 126              |
| Estudiantes | 12         | 50              | 192.168.13.128 | /26     | 192.168.13.130 | 192.168.13.190 | 192.168.13.191 | 62               |
| Docentes    | 22         | 20              | 192.168.13.192 | /27     | 192.168.13.194 | 192.168.13.222 | 192.168.13.223 | 30               |
| Seguridad   | 32         | 5               | 192.168.13.224 | /29     | 192.168.13.226 | 192.168.13.230 | 192.168.13.231 | 26               |

#### VLSM AREA DE CUNOROC

| VLAN        | ID DE VLAN | HOST REQUERIDOS | ID             | MASCARA | PRIMER HOST    | ULTIMO HOST    | BROADCAST      | HOST UTILIZABLES |
| ----------- | ---------- | --------------- | -------------- | ------- | -------------- | -------------- | -------------- | ---------------- |
| Biblioteca  | 42         | 75              | 192.148.13.0   | /25     | 192.148.13.2   | 192.148.13.126 | 192.148.13.127 | 126              |
| Estudiantes | 12         | 45              | 192.148.13.128 | /26     | 192.148.13.130 | 192.148.13.190 | 192.148.13.191 | 62               |
| Docentes    | 22         | 25              | 192.148.13.192 | /27     | 192.148.13.194 | 192.148.13.222 | 192.148.13.223 | 30               |
| Seguridad   | 32         | 10              | 192.148.13.224 | /28     | 192.148.13.226 | 192.148.13.238 | 192.148.13.239 | 14               |

#### VLSM AREA DE CUNOC

| VLAN        | ID DE VLAN | HOST REQUERIDOS | ID            | MASCARA | PRIMER HOST   | ULTIMO HOST   | BROADCAST     | HOST UTILIZABLES |
| ----------- | ---------- | --------------- | ------------- | ------- | ------------- | ------------- | ------------- | ---------------- |
| Estudiantes | 12         | 60              | 172.16.13.0   | /26     | 172.16.13.2   | 172.16.13.62  | 172.16.13.63  | 62               |
| Biblioteca  | 42         | 50              | 172.16.13.64  | /26     | 172.16.13.66  | 172.16.13.126 | 172.16.13.127 | 62               |
| Docentes    | 22         | 35              | 172.16.13.128 | /26     | 172.16.13.130 | 172.16.13.190 | 172.16.13.191 | 62               |
| Seguridad   | 32         | 5               | 172.16.13.192 | /29     | 172.16.13.194 | 172.16.13.198 | 172.16.13.199 | 6                |

#### VLSM AREA DE CENTRAL

| VLAN    | ID DE VLAN | HOST REQUERIDOS | ID  | MASCARA | PRIMER HOST | ULTIMO HOST | BROADCAST | HOST UTILIZABLES |
| ------- | ---------- | --------------- | --- | ------- | ----------- | ----------- | --------- | ---------------- |
| Server0 | 52         | 60              |
| Server1 | 62         | 35              |
| Server2 | 72         | 5               |

#### VLSM AREA DE CUM

| VLAN        | ID DE VLAN | HOST REQUERIDOS | ID             | MASCARA | PRIMER HOST    | ULTIMO HOST    | BROADCAST      | HOST UTILIZABLES |
| ----------- | ---------- | --------------- | -------------- | ------- | -------------- | -------------- | -------------- | ---------------- |
| Biblioteca  | 42         | 75              | 192.158.13.0   | /25     | 192.158.13.2   | 192.158.13.126 | 192.158.13.127 | 126              |
| Estudiantes | 12         | 45              | 192.158.13.128 | /26     | 192.158.13.130 | 192.158.13.190 | 192.158.13.191 | 62               |
| Docentes    | 22         | 25              | 192.158.13.192 | /27     | 192.158.13.194 | 192.158.13.222 | 192.158.13.223 | 30               |
| Seguridad   | 32         | 10              | 192.158.13.224 | /28     | 192.158.13.226 | 192.158.13.238 | 192.158.13.239 | 14               |


### Comandos de configuracion

#### Área de CUNDECH

##### 1. Switch "SW7"(VTP Server)

enable
configure terminal

vtp domain Grupo13
vtp password usac2025
vtp mode server 

vlan 12
name Estudiantes
vlan 22
name Docentes
vlan 32
name Biblioteca
vlan 42
name Seguridad
exit

##### 2. Configuración de enlaces troncales en todos los Switch que conectan entre sí

interface FastEthernet0/1
switchport mode trunk
-- switchport trunk encapsulation dot1q
exit

##### 3. Configuración de Switches "SW6" y "SW8" en modo cliente

enable
configure terminal

vtp domain Grupo13
vtp password usac2025
vtp mode client
exit

##### 4. Configuración del switch multicapa "MS8"

enable
configure terminal

ip routing

vtp domain Grupo13
vtp password usac2025
vtp mode server



! Interfaces VLAN con IP correspondiente (puerta de enlace)
interface vlan 42
 ip address 192.168.13.1 255.255.255.128
 no shutdown

interface vlan 12
 ip address 192.168.13.129 255.255.255.192
 no shutdown

interface vlan 22
 ip address 192.168.13.193 255.255.255.224
 no shutdown

interface vlan 32
 ip address 192.168.13.225 255.255.255.248
 no shutdown

exit

##### 5. Asignar puertos a VLANs (Cualquier swtich con equipos de cómputo conectadas)

interface FastEthernet0/11
switchport mode access
switchport access vlan 32
exit

interface range FastEthernet0/12-13
switchport mode access
switchport access vlan 42
exit


#### Área de CUNOROC

##### 1. Switch "SW3"(VTP Server)

enable
configure terminal

vtp domain Grupo13
vtp password usac2025
vtp mode server

vlan 42
 name Biblioteca
vlan 12
 name Estudiantes
vlan 22
 name Docentes
vlan 32
 name Seguridad

interface range fa0/1 - 2
 switchport mode trunk

exit



##### 2. Configuración de Switches "SW4" y "SW2" en modo cliente

enable
configure terminal

vtp domain Grupo13
vtp password usac2025
vtp mode client

interface range fa0/1-2
 switchport mode trunk

exit

##### 3. Asignar puertos a VLANs (Cualquier swtich con equipos de cómputo conectadas)

SW4

interface FastEthernet0/11
switchport mode access
switchport access vlan 42
exit

interface range FastEthernet0/12
switchport mode access
switchport access vlan 32
exit

SW3

interface FastEthernet0/3
switchport mode access
switchport access vlan 12
exit

SW2

interface FastEthernet0/3
switchport mode access
switchport access vlan 22
exit

##### 4.  


#### Área de CUNOC

##### 1. Switch "MS0"(VTP Server) 

conf t
vtp domain Grupo13
vtp mode server
vtp password usac2025
exit

conf t
vlan 12
 name Estudiantes
vlan 22
 name Docentes
vlan 32
 name Seguridad
vlan 42
 name Biblioteca
exit


##### 2. VTP - MS1 y MS2 (modo cliente)

conf t
vtp domain Grupo13
vtp mode client
vtp password usac2025
exit

##### 3. Configuración de enlaces troncales en todos los Switch que conectan entre sí

MS1 y MS2
en
config t
interface range FastEthernet0/1-2
switchport mode trunk
switchport trunk encapsulation dot1q
exit

MS0
en
config t
interface range FastEthernet0/1-5
switchport mode trunk
switchport trunk encapsulation dot1q
exit

SW0, SW9 Y SW1
en
config t
interface FastEthernet0/1
switchport mode trunk
exit

##### 4. Configurar interfaces VLAN con HSRP (MS1 y MS2)

conf t
interface vlan 12
 ip address 172.16.13.3 255.255.255.192
 standby 12 ip 172.16.13.2
 standby 12 priority 110
 standby 12 preempt

interface vlan 42
 ip address 172.16.13.67 255.255.255.192
 standby 42 ip 172.16.13.66
 standby 42 priority 110
 standby 42 preempt

interface vlan 22
 ip address 172.16.13.131 255.255.255.192
 standby 22 ip 172.16.13.130
 standby 22 priority 110
 standby 22 preempt

interface vlan 32
 ip address 172.16.13.195 255.255.255.248
 standby 32 ip 172.16.13.194
 standby 32 priority 110
 standby 32 preempt
exit

##### 5. Comandos para MS1 (Switch Multicapa 1 — Activo en HSRP)

en
config ter
interface vlan 12
 ip address 172.16.13.2 255.255.255.192
 standby 12 ip 172.16.13.1
 standby 12 priority 110
 standby 12 preempt

interface vlan 42
 ip address 172.16.13.66 255.255.255.192
 standby 42 ip 172.16.13.65
 standby 42 priority 110
 standby 42 preempt

interface vlan 22
 ip address 172.16.13.130 255.255.255.192
 standby 22 ip 172.16.13.129
 standby 22 priority 110
 standby 22 preempt

interface vlan 32
 ip address 172.16.13.194 255.255.255.248
 standby 32 ip 172.16.13.193
 standby 32 priority 110
 standby 32 preempt

##### 6. Comandos para MS2 (Switch Multicapa 2 — Respaldo HSRP)

en
config ter
interface vlan 12
 ip address 172.16.13.3 255.255.255.192
 standby 12 ip 172.16.13.1
 standby 12 priority 100
 standby 12 preempt

interface vlan 42
 ip address 172.16.13.67 255.255.255.192
 standby 42 ip 172.16.13.65
 standby 42 priority 100
 standby 42 preempt

interface vlan 22
 ip address 172.16.13.131 255.255.255.192
 standby 22 ip 172.16.13.129
 standby 22 priority 100
 standby 22 preempt

interface vlan 32
 ip address 172.16.13.195 255.255.255.248
 standby 32 ip 172.16.13.193
 standby 32 priority 100
 standby 32 preempt

##### 7. Asignar puertos a VLANs en switches de acceso
conf t
interface range fa0/11-12
 switchport mode access
 switchport access vlan 12
exit

#### Area de CUM

##### 1. Asignar puertos a VLANs en switches de acceso
conf t
interface fa0/14
 switchport mode access
 switchport access vlan 42
exit

### Direccionamientos asignados


|Equipo|Departamento|Vlan|Dirección IP|Area|
|-------|------|-----|-------------|-------|
|Seguridad2|Seguridad|32|192.168.13.226|CUNDECH|
|Biblioteca3|Biblioteca|42|192.168.13.2|CUNDECH|
|Biblioteca4|Biblioteca|42|192.168.13.3|CUNDECH|
|Estudiantes6|Estudiantes|12|192.168.13.130|CUNDECH|
|Estudiantes7|Estudiantes|12|192.168.13.131|CUNDECH|
|Docentes7|Docentes|22|192.168.13.194|CUNDECH|
|Docentes6|Docentes|22|192.168.13.195|CUNDECH|


|Equipo|Departamento|Vlan|Dirección IP|Area|
|-------|------|-----|-------------|-------|
|Seguridad3|Seguridad|32|192.148.13.227|CUNOROC|
|Biblioteca1|Biblioteca|42|192.148.13.4|CUNOROC|
|Estudiantes3|Estudiantes|12|192.148.13.132|CUNOROC|
|Docentes3|Docentes|22|192.148.13.196|CUNOROC|


|Equipo|Departamento|Vlan|Dirección IP|Area|
|-------|------|-----|-------------|-------|
|Seguridad4|Seguridad|32|172.16.13.196|CUNOC|
|Estudiantes1|Estudiantes|12|172.16.13.4|CUNOC|
|Estudiantes2|Estudiantes|12|172.16.13.5|CUNOC|
|Docentes1|Docentes|22|172.16.13.132|CUNOC|
|Docentes2|Docentes|22|172.16.13.133|CUNOC|

|Equipo|Departamento|Vlan|Dirección IP|Area|
|-------|------|-----|-------------|-------|
|Seguridad1|Seguridad|32|192.158.13.226|CUM|
|Estudiantes5|Estudiantes|12|192.158.13.129|CUM|
|Docentes5|Docentes|22|192.158.13.194|CUM|
|Biblioteca2|Biblioteca|22|192.158.13.2|CUM|
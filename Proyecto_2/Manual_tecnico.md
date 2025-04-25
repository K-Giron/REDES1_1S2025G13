# Manual Técnico Proyecto 1

## Enunciado

El proyecto tiene como objetivo diseñar y configurar una red de comunicaciones que interconecte los centros de la Universidad de San Carlos de Guatemala (USAC). El estudiante deberá crear una topología de red utilizando Cisco Packet Tracer, simulando la interconexión de los siguientes centros: Sede Central, Centro Universitario de Nor Occidente (CUNOROC), Centro Universitario de Occidente (CUNOC), Centro Universitario de Chimaltenango (CUNDECH), y el Centro Universitario Metropolitano (CUM). El proyecto incluirá la segmentación de la red mediante la creación de VLANs para distintas áreas de la universidad, como Estudiantes, Docentes, Biblioteca, y Seguridad. Además, se implementará el ruteo inter-VLAN utilizando la técnica de Router on a Stick y configurando interfaces virtuales. El estudiante también deberá aplicar VLSM y FLSM para la asignación eficiente de direcciones IP, y configurar el ruteo estático y dinámico para asegurar la conectividad entre los centros.

## Subneteo de Áreas

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

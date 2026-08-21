# Proyecto Final - Fundamentos de Enrutamiento (ITLA)

**Estudiante:** Frederick Alexander Santos Rivera
**Matrícula:** 2025-0822

## Descripción

Este repositorio contiene la documentación de configuración de la
topología de red del proyecto final, organizada por equipo. Cada
archivo `.txt` explica el propósito y el porqué de cada bloque de
configuración, además de incluir los comandos completos aplicados
en Packet Tracer.

## Video de sustentación

Lista de reproducción en YouTube: [PEGAR AQUÍ EL LINK DE LA PLAYLIST]

## Orden lógico de configuración

| # | Archivo | Equipo | Función |
|---|---------|--------|---------|
| 1 | `01-SMC1.txt` | SMC1 | Switch multicapa: SSH, VLANs, SVIs, EtherChannel a SW3, enrutamiento entre VLANs, seguridad de puertos |
| 2 | `02-SW3.txt` | SW3 | Switch de acceso VLANs 2-7 (Servidores, Empleados, Finanzas, TI, WIFI), EtherChannel hacia SMC1 |
| 3 | `03-SW4.txt` | SW4 | Switch de acceso para WIFI (WLC y APs), puerto Fa0/4 para PC0 temporal |
| 4 | `04-SW1.txt` | SW1 | Switch de acceso VLANs 300/500/999, EtherChannel LACP con SW2 (Root Secondary) |
| 5 | `05-SW2.txt` | SW2 | Switch de acceso VLANs 300/500/999, EtherChannel LACP con SW1 (Root Primary) |
| 6 | `06-R1.txt` | R1 | Router-on-a-stick con HSRP (Standby) para VLANs 300, 500 y 999 |
| 7 | `07-R2.txt` | R2 | Router-on-a-stick con HSRP (Activo) para VLANs 300, 500 y 999 |
| 8 | `08-R3-DHCP.txt` | R3-DHCP | Servidor DHCP para todas las VLANs, rutas estáticas y ruta por defecto al ISP |
| 9 | `09-WLC.txt` | WLC | Configuración inicial y perfiles inalámbricos (SSIDs, AP Groups) |
| 10 | `10-PC0-temporal.txt` | PC0 | IP estática temporal para acceder al WLC antes del DHCP relay |

## Correcciones aplicadas respecto a versiones anteriores

1. Contraseña del WLC corregida a `Cisco123` (usuario Admin).
2. Se agregó DHCP Snooping y Dynamic ARP Inspection (DAI) en todos
   los switches de acceso (SMC1, SW1, SW2, SW3, SW4).
3. Se agregó `switchport nonegotiate` en todos los enlaces trunk
   para mitigar ataques de VLAN hopping por DTP spoofing.
4. Se agregó la PC0 temporal con IP estática en la subred WIFI y su
   exclusión correspondiente en el pool DHCP de R3-DHCP.
5. Se confirmó y documentó el puerto Fa0/4 en SW4 para conectar la
   PC0 temporal (PC0 Fa0 <-> SW4 Fa0/4).

## Archivo Packet Tracer

El archivo `.pkt` del proyecto se entrega por separado en la
plataforma virtual junto con el PDF que enlaza este repositorio y
la lista de reproducción del video.

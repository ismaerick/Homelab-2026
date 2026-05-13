# Homelab 2026

Un homelab personal construido en base a la virtualización con Proxmox, servicios de self-hostinh y una infraestructura multimedia dedicada. Este artículo abarca todo el hardware, los servicios gestionados, las máquinas virtuales y los equipos de red que estoy utilizando.

---

## Tabla de contenido

- [Hardware](#hardware)
  - [Servidor](#servidor)
  - [Almacenamiento](#almacenamiento)
  - [Networking](#networking)
- [Servicios y maquinas virtuales](#servicios-y-maquinas-virtuales)
  - [pve — HP EliteDesk 705 G4 DM (Host principal de Proxmox)](#pve--hp-elitedesk-705-g4-dm-host-principal-de-proxmox)
  
- [UPS](#ups)

---

## Hardware

### Servidor

| Host | Dispositivo | Rol |
|------|--------|------|
| **pve** | HP EliteDesk 705 G4 DM | Host principal de Proxmox — Servicios principales y VMs, servidor multimedia |

La NAS de ugreen provee un share NFS que se utiliza para hacer backups a todos los contenedores y maquinas virtuales en un intervalo diario.


### Almacenamiento

| Dispositivo | Rol |
|--------|------|
| **NAS UGREEN DH2300** | Usado para almacenamiento de archivos personales asi como shares NFS y SMB para backups de proxmox, fotos y archivos multimedia  |


### Networking

| Dispositivo | Rol |
|--------|------|
| **Huawei EchoLife HG8245H** | Router primario |
| **TP-Link TL-SG105** | Switch gigabit simple |
| **netgear wgr614** | Router viejo utilizado como access point |
| **TP-Link TL-WPA4220KIT** | Adaptador Wi-Fi powerline |


---

## Servicios y maquinas virtuales

### pve — HP EliteDesk 705 G4 DM (Host principal de Proxmox)

Por ahora el unico nodo que esta ejecutando Proxmox y que corre todos los servicios del homelab mediante contenedores LXC y maquinas virtuales.

#### Contenedores LXC

| Servicio | Descripcion | Link |
|---------|-------------|------|
| **AMP Control Panel** | Panel de control que facilita la creacion y la gestion de servidores de diferentes tipos de juegos | [Cubecoders/AMP](https://cubecoders.com/AMP) |
| **Pi-hole** | Bloqueo de anuncios y rastreadores basado en DNS en toda la red. Actúa como el principal resolvedor DNS para toda la red. | [pi-hole.net](https://pi-hole.net) |
| **Nginx Proxy manager** | Gestión de proxy inverso basada en web con automatización de certificados SSL a través de Let's Encrypt. | [nginxproxymanager.com](https://nginxproxymanager.com) |


#### Maquinas Virtuales

| VM | Descripcion|
|----|-------------|
| **Docker** | Host de Docker de propósito general para workloads en contenedores y servicios adicionales. |

Aqui se destacan varios servicios, mayormente con un proposito multimedia como series, peliculas, y fotografias

| Servicio | Descripcion | Link |
|---------|-------------|------|
| **Jellyfin** | Servidor multimedia principal para la transmisión de películas, programas de televisión y música a todos los dispositivos de la red y de forma remota. | [Jellyfin.org](https://jellyfin.org/) |
| **Stack de automatizacion de jellyfin** | Servicios de soporte para la gestión y el enriquecimiento de la biblioteca de Jellyfin. (e.j. Radarr, Sonarr, y herramientas similares). | — |
| **Immich** | Solución de copia de seguridad de fotos y vídeos autogestionada, que funciona como una alternativa a Google Fotos con soporte para aplicación móvil. | [immich.app](https://immich.app) |

La NAS de ugreen se conecta por un share NFS a esta maquina virtual para el almacenamiento de las fotos, peliculas, series.


#### Conexion remota

| Servicio | Descripcion | Link |
|---------|-------------|------|
| **Tailscale** | VPN principal utilizada para poder acceder a los servicios de manera remota, asi como proveer conectividad a familiares y amigos al servidor multimedia sin necesidas de abrir puertos | [Tailscale.com](https://tailscale.com/) |
| **Playit.gg** | Manera facil y rapida para conexion a servidores de diferentes juegos de manera remota sin necesidad de abrir puertos | [playit.gg](https://playit.gg/) |

---

## UPS

| Dispositivo | Rol |
|--------|------|
| **UPS HIKVISION 600VA** | Sistema de alimentación ininterrumpida que proporciona respaldo de batería y protección contra sobretensiones para equipos de laboratorio críticos. |

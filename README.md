## microservice home server

### hardware

Everything runs on a Lenovo IdeaPad Gaming 3 15" with 16 Gb of RAM, 512 Gb of internal nvme storage, and an Intel i7-12650H.

```
$ lscpu
Architecture:            x86_64
  CPU op-mode(s):        32-bit, 64-bit
  Address sizes:         39 bits physical, 48 bits virtual
  Byte Order:            Little Endian
CPU(s):                  16
  On-line CPU(s) list:   0-15
Vendor ID:               GenuineIntel
  Model name:            12th Gen Intel(R) Core(TM) i7-12650H
    CPU family:          6
    Model:               154
    Thread(s) per core:  2
    Core(s) per socket:  10
    Socket(s):           1
    Stepping:            3
    CPU max MHz:         4700.0000
    CPU min MHz:         400.0000
```

### media storge

32 TB of external HDD storage configured as RAID0 (striping) in a MAIWO 4 Bay USB 3.1 (USB-C) interface.

### services

traefik version 1.7.16 is used as a reverse proxy manager for requests made to my (sub)domains. 

- Traefik: `traefik:v1.7.16`
- Plex: `lscr.io/linuxserver/plex:latest`
- Dashdot: `mauricenino/dashdot`
- Radarr: `lscr.io/linuxserver/radarr:latest`
- Sonarr: `lscr.io/linuxserver/sonarr:latest`
- qBittorrent: `dyonr/qbittorrentvpn`
- Jackett: `lscr.io/linuxserver/jackett:latest`
- Portainer: `portainer/portainer`
- ForwardAuth: `thomseddon/traefik-forward-auth:2.1.0`
- Homarr: `ghcr.io/ajnart/homarr:0.12.2`

### security

All external traffic uses HTTPS. Externally-facing services require authentication through Google OAuth (whitelist) or basic authentication (e.g., Homarr dashboard). 

#### docker compose

all services (including traefik) are deployed in a single stack using Docker Compose version v2.19.1

see my [docker compose file](./docker-compose.yml).



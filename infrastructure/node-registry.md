[Home](../README.md) › [Infrastructure](README.md) › Node Registry

# Node Registry

This is the **single source of truth** for all hostnames, IP addresses, and roles in the homelab. All other documentation pages reference this table — never redefine hostnames elsewhere.

The homelab uses a **Tolkien / Middle-earth–inspired** hostname scheme with the `.shire` domain suffix.

---

## Homelab LAN — 10.136.20.0/24

| Hostname | Device | Role | IP |
|---|---|---|---|
| `the.shire` | N150 Mini-PC | OPNsense Router / Firewall / DNS / Ad-blocking | 10.136.20.1 |
| `hobbiton.shire` | Netgear GS108E | Core Managed Switch (8-port) | 10.136.20.2 |
| `greenway.shire` | Netgear GS308EP | PoE Managed Switch (8-port) | 10.136.20.3 |
| `bree.shire` | Zyxel NWA50AX | Wi-Fi 6 Access Point (OpenWRT) | 10.136.20.4 |
| `bill-the-pony.shire` | N150 Mini-PC | Proxmox VE Hypervisor | 10.136.20.10 |
| `isengard.shire` | Cel3867U Mini-PC | K3s Master Node | 10.136.20.11 |
| `rohan.shire` | N150 Mini-PC | K3s Worker Node 1 | 10.136.20.12 |
| `gondor.shire` | N150 Mini-PC | K3s Worker Node 2 | 10.136.20.13 |
| `valinor.shire` | Mac Mini M4 | LLM Server — LM Studio (inference) + OpenWebUI (Docker, frontend) | 10.136.20.20 |
| `tuckborough.shire` | Raspberry Pi 5B (8 GB) | Development / General-Purpose / Local app testing | 10.136.20.21 |
| `overhill.shire` | Raspberry Pi B+ | Hello App | 10.136.20.22 |
| `bywater.shire` | Raspberry Pi 2B | Development | 10.136.20.23 |
| `stock.shire` | Raspberry Pi Zero 2W | Development | 10.136.20.24 |
| `buckland.shire` | Orange Pi Zero 3 (4 GB) | Development | 10.136.20.25 |
| `crickhollow.shire` | Orange Pi Zero 3 (1 GB) | Development | 10.136.20.26 |
| `radagast.shire` | Proxmox VM (Debian 12) | n8n Workflow Automation | 10.136.20.101 |
| `gondolin.shire` | Proxmox VM (Debian 12) | GitLab CE | 10.136.20.102 |
| `rivendell.shire` | Proxmox VM (TrueNAS Scale) | NAS / File Storage | 10.136.20.103 |
| `thal.shire` | Proxmox VM (Debian 12) | Heimdall Dashboard | 10.136.20.104 |
| `palantir.shire` | Proxmox VM (Debian 12) | Grafana + Prometheus Monitoring | 10.136.20.105 |
| `khazad-dum.shire` | Proxmox VM (Ubuntu 24.04) | Kernel / Low-Level Development | 10.136.20.106 |
| `weathertop.shire` | Proxmox VM (Home Assistant OS) | Home Automation Hub | 10.136.20.107 / 10.136.30.5 |

---

## Workstation — 10.136.50.0/24

| Hostname | Device | Role | IP |
|---|---|---|---|
| `iron-hills.shire` | AMD X570 PC | Personal Workstation | 10.136.50.10 |

---

## IoT VLAN 30 — 10.136.30.0/24

| Hostname | Device | Role | IP |
|---|---|---|---|
| `proudfoot-00.shire` | ESP8266 | IoT Temp Sensor — Server rack | 10.136.30.10 |
| `proudfoot-01.shire` | ESP8266 | IoT Temp/Humidity Sensor — Living room | 10.136.30.11 |
| `proudfoot-02.shire` | ESP8266 | IoT Temp/Humidity Sensor — Bedroom | 10.136.30.12 |
| `proudfoot-03.shire` | ESP8266 | IoT Temp/Humidity Sensor — Bathroom | 10.136.30.13 |
| `proudfoot-04.shire` | ESP8266 | IoT Temp/Humidity Sensor — Kitchen | 10.136.30.14 |
| `took-00.shire` | Smart Plug | IoT Smart Plug — Server rack | 10.136.30.20 |
| `took-01.shire` | Smart Plug | IoT Smart Plug — Living room | 10.136.30.21 |

---

## Virtual APs / SSIDs (on `bree.shire`)

| Hostname | Type | Band | VLAN | Description |
|---|---|---|---|---|
| `bag-end.shire` | Virtual AP (SSID) | 5 GHz | 20 | Home Wi-Fi — homelab access |
| `green-dragon-inn.shire` | Virtual AP (SSID) | 2.4 GHz | 30 | IoT Wi-Fi — isolated to VLAN 30 |
| `prancing-pony.shire` | Virtual AP (SSID) | 2.4 GHz | 100 | Guest Wi-Fi — Internet only |

---

## Naming Convention

All devices follow a **Tolkien / Middle-earth** hostname scheme:
- Domain suffix: `.shire`
- Format: lowercase, hyphen-separated
- IoT devices use **Hobbit family surname** patterns (`proudfoot-NN`, `took-NN`)

See [networking/overview.md](../networking/overview.md) for the full naming convention breakdown.

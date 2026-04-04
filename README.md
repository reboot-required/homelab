# The Shire — Homelab

A self-hosted homelab built on a Lord of the Rings / Middle-earth hostname scheme with the `.shire` domain suffix. This repository is the single source of truth for all infrastructure documentation, service runbooks, and operational notes.

---

## Navigation

| Category | Description |
|---|---|
| [Infrastructure](infrastructure/README.md) | Hardware, node registry, rack layout |
| [Networking](networking/README.md) | Network topology, VLANs, DNS, OPNsense, wireless |
| [Compute](compute/README.md) | Proxmox VE hypervisor, K3s Kubernetes cluster |
| [Storage](storage/README.md) | TrueNAS Scale, backup strategy |
| [Services](services/README.md) | All running services with dedicated pages |
| [IoT](iot/README.md) | Sensors, smart plugs, MQTT |
| [Automation](automation/README.md) | GitLab CI/CD, configuration management |
| [Monitoring](monitoring/README.md) | Prometheus + Grafana monitoring stack |
| [Journal](journal/README.md) | Personal lab diary and LinkedIn post archive |
| [Changelog](CHANGELOG.md) | Dated log of all significant infrastructure changes |

---

## Naming Convention

All devices follow a **Tolkien / Middle-earth** hostname scheme:
- **Domain suffix:** `.shire`
- **Format:** lowercase, hyphen-separated
- **IoT devices:** Hobbit family surname pattern (`proudfoot-NN`, `took-NN`)
- **SSIDs / Virtual APs:** named after locations from the Shire (`bag-end`, `green-dragon-inn`, `prancing-pony`)

---

## Node Glossary

For the full authoritative table, see [infrastructure/node-registry.md](infrastructure/node-registry.md).

| Hostname | Device | Role | IP |
|---|---|---|---|
| `the.shire` | N150 Mini-PC | OPNsense Router / Firewall / DNS / Ad-blocking | 10.136.20.1 |
| `hobbiton.shire` | Netgear GS108E | Core Managed Switch (8-port) | 10.136.20.2 |
| `greenway.shire` | Netgear GS308EP | PoE Managed Switch (8-port) | 10.136.20.3 |
| `bree.shire` | Zyxel NWA50AX | Wi-Fi 6 Access Point (OpenWRT) | 10.136.20.151 |
| `bill-the-pony.shire` | N150 Mini-PC | Proxmox VE Hypervisor | 10.136.20.100 |
| `isengard.shire` | Cel3867U Mini-PC | K3s Master Node | 10.136.20.11 |
| `rohan.shire` | N150 Mini-PC | K3s Worker Node 1 | 10.136.20.12 |
| `gondor.shire` | N150 Mini-PC | K3s Worker Node 2 | 10.136.20.13 |
| `valinor.shire` | Mac Mini M4 | LLM Server (LM Studio + OpenWebUI) | 10.136.20.20 |
| `tuckborough.shire` | Raspberry Pi 5B (8 GB) | Development / General-Purpose | 10.136.20.21 |
| `overhill.shire` | Raspberry Pi B+ | Hello App | 10.136.20.22 |
| `bywater.shire` | Raspberry Pi 2B | Development | 10.136.20.23 |
| `stock.shire` | Raspberry Pi Zero 2W | Development | 10.136.20.24 |
| `buckland.shire` | Orange Pi Zero 3 (4 GB) | Development | 10.136.20.25 |
| `crickhollow.shire` | Orange Pi Zero 3 (1 GB) | Development | 10.136.20.26 |
| `iron-hills.shire` | AMD X570 PC | Personal Workstation | 10.136.50.10 |
| `radagast.shire` | Proxmox VM (Debian 12) | n8n Workflow Automation | 10.136.20.101 |
| `erebor.shire` | Proxmox VM (Debian 12) | GitLab CE | 10.136.20.102 |
| `gondolin.shire` | Raspberry Pi 2B | MQTT IoT Gateway | 10.136.20.x |
| `rivendell.shire` | Proxmox VM (TrueNAS Scale) | NAS / File Storage | 10.136.20.103 |
| `thal.shire` | Proxmox VM (Debian 12) | Heimdall Dashboard | 10.136.20.104 |
| `palantir.shire` | Proxmox VM (Debian 12) | Grafana + Prometheus Monitoring | 10.136.20.105 |
| `khazad-dum.shire` | Proxmox VM (Ubuntu 24.04) | Kernel / Low-Level Development | 10.136.20.106 |
| `weathertop.shire` | Proxmox VM (Home Assistant OS) | Home Automation Hub | 10.136.20.107 / 10.136.30.5 |
| `proudfoot-00..04.shire` | ESP8266 ×5 | IoT Temp/Humidity Sensors | 10.136.30.10–.14 |
| `took-00..01.shire` | Smart Plugs ×2 | IoT Smart Plugs | 10.136.30.20–.21 |
| `bag-end.shire` | Virtual AP (SSID) | Home Wi-Fi 5 GHz, VLAN 20 | — |
| `green-dragon-inn.shire` | Virtual AP (SSID) | IoT Wi-Fi 2.4 GHz, VLAN 30 | — |
| `prancing-pony.shire` | Virtual AP (SSID) | Guest Wi-Fi 2.4 GHz, VLAN 100 | — |

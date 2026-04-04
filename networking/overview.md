[Home](../README.md) › [Networking](README.md) › Overview

# Homelab Network Documentation

> **Last updated:** 2026-03-15  
> **Revision:** 3.0

---

## Table of Contents

- [1 · Network Overview](#1--network-overview)
- [2 · Device Naming Convention](#2--device-naming-convention)
- [3 · OPNsense Interface Layout](#3--opnsense-interface-layout)
- [4 · VLAN Architecture](#4--vlan-architecture)
  - [VLAN Summary](#vlan-summary)
  - [Device-to-VLAN Mapping](#device-to-vlan-mapping)
- [5 · IP Address Assignments](#5--ip-address-assignments)
  - [Homelab LAN — 10.136.20.0/24](#homelab-lan--1013620024)
  - [Workstation — 10.136.50.0/24](#workstation--1013650024)
  - [IoT VLAN 30 — 10.136.30.0/24](#iot-vlan-30--1013630024)
  - [Guest VLAN 100 — 10.136.100.0/24](#guest-vlan-100--10136100024)
- [6 · Physical Network Topology](#6--physical-network-topology)
  - [Proxmox VM Group](#proxmox-vm-group)
- [7 · Switch Port Configuration](#7--switch-port-configuration)
  - [hobbiton.shire — Netgear GS108E](#hobbitonshire--netgear-gs108e)
  - [greenway.shire — Netgear GS308EP](#greenwayshire--netgear-gs308ep)
- [8 · Wireless Networks](#8--wireless-networks)
- [9 · Virtual Machines — Proxmox](#9--virtual-machines--proxmox)
- [10 · IoT Devices — VLAN 30](#10--iot-devices--vlan-30)
- [11 · Client Devices](#11--client-devices)
- [12 · Firewall & Inter-VLAN Routing](#12--firewall--inter-vlan-routing)

---

## 1 · Network Overview

The homelab operates on the **10.136.0.0/16** supernet. All segments are subnets within this space, routed and firewalled by an OPNsense appliance with four physical interfaces. IoT and guest traffic are isolated in dedicated VLANs; server workloads run on a Proxmox hypervisor and a three-node K3s Kubernetes cluster.

| Layer | Hardware | Hostname | Role |
|---|---|---|---|
| WAN | Fiber optic modem | — | ISP uplink |
| Router / Firewall | OPNsense on N150 Mini-PC | `the.shire` | Routing, firewall, DNS, ad-blocking, DHCP |
| Core Switch | Netgear GS108E (8-port managed) | `hobbiton.shire` | Core switching, VLAN trunking |
| PoE Switch | Netgear GS308EP (8-port managed, PoE) | `greenway.shire` | PoE distribution, AP & server uplink |
| Access Point | Zyxel NWA50AX (Wi-Fi 6, OpenWRT) | `bree.shire` | Wireless — three SSIDs across three VLANs |
| Hypervisor | Proxmox VE on N150 Mini-PC | `bill-the-pony.shire` | Virtual machine hosting |
| K3s Master | Cel3867U Mini-PC | `isengard.shire` | Kubernetes control plane |
| K3s Worker 1 | N150 Mini-PC | `rohan.shire` | Kubernetes worker node |
| K3s Worker 2 | N150 Mini-PC | `gondor.shire` | Kubernetes worker node |
| LLM Server | Mac Mini M4 | `valinor.shire` | Local language model inference |
| Workstation | AMD X570 PC | `iron-hills.shire` | Personal workstation, direct OPNsense uplink (port 30) |

---

## 2 · Device Naming Convention

All network-attached devices use a **Tolkien / Middle-earth–inspired** hostname scheme with the `.shire` domain suffix. Hostnames are lowercase and hyphen-separated. IoT devices specifically follow the **Hobbit family surname** convention.

| Category | Hostnames / Pattern |
|---|---|
| Router / firewall | `the.shire` |
| Managed switches | `hobbiton.shire`, `greenway.shire` |
| Access point (physical) | `bree.shire` |
| Wireless SSIDs / virtual APs | `bag-end.shire` (home), `green-dragon-inn.shire` (IoT), `prancing-pony.shire` (guest) |
| Proxmox hypervisor | `bill-the-pony.shire` |
| VMs | `radagast.shire`, `erebor.shire`, `rivendell.shire`, `thal.shire`, `palantir.shire`, `khazad-dum.shire`, `weathertop.shire` |
| Kubernetes cluster nodes | `isengard.shire`, `rohan.shire`, `gondor.shire` |
| LLM server | `valinor.shire` |
| Raspberry Pi devices | `tuckborough.shire`, `overhill.shire`, `bywater.shire`, `stock.shire`, `gondolin.shire` |
| Orange Pi devices | `buckland.shire`, `crickhollow.shire` |
| IoT sensors (ESP8266 ×5) — Proudfoot family | `proudfoot-00.shire` – `proudfoot-04.shire` |
| IoT smart plugs ×2 — Took family | `took-00.shire`, `took-01.shire` |

> **Note:** `bag-end.shire` is reserved for the home Wi-Fi SSID/VAP on `bree.shire`. The Raspberry Pi B+ uses `overhill.shire` to avoid name collision.

---

## 3 · OPNsense Interface Layout

**Hostname:** `the.shire` | **Hardware:** N150 Mini-PC with 4× NIC

The OPNsense appliance exposes four physical network interfaces, labeled by port number:

| Port | Interface Role | Connected To | Subnet | Notes |
|---|---|---|---|---|
| 10 | WAN | Fiber optic modem | DHCP from ISP | Internet uplink |
| 20 | HOMELAB (LAN) | `hobbiton.shire` — core switch | 10.136.20.0/24 | All homelab devices; VLAN 30 + VLAN 100 as tagged sub-interfaces |
| 30 | WORKSTATION | `iron-hills.shire` — direct cable | 10.136.50.0/24 | Personal workstation, no switch; isolated from homelab LAN |
| 40 | DEBUG | *(unconnected)* | 10.136.40.0/24 | Reserved for temporary debugging |

> VLAN 30 (IoT) and VLAN 100 (Guest) are 802.1Q sub-interfaces on port 20. Physical port 30 (workstation) is a separate OPNsense interface unrelated to VLAN 30, and uses subnet 10.136.50.x to avoid ambiguity.

See [opnsense.md](opnsense.md) for detailed OPNsense configuration.

---

## 4 · VLAN Architecture

### VLAN Summary

| VLAN ID | Name | Subnet | Gateway | DHCP Range | Description |
|---|---|---|---|---|---|
| 20 | Homelab | 10.136.20.0/24 | 10.136.20.1 | .150 – .200 | All trusted infrastructure: servers, cluster nodes, SBCs |
| 30 | IoT | 10.136.30.0/24 | 10.136.30.1 | .100 – .199 | IoT sensors and smart-home actuators (Hobbit surnames) |
| 100 | Guest | 10.136.100.0/24 | 10.136.100.1 | .100 – .199 | Untrusted guest Wi-Fi clients, Internet access only |
| — | Workstation | 10.136.50.0/24 | 10.136.50.1 | Static only | Personal workstation, dedicated OPNsense port 30 |

See [vlans.md](vlans.md) for detailed VLAN configuration. A visual VLAN diagram is also available: [vlan-dummy.excalidraw](vlan-dummy.excalidraw).

### Device-to-VLAN Mapping

| Hostname | Device | VLAN |
|---|---|---|
| `the.shire` | OPNsense Router | All (router) |
| `hobbiton.shire` | Netgear GS108E | Homelab (native) |
| `greenway.shire` | Netgear GS308EP | Homelab (native) |
| `bree.shire` | Zyxel NWA50AX | Homelab (mgmt) + trunk to VLAN 30 & 100 |
| `bill-the-pony.shire` | Proxmox Hypervisor | Homelab |
| `radagast.shire` | VM — n8n | Homelab |
| `erebor.shire` | VM — GitLab | Homelab |
| `rivendell.shire` | VM — TrueNAS | Homelab |
| `thal.shire` | VM — Heimdall Dashboard | Homelab |
| `palantir.shire` | VM — Grafana | Homelab |
| `khazad-dum.shire` | VM — Ubuntu KernelDev | Homelab |
| `weathertop.shire` | VM — Home Assistant OS | Homelab (mgmt NIC) + IoT VLAN 30 (IoT NIC) |
| `isengard.shire` | K3s Master | Homelab |
| `rohan.shire` | K3s Worker 1 | Homelab |
| `gondor.shire` | K3s Worker 2 | Homelab |
| `valinor.shire` | Mac Mini M4 | Homelab |
| `tuckborough.shire` | Raspberry Pi 5B (8 GB) | Homelab |
| `overhill.shire` | Raspberry Pi B+ | Homelab |
| `bywater.shire` | Raspberry Pi 2B | Homelab |
| `stock.shire` | Raspberry Pi Zero 2W | Homelab |
| `buckland.shire` | Orange Pi Zero 3 (4 GB) | Homelab |
| `crickhollow.shire` | Orange Pi Zero 3 (1 GB) | Homelab |
| `iron-hills.shire` | Personal workstation (AMD X570) | Workstation (10.136.50.x) |
| `proudfoot-00.shire` – `proudfoot-04.shire` | ESP8266 sensors | IoT VLAN 30 |
| `took-00.shire`, `took-01.shire` | Smart plugs | IoT VLAN 30 |
| Guest devices | — | Guest VLAN 100 |

---

## 5 · IP Address Assignments

> Addresses marked with * are assumed defaults based on the 10.136.x.x convention and should be verified against the actual OPNsense configuration.

### Homelab LAN — 10.136.20.0/24

| Hostname | Device | IP Address | Assignment |
|---|---|---|---|
| `the.shire` | OPNsense (homelab interface) | 10.136.20.1 | Static |
| `hobbiton.shire` | Netgear GS108E | 10.136.20.2 | Static |
| `greenway.shire` | Netgear GS308EP | 10.136.20.3 | Static |
| `bree.shire` | Zyxel NWA50AX | 10.136.20.151 | Static |
| `bill-the-pony.shire` | Proxmox Hypervisor | 10.136.20.100 | Static |
| `isengard.shire` | K3s Master (Cel3867U) | 10.136.20.11 | Static |
| `rohan.shire` | K3s Worker 1 (N150) | 10.136.20.12 | Static |
| `gondor.shire` | K3s Worker 2 (N150) | 10.136.20.13 | Static |
| `valinor.shire` | Mac Mini M4 | 10.136.20.20 | Static |
| `tuckborough.shire` | Raspberry Pi 5B (8 GB) | 10.136.20.21 | Static |
| `overhill.shire` | Raspberry Pi B+ | 10.136.20.22 | Static |
| `bywater.shire` | Raspberry Pi 2B | 10.136.20.23 | Static |
| `stock.shire` | Raspberry Pi Zero 2W | 10.136.20.24 | Static |
| `buckland.shire` | Orange Pi Zero 3 (4 GB) | 10.136.20.25 | Static |
| `crickhollow.shire` | Orange Pi Zero 3 (1 GB) | 10.136.20.26 | Static |
| `radagast.shire` | VM — n8n | 10.136.20.101 | Static |
| `erebor.shire` | VM — GitLab | 10.136.20.102 | Static |
| `rivendell.shire` | VM — TrueNAS | 10.136.20.103 | Static |
| `thal.shire` | VM — Heimdall Dashboard | 10.136.20.104 | Static |
| `palantir.shire` | VM — Grafana | 10.136.20.105 | Static |
| `khazad-dum.shire` | VM — Ubuntu KernelDev | 10.136.20.106 | Static |
| `weathertop.shire` | VM — Home Assistant OS (homelab NIC) | 10.136.20.107 | Static |
| — | DHCP pool | 10.136.20.150 – .200 | DHCP |

### Workstation — 10.136.50.0/24

| Hostname | Device | IP Address | Assignment |
|---|---|---|---|
| `the.shire` | OPNsense (workstation interface) | 10.136.50.1 | Static |
| `iron-hills.shire` | Personal workstation (AMD X570) | 10.136.50.10 | Static |

### IoT VLAN 30 — 10.136.30.0/24

| Hostname | Device | IP Address | Assignment |
|---|---|---|---|
| `the.shire` | OPNsense (VLAN 30 gateway) | 10.136.30.1 | Static |
| `weathertop.shire` | VM — Home Assistant OS (IoT NIC) | 10.136.30.5 | Static |
| `proudfoot-00.shire` | ESP8266 — Server rack temp | 10.136.30.10 | DHCP reserved |
| `proudfoot-01.shire` | ESP8266 — Living room temp/rH | 10.136.30.11 | DHCP reserved |
| `proudfoot-02.shire` | ESP8266 — Bedroom temp/rH | 10.136.30.12 | DHCP reserved |
| `proudfoot-03.shire` | ESP8266 — Bathroom temp/rH | 10.136.30.13 | DHCP reserved |
| `proudfoot-04.shire` | ESP8266 — Kitchen temp/rH | 10.136.30.14 | DHCP reserved |
| `took-00.shire` | Smart plug — Server rack | 10.136.30.20 | DHCP reserved |
| `took-01.shire` | Smart plug — Living room | 10.136.30.21 | DHCP reserved |
| — | DHCP pool | 10.136.30.100 – .199 | DHCP |

### Guest VLAN 100 — 10.136.100.0/24

| Hostname | Device | IP Address | Assignment |
|---|---|---|---|
| `the.shire` | OPNsense (VLAN 100 gateway) | 10.136.100.1 | Static |
| — | Guest DHCP pool | 10.136.100.100 – .199 | DHCP |

---

## 6 · Physical Network Topology

```
                ┌──────────────────┐
                │    INTERNET      │
                └────────┬─────────┘
                         │
                ┌────────┴─────────┐
                │  Fiber Optic     │
                │  Modem           │
                └────────┬─────────┘
                         │ WAN (port 10)
     ┌───────────────────┴──────────────────────────────────────┐
     │                       the.shire                          │
     │         OPNsense Router / Firewall — N150 Mini-PC        │
     │                                                          │
     │  [port 10: WAN]  [port 20: HOMELAB]  [port 30: WS]  [port 40: DEBUG]
     └──────────────────────┬──────────────────────┬────────────┘
                            │ trunk                │ direct
                   10.136.20.1              10.136.50.1
                       (VLAN 30 + 100)             │
                            │                      │
          ┌─────────────────┴──────────────────┐   │
          │           hobbiton.shire           │   │
          │     Netgear GS108E (8-port)        │   │
          │     10.136.20.2                    │   │
          └──┬────┬────┬────┬────┬────┬────┬───┘   │
          P1 │ P2 │ P3 │ P4 │ P5 │ P6 │ P7 │ P8    │
             │    │    │    │    │    │    │       │
             │    │    │    │    │    │    └── greenway.shire (trunk)
             │    │    │    │    │    └── gondor.shire  (K3s W2)  10.136.20.13
             │    │    │    │    └── rohan.shire     (K3s W1)  10.136.20.12
             │    │    │    └── isengard.shire    (K3s M1)  10.136.20.11
             │    │    └── bill-the-pony.shire   (Proxmox)  10.136.20.100
             │    └── tuckborough.shire          (RPi 5B)   10.136.20.21
             └── the.shire uplink (port 20)
                                                    │
          ┌─────────────────────────────────────────┘
          │
          ┌─────────────────────────────────────────────────────┐
          │               greenway.shire                        │
          │     Netgear GS308EP (8-port, PoE)                   │
          │     10.136.20.3                                     │
          └──┬───────────────────────┬──────────────┬───────────┘
          P1 │                    P7 │ (PoE)     P8 │
             │                       │              └── hobbiton.shire (uplink)
             │                       │
             │              ┌────────┴────────────────────────┐
             │              │          bree.shire             │
             │              │  Zyxel NWA50AX Wi-Fi 6 OpenWRT  │
             │              │  10.136.20.151                  │
             │              └────┬──────────────┬──────────┬──┘
             │                   │              │          │
             │         bag-end.shire  green-dragon-   prancing-pony.shire
             │         Home WiFi       inn.shire      Guest WiFi
             │         5 GHz           IoT WiFi       2.4 GHz
             │         (homelab)       2.4 GHz        VLAN 100
             │         10.136.20.x     VLAN 30        10.136.100.x
             │                        10.136.30.x
             │                             │
             │                   ┌─────────┴─────────────────────────┐
             │                   │          IoT VLAN 30               │
             │                   │  proudfoot-00..04  took-00..01     │
             │                   │  10.136.30.10-.14  10.136.30.20-21 │
             │                   └────────────────────────────────────┘
             │
             └── valinor.shire  (Mac Mini M4)  10.136.20.20

iron-hills.shire  (AMD X570 Workstation, 10.136.50.10)  ◄── direct, OPNsense port 30
```

### Proxmox VM Group

```
bill-the-pony.shire  (Proxmox VE, 10.136.20.100)
├── radagast.shire      10.136.20.101   Workflow automation (n8n)
├── erebor.shire        10.136.20.102   Source control (GitLab CE)
├── rivendell.shire     10.136.20.103   NAS / file storage (TrueNAS Scale)
├── thal.shire          10.136.20.104   Service dashboard (Heimdall)
├── palantir.shire      10.136.20.105   Monitoring (Grafana + Prometheus)
├── khazad-dum.shire    10.136.20.106   Kernel / low-level development (Ubuntu)
└── weathertop.shire    10.136.20.107   Home automation hub (Home Assistant OS)
                        10.136.30.5     └── IoT NIC on VLAN 30
```

---

## 7 · Switch Port Configuration

### hobbiton.shire — Netgear GS108E

| Port | Device | Hostname | VLAN Mode | Tagged VLANs | Native VLAN |
|---|---|---|---|---|---|
| 1 | OPNsense LAN | `the.shire` | Trunk | 30, 100 | 20 |
| 2 | Raspberry Pi 5B | `tuckborough.shire` | Access | — | 20 |
| 3 | Proxmox Server | `bill-the-pony.shire` | Trunk | 30 | 20 |
| 4 | K3s Master | `isengard.shire` | Access | — | 20 |
| 5 | K3s Worker 1 | `rohan.shire` | Access | — | 20 |
| 6 | K3s Worker 2 | `gondor.shire` | Access | — | 20 |
| 7 | Netgear GS308EP | `greenway.shire` | Trunk | 30, 100 | 20 |
| 8 | Raspberry Pi B+ | `overhill.shire` | Access | — | 20 |

### greenway.shire — Netgear GS308EP

| Port | Device | Hostname | VLAN Mode | Tagged VLANs | Native VLAN |
|---|---|---|---|---|---|
| 1 | Mac Mini M4 | `valinor.shire` | Access | — | 20 |
| 2 | *(empty)* | — | — | — | — |
| 3 | *(empty)* | — | — | — | — |
| 4 | *(empty)* | — | — | — | — |
| 5 | *(empty)* | — | — | — | — |
| 6 | *(empty)* | — | — | — | — |
| 7 | Zyxel NWA50AX | `bree.shire` | Trunk (PoE) | 30, 100 | 20 |
| 8 | Netgear GS108E | `hobbiton.shire` | Trunk | 30, 100 | 20 |

---

## 8 · Wireless Networks

**Hardware:** Zyxel NWA50AX — Wi-Fi 6 (802.11ax), OpenWRT — `bree.shire` (10.136.20.151)

Three virtual APs are configured on `bree.shire`, each mapped to a different VLAN:

| Virtual AP | SSID | Band | Security | VLAN | Subnet |
|---|---|---|---|---|---|
| `bag-end.shire` | *(home SSID)* | 5 GHz | WPA3-Personal | Homelab (native) | 10.136.20.x |
| `green-dragon-inn.shire` | *(IoT SSID)* | 2.4 GHz | WPA2-Personal | IoT VLAN 30 | 10.136.30.x |
| `prancing-pony.shire` | *(guest SSID)* | 2.4 GHz | WPA2-Personal | Guest VLAN 100 | 10.136.100.x |

> **Firewall rules:**
> - `prancing-pony.shire` (Guest VLAN 100): Internet access only — all homelab traffic blocked.
> - `green-dragon-inn.shire` (IoT VLAN 30): IoT devices communicate with `weathertop.shire` via its IoT NIC at **10.136.30.5** (same L2 segment — no inter-VLAN routing required). All traffic toward the homelab network (10.136.20.x) is blocked by the firewall.
> - `bag-end.shire` (Homelab): full internal access.

See [wireless.md](wireless.md) for detailed wireless configuration.

---

## 9 · Virtual Machines — Proxmox (`bill-the-pony.shire`)

**Hypervisor:** Proxmox VE | **Host:** `bill-the-pony.shire` | **Host IP:** 10.136.20.100

> Resource allocations are estimates; verify against the actual Proxmox configuration.

| VM ID | Hostname | OS | Role | vCPU | RAM | Storage | IP |
|---|---|---|---|---|---|---|---|
| 100 | `radagast.shire` | Debian 12 | Workflow automation — n8n | 2 | 4 GB | 20 GB | 10.136.20.101 |
| 101 | `erebor.shire` | Debian 12 | Source control — GitLab CE | 4 | 8 GB | 100 GB | 10.136.20.102 |
| 102 | `rivendell.shire` | TrueNAS Scale | NAS / file storage | 2 | 8 GB | 500 GB+ | 10.136.20.103 |
| 103 | `thal.shire` | Debian 12 | Service dashboard — Heimdall | 1 | 1 GB | 10 GB | 10.136.20.104 |
| 104 | `palantir.shire` | Debian 12 | Monitoring — Grafana + Prometheus | 2 | 4 GB | 50 GB | 10.136.20.105 |
| 105 | `khazad-dum.shire` | Ubuntu 24.04 LTS | Kernel / low-level development | 4 | 8 GB | 100 GB | 10.136.20.106 |
| 106 | `weathertop.shire` | Home Assistant OS | Home automation & IoT hub | 2 | 4 GB | 32 GB | 10.136.20.107 / 10.136.30.5 |

### VM Notes

- **`weathertop.shire`** has two virtual NICs: one on the homelab network (admin UI, 10.136.20.107) and one on IoT VLAN 30 (10.136.30.5) for subscribing to the MQTT broker on `gondolin.shire` and managing IoT automations.
- **`rivendell.shire`** (TrueNAS Scale) should use PCIe/USB disk pass-through configured in Proxmox for production use.
- **`radagast.shire`** (*the wizard who tends to nature*) handles automated workflows connecting homelab services.
- **`palantir.shire`** (*the far-seeing stone*) aggregates metrics and logs from all servers and the K3s cluster.
- **`khazad-dum.shire`** (*the great dwarven mine*) is the dedicated kernel and low-level development environment.

See [compute/proxmox/vm-overview.md](../compute/proxmox/vm-overview.md) for more detail.

---

## 10 · IoT Devices — VLAN 30

All IoT devices connect via the `green-dragon-inn.shire` SSID (2.4 GHz, VLAN 30, 10.136.30.0/24). Device names follow the **Hobbit family surname** convention. All sensors and smart plugs report via MQTT to `gondolin.shire` (MQTT IoT gateway, Raspberry Pi 2B). Home Assistant on `weathertop.shire` subscribes to the broker.

### Proudfoot Family — Temperature & Humidity Sensors (ESP8266)

| Hostname | Location | Sensors | IP | Protocol |
|---|---|---|---|---|
| `proudfoot-00.shire` | Server rack | Temperature | 10.136.30.10 | MQTT → `gondolin.shire` |
| `proudfoot-01.shire` | Living room | Temperature + Humidity | 10.136.30.11 | MQTT → `gondolin.shire` |
| `proudfoot-02.shire` | Bedroom | Temperature + Humidity | 10.136.30.12 | MQTT → `gondolin.shire` |
| `proudfoot-03.shire` | Bathroom | Temperature + Humidity | 10.136.30.13 | MQTT → `gondolin.shire` |
| `proudfoot-04.shire` | Kitchen | Temperature + Humidity | 10.136.30.14 | MQTT → `gondolin.shire` |

### Took Family — Smart Plugs

| Hostname | Location | Function | IP | Protocol |
|---|---|---|---|---|
| `took-00.shire` | Server rack | Power monitoring & switching | 10.136.30.20 | MQTT → `gondolin.shire` |
| `took-01.shire` | Living room | Power monitoring & switching | 10.136.30.21 | MQTT → `gondolin.shire` |

See [iot/sensors.md](../iot/sensors.md) and [iot/smart-plugs.md](../iot/smart-plugs.md) for full IoT device documentation.

---

## 11 · Client Devices

| Device Type | VLAN | Connection | Notes |
|---|---|---|---|
| Personal laptops | Homelab (native) | Wi-Fi (`bag-end.shire`, 5 GHz) or wired | Static or DHCP |
| Personal smartphones | Homelab (native) | Wi-Fi (`bag-end.shire`, 5 GHz) | DHCP |
| Personal workstation | Workstation (10.136.50.x) | Wired — direct OPNsense port 30 | `iron-hills.shire`, 10.136.50.10 |
| Guest devices | Guest VLAN 100 | Wi-Fi (`prancing-pony.shire`, 2.4 GHz) | Internet only, DHCP |
| IoT sensors / smart plugs | IoT VLAN 30 | Wi-Fi (`green-dragon-inn.shire`, 2.4 GHz) | DHCP reserved |

---

## 12 · Firewall & Inter-VLAN Routing

All inter-VLAN routing is handled by **`the.shire`** (OPNsense). Default policy is **deny all**; explicit allow rules are listed below.

| Source | Destination | Permitted | Notes |
|---|---|---|---|
| Homelab (20) | Internet | ✅ Yes | Full access |
| Homelab (20) | IoT VLAN 30 | ❌ No | No direct homelab access to IoT devices; HA uses its own IoT NIC (10.136.30.5) on the same L2 |
| Homelab (20) | Guest VLAN 100 | ❌ No | — |
| Homelab (20) | Workstation (50) | ✅ Yes | Bi-directional |
| Workstation (50) | Homelab (20) | ✅ Yes | Full access to homelab |
| Workstation (50) | IoT VLAN 30 | ❌ No | Isolated |
| Workstation (50) | Guest VLAN 100 | ❌ No | Isolated |
| Workstation (50) | Internet | ✅ Yes | Full access |
| IoT VLAN 30 | `weathertop.shire` IoT NIC (10.136.30.5) | ✅ (L2) | MQTT — same subnet, no inter-VLAN routing involved |
| IoT VLAN 30 | Homelab (20) | ❌ No | Fully isolated; homelab NIC of `weathertop.shire` (10.136.20.107) not reachable from IoT |
| IoT VLAN 30 | Internet | ✅ Limited | NTP, DNS, OTA firmware updates only |
| IoT VLAN 30 | Workstation (50) | ❌ No | Isolated |
| IoT VLAN 30 | Guest VLAN 100 | ❌ No | Isolated |
| Guest VLAN 100 | Internet | ✅ Yes | Full Internet, DNS via `the.shire` |
| Guest VLAN 100 | All internal | ❌ No | Fully isolated |

See [vlans.md](vlans.md) for planned detailed VLAN expansion documentation.

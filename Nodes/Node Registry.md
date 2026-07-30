---
type: moc
tags:
  - moc
  - nodes
---

# Node Registry

Index of every node in the lab, grouped by segment.

> [!info] This is an index, not the source of truth
> Each node's authoritative facts live in its own note. If a value here
> disagrees with the node note, the node note wins and this table is stale.
> See [[Conventions]].
>
> The `bases` core plugin is enabled, so this table can also be rebuilt as a
> live view over the `type: node` frontmatter if hand-maintenance becomes a
> chore.

## Homelab — 10.136.20.0/24

| Node | Hardware | Role | IP |
|---|---|---|---|
| [[the.shire]] | N150 Mini-PC, 4× NIC | Router, firewall, DNS, DHCP | 10.136.20.1 |
| [[hobbiton.shire]] | Netgear GS108E | Core switch | 10.136.20.2 |
| [[greenway.shire]] | Netgear GS308EP | PoE switch | 10.136.20.3 |
| [[isengard.shire]] | Cel3867U Mini-PC | K3s control plane | 10.136.20.11 |
| [[rohan.shire]] | N150 Mini-PC | K3s worker 1 | 10.136.20.12 |
| [[gondor.shire]] | N150 Mini-PC | K3s worker 2 | 10.136.20.13 |
| [[valinor.shire]] | Mac Mini M4 | LLM inference | 10.136.20.20 |
| [[tuckborough.shire]] | Raspberry Pi 5B (8 GB) | Development | 10.136.20.21 |
| [[overhill.shire]] | Raspberry Pi B+ | Hello App | 10.136.20.22 |
| [[bywater.shire]] | Raspberry Pi 2B | Development | 10.136.20.23 |
| [[stock.shire]] | Raspberry Pi Zero 2W | Development | 10.136.20.24 |
| [[buckland.shire]] | Orange Pi Zero 3 (4 GB) | Development | 10.136.20.25 |
| [[crickhollow.shire]] | Orange Pi Zero 3 (1 GB) | Development | 10.136.20.26 |
| [[bill-the-pony.shire]] | N150 Mini-PC | Proxmox VE hypervisor | 10.136.20.100 |
| [[radagast.shire]] | Proxmox VM 100 · Debian 12 | n8n workflow automation | 10.136.20.101 |
| [[erebor.shire]] | Proxmox VM 101 · Debian 12 | GitLab CE | 10.136.20.102 |
| [[rivendell.shire]] | Proxmox VM 102 · TrueNAS Scale | NAS / file storage | 10.136.20.103 |
| [[thal.shire]] | Proxmox VM 103 · Debian 12 | Heimdall dashboard | 10.136.20.104 |
| [[palantir.shire]] | Proxmox VM 104 · Debian 12 | Prometheus + Grafana | 10.136.20.105 |
| [[khazad-dum.shire]] | Proxmox VM 105 · Ubuntu 24.04 | Kernel development | 10.136.20.106 |
| [[weathertop.shire]] | Proxmox VM 106 · Home Assistant OS | Home automation hub | 10.136.20.107 |
| [[bree.shire]] | Zyxel NWA50AX | Wireless access point | 10.136.20.151 |
| [[gondolin.shire]] | Raspberry Pi 2B | MQTT broker | **unrecorded** |

DHCP pool: 10.136.20.150 – .200.

> [!bug] One gap
> [[gondolin.shire]] has no address on record. See the open questions on that
> note.

## IoT — VLAN 30 — 10.136.30.0/24

| Node | Hardware | Location | IP |
|---|---|---|---|
| [[weathertop.shire]] | Second NIC of VM 106 | — | 10.136.30.5 |
| [[proudfoot-00.shire]] | ESP8266 | Server rack | 10.136.30.10 |
| [[proudfoot-01.shire]] | ESP8266 | Living room | 10.136.30.11 |
| [[proudfoot-02.shire]] | ESP8266 | Bedroom | 10.136.30.12 |
| [[proudfoot-03.shire]] | ESP8266 | Bathroom | 10.136.30.13 |
| [[proudfoot-04.shire]] | ESP8266 | Kitchen | 10.136.30.14 |
| [[took-00.shire]] | Smart plug | Server rack | 10.136.30.20 |
| [[took-01.shire]] | Smart plug | Living room | 10.136.30.21 |

DHCP pool: 10.136.30.100 – .199.

## Workstation — 10.136.50.0/24

| Node | Hardware | Role | IP |
|---|---|---|---|
| [[iron-hills.shire]] | AMD X570 PC | Personal workstation | 10.136.50.10 |

## Guest — VLAN 100 — 10.136.100.0/24

No permanent nodes. DHCP pool 10.136.100.100 – .199, gateway 10.136.100.1 on
[[the.shire]].

## SSIDs

Virtual APs on [[bree.shire]] — named like nodes, but they are radios, not
machines. See [[Wireless]].

| SSID | Band | VLAN |
|---|---|---|
| `bag-end.shire` | 5 GHz | 20 |
| `green-dragon-inn.shire` | 2.4 GHz | 30 |
| `prancing-pony.shire` | 2.4 GHz | 100 |

## Not on the network

| Device | Role |
|---|---|
| TP-Link TL-SG105 | Unmanaged switch, kept for bench testing |
| 12-port patch panel | Cable management, U5 |

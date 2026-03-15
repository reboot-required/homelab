# Hardware Summary

## System Overview

| Device | Hostname | Role | Notes | Idle (W) | Peak (W) | kWh/Year (≈avg) |
|---|---|---|---|---:|---:|---:|
| N150 Mini-PC (Router) | `the.shire` | OPNsense Router, DNS, Ad-blocking | 4× NIC | 6 | 15 | 92 |
| N150 Mini-PC 01 | `bill-the-pony.shire` | Proxmox Hypervisor | | 8 | 30 | 166 |
| Cel3867U Mini-PC | `isengard.shire` | K3s Master Node | | 7 | 25 | 140 |
| N150 Mini-PC 02 | `rohan.shire` | K3s Worker Node 1 | | 8 | 30 | 166 |
| N150 Mini-PC 03 | `gondor.shire` | K3s Worker Node 2 | | 8 | 30 | 166 |
| Netgear GS108E | `hobbiton.shire` | Managed Switch (8-port, Gigabit) | | 5 | 8 | 57 |
| Netgear GS308EP | `greenway.shire` | Managed Switch (8-port, Gigabit, PoE) | | 7 | 10 | 61 |
| Zyxel NWA50AX | `bree.shire` | Wi-Fi 6 Access Point | OpenWRT | 6 | 12 | 79 |
| ESP8266 ×5 | `proudfoot-00..04.shire` | IoT Temperature/Humidity Sensors | VLAN 30 | 0.2 (×1) | 0.5 (×5) | 3 (15) |
| **Total (estimated)** | — | — | — | — | — | **942 kWh/year** |

### Additional Devices

| Device | Hostname | Role | Notes | Idle (W) | Peak (W) | kWh/Year (≈avg) |
|---|---|---|---|---:|---:|---:|
| Mac Mini M4 | `valinor.shire` | LLM Server | | 10 | 50 | 263 |
| Raspberry Pi B+ | `overhill.shire` | Hello App | | 1.5 | 3 | 20 |
| Raspberry Pi 2B | `bywater.shire` | Development | | 2.5 | 5 | 33 |
| Raspberry Pi Zero 2W | `stock.shire` | Development | | 1.5 | 3 | 20 |
| Raspberry Pi 5B (8 GB) | `tuckborough.shire` | Development / general-purpose SBC | | 5 | 12 | 74 |
| Orange Pi Zero 3 (4 GB) | `buckland.shire` | Development | | 2 | 4 | 26 |
| Orange Pi Zero 3 (1 GB) | `crickhollow.shire` | Development | | 1.5 | 3 | 20 |
| AMD X570 PC | `iron-hills.shire` | Personal Workstation | Direct OPNsense port 30 | — | — | — |
| Smart Plugs ×2 | `took-00..01.shire` | IoT Smart Plugs | VLAN 30 | ~0.5 | ~2 | ~13 |
| TP-Link TL-SG105 | — | Unmanaged Switch | Network testing | 3 | 5 | 35 |

---

## Network Overview

- **Router / Firewall**: OPNsense, 4× NIC — `the.shire`
  - Port 10: WAN | Port 20: Homelab (10.136.20.0/24) | Port 30: Workstation (10.136.50.0/24) | Port 40: Debug
- **Switches**:
  - Netgear GS108E (8-port, managed, Gigabit) — `hobbiton.shire`
  - Netgear GS308EP (8-port, managed, PoE, Gigabit) — `greenway.shire`
- **Access Point**: Zyxel NWA50AX (Wi-Fi 6, OpenWRT) — `bree.shire`
  - SSIDs: `bag-end.shire` (5 GHz, homelab), `green-dragon-inn.shire` (2.4 GHz, IoT VLAN 30), `prancing-pony.shire` (2.4 GHz, Guest VLAN 100)
- **Network supernet**: 10.136.0.0/16
- **Cable management**: 0.5U Patch panel

For detailed VLAN configuration, IP assignments, switch port layout, and network topology, see [network-docu.md](network-docu.md).

---

## Rack Layout (9U, 10")

| U | Device | Hostname |
|---|---|---|
| 09 | OPNsense Router | `the.shire` |
| 08 | Raspberry Pi Panel (B+, 2B, Zero 2W) | `overhill.shire`, `bywater.shire`, `stock.shire` |
| 07 | Netgear GS108E — Core Switch | `hobbiton.shire` |
| 06 | Proxmox Server | `bill-the-pony.shire` |
| 05 | 12-Port Patch Panel | — |
| 04 | Netgear GS308EP — PoE Switch | `greenway.shire` |
| 03 | K3s Shelf (`isengard` + `rohan`) | `isengard.shire`, `rohan.shire` |
| 02 | K3s Shelf (`gondor`) | `gondor.shire` |
| 01 | K3s Shelf (reserved) | — |

---

## Future & Extension Plans

- **NAS expansion**: `rivendell.shire` (TrueNAS Scale) already runs as a Proxmox VM; long-term plan is a dedicated physical NAS device with direct disk pass-through for improved performance and redundancy
- **Proxmox upgrade**: Replace N150 Mini-PC with Ryzen 9 mini-PC for increased VM headroom
- **Rack expansion**: Additional U-space for extra patch panels and future devices
- **Additional access points**: Deploy `green-dragon-inn.shire` and `prancing-pony.shire` as physically separate APs for improved whole-home Wi-Fi coverage (currently provided by `bree.shire` as virtual APs)

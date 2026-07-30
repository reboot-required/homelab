---
type: note
tags:
  - infrastructure
  - hardware
---

# Hardware Summary

Every physical device in the lab, with the specification that matters for it.
Per-device detail lives on the node notes; this is the shopping-list view.

## Core infrastructure

Runs 24/7. If one of these is down, something visible breaks.

| Device | Node | Role | Idle | Peak |
|---|---|---|---:|---:|
| N150 Mini-PC, 4× NIC | [[the.shire]] | Router, firewall, DNS | 6 W | 15 W |
| Netgear GS108E | [[hobbiton.shire]] | Core switch, 8× GbE managed | 5 W | 8 W |
| Netgear GS308EP | [[greenway.shire]] | PoE switch, 8× GbE managed | 7 W | 10 W |
| Zyxel NWA50AX | [[bree.shire]] | Wi-Fi 6 AP, OpenWRT | 6 W | 12 W |
| N150 Mini-PC | [[bill-the-pony.shire]] | Proxmox VE hypervisor | 8 W | 30 W |
| Cel3867U Mini-PC | [[isengard.shire]] | K3s control plane | 7 W | 25 W |
| N150 Mini-PC | [[rohan.shire]] | K3s worker 1 | 8 W | 30 W |
| N150 Mini-PC | [[gondor.shire]] | K3s worker 2 | 8 W | 30 W |

## Compute and development

| Device | Node | Role | Idle | Peak |
|---|---|---|---:|---:|
| Mac Mini M4 | [[valinor.shire]] | LLM inference | 10 W | 50 W |
| Raspberry Pi 5B (8 GB) | [[tuckborough.shire]] | Development, Docker host | 5 W | 12 W |
| Raspberry Pi 2B | [[bywater.shire]] | Development | 2.5 W | 5 W |
| Raspberry Pi 2B | [[gondolin.shire]] | MQTT broker | 2.5 W | 5 W |
| Raspberry Pi B+ | [[overhill.shire]] | Hello App | 1.5 W | 3 W |
| Raspberry Pi Zero 2W | [[stock.shire]] | Development | 1.5 W | 3 W |
| Orange Pi Zero 3 (4 GB) | [[buckland.shire]] | Development | 2 W | 4 W |
| Orange Pi Zero 3 (1 GB) | [[crickhollow.shire]] | Development | 1.5 W | 3 W |
| AMD X570 PC | [[iron-hills.shire]] | Personal workstation | — | — |

The workstation is deliberately unmeasured — it is not part of the always-on
budget.

## IoT

| Device | Nodes | Role | Idle | Peak |
|---|---|---|---:|---:|
| ESP8266 ×5 | [[proudfoot-00.shire]] – [[proudfoot-04.shire]] | Temp/humidity sensors | 0.2 W each | 0.5 W each |
| Smart plug ×2 | [[took-00.shire]], [[took-01.shire]] | Power monitoring, switching | ~0.5 W each | ~2 W each |

## Storage

| Device | Where | Configuration |
|---|---|---|
| 2× 2 TB HDD | [[rivendell.shire]] | RAID1 mirror, 2 TB usable |

See [[TrueNAS Scale]] for the caveat about virtualised disks.

## Spares and bench

| Device | Role |
|---|---|
| TP-Link TL-SG105 | Unmanaged 5-port switch, network testing |
| 12-port patch panel | Cable management, rack U5 |
| 0.5U patch panel | Cable management |

## Related

- [[Node Registry]]
- [[Rack Layout]]
- [[Power Budget]]
- [[Future Hardware]]

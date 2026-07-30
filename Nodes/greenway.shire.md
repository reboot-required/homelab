---
type: node
hostname: greenway.shire
ip: 10.136.20.3
vlan: 20
category: network
hardware: Netgear GS308EP (8-port, Gigabit, PoE, managed)
role: PoE distribution switch
power-idle-w: 7
power-peak-w: 10
status: active
tags:
  - node
  - network
  - switch
  - poe
---

# greenway.shire

PoE switch, downstream of [[hobbiton.shire]]. Its reason to exist is powering
[[bree.shire]] over the same cable that trunks its VLANs.

## Port assignment

| Port | Device | Mode | Tagged | Native |
|---|---|---|---|---|
| 1 | [[valinor.shire]] | Access | — | 20 |
| 2–6 | *empty* | — | — | — |
| 7 | [[bree.shire]] | Trunk (PoE) | 30, 100 | 20 |
| 8 | [[hobbiton.shire]] — uplink | Trunk | 30, 100 | 20 |

Five free ports — this is where the homelab grows next.

## Physical

| Property | Value |
|---|---|
| Hardware | Netgear GS308EP, 8× Gigabit, PoE, managed |
| Rack position | U4 — see [[Rack Layout]] |
| Power (idle / peak) | 7 W / 10 W (excluding PoE budget) |

## Related

- [[Switch Ports]]
- [[Wireless]]
- [[Network Topology]]

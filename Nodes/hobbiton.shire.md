---
type: node
hostname: hobbiton.shire
ip: 10.136.20.2
vlan: 20
category: network
hardware: Netgear GS108E (8-port, Gigabit, managed)
role: Core switch
power-idle-w: 5
power-peak-w: 8
status: active
tags:
  - node
  - network
  - switch
---

# hobbiton.shire

The core switch. Everything in the rack lands here, and it carries the VLAN
trunk from [[the.shire]].

## Port assignment

| Port | Device | Mode | Tagged | Native |
|---|---|---|---|---|
| 1 | [[the.shire]] — OPNsense LAN | Trunk | 30, 100 | 20 |
| 2 | [[tuckborough.shire]] | Access | — | 20 |
| 3 | [[bill-the-pony.shire]] | Trunk | 30 | 20 |
| 4 | [[isengard.shire]] | Access | — | 20 |
| 5 | [[rohan.shire]] | Access | — | 20 |
| 6 | [[gondor.shire]] | Access | — | 20 |
| 7 | [[greenway.shire]] | Trunk | 30, 100 | 20 |
| 8 | [[overhill.shire]] | Access | — | 20 |

The switch is full. Any further wired device has to go on [[greenway.shire]].

## Physical

| Property | Value |
|---|---|
| Hardware | Netgear GS108E, 8× Gigabit, managed |
| Rack position | U7 — see [[Rack Layout]] |
| Power (idle / peak) | 5 W / 8 W |

## Related

- [[Switch Ports]]
- [[VLANs]]
- [[Network Topology]]

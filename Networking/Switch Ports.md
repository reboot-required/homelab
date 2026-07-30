---
type: note
tags:
  - networking
  - switching
---

# Switch Ports

Both switches in one place. The authoritative copy of each table is on the
switch's own note — this page exists so you can see the whole fabric at once.

## hobbiton.shire — Netgear GS108E

Core switch. **Full — no free ports.**

| Port | Device | Mode | Tagged | Native |
|---:|---|---|---|---:|
| 1 | [[the.shire]] — OPNsense LAN | Trunk | 30, 100 | 20 |
| 2 | [[tuckborough.shire]] | Access | — | 20 |
| 3 | [[bill-the-pony.shire]] | Trunk | 30 | 20 |
| 4 | [[isengard.shire]] | Access | — | 20 |
| 5 | [[rohan.shire]] | Access | — | 20 |
| 6 | [[gondor.shire]] | Access | — | 20 |
| 7 | [[greenway.shire]] — downlink | Trunk | 30, 100 | 20 |
| 8 | [[overhill.shire]] | Access | — | 20 |

## greenway.shire — Netgear GS308EP

PoE switch. **Five free ports** — this is where the lab grows.

| Port | Device | Mode | Tagged | Native |
|---:|---|---|---|---:|
| 1 | [[valinor.shire]] | Access | — | 20 |
| 2 | *free* | — | — | — |
| 3 | *free* | — | — | — |
| 4 | *free* | — | — | — |
| 5 | *free* | — | — | — |
| 6 | *free* | — | — | — |
| 7 | [[bree.shire]] | Trunk, PoE | 30, 100 | 20 |
| 8 | [[hobbiton.shire]] — uplink | Trunk | 30, 100 | 20 |

## Unaccounted for

| Node | Note |
|---|---|
| [[bywater.shire]], [[stock.shire]] | On the U8 Pi panel; which port they land on is not recorded |
| [[buckland.shire]], [[crickhollow.shire]] | Port not recorded |
| [[gondolin.shire]] | Port not recorded — see its open questions |

With [[hobbiton.shire]] full and only [[overhill.shire]] of the three panel Pis
holding a documented port, these devices must be sharing something undocumented.
Trace the cables and fill this in.

## Related

- [[Network Topology]]
- [[VLANs]]

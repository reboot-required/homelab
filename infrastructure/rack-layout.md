[Home](../README.md) › [Infrastructure](README.md) › Rack Layout

# Rack Layout

> 🚧 This page is a stub. Content to be added.

The homelab uses a **9U 10" rack**. The current device layout is shown below.

---

## Current Layout

```
┌─────────────────────────────────────────────────────┐
│  U  │  Device                    │  Hostname         │
├─────┼────────────────────────────┼───────────────────┤
│  9  │  OPNsense Router           │  the.shire        │
│  8  │  Raspberry Pi Panel        │  overhill.shire   │
│     │  (B+, 2B, Zero 2W)         │  bywater.shire    │
│     │                            │  stock.shire      │
│  7  │  Netgear GS108E Core Switch│  hobbiton.shire   │
│  6  │  Proxmox Server            │  bill-the-pony.shire│
│  5  │  12-Port Patch Panel       │  —                │
│  4  │  Netgear GS308EP PoE Switch│  greenway.shire   │
│  3  │  K3s Shelf                 │  isengard.shire   │
│     │  (isengard + rohan)        │  rohan.shire      │
│  2  │  K3s Shelf (gondor)        │  gondor.shire     │
│  1  │  K3s Shelf (reserved)      │  —                │
└─────┴────────────────────────────┴───────────────────┘
```

---

## Notes

- The rack is a **10" mini-rack** (not a standard 19" rack), suited for compact mini-PCs and single-board computers.
- `valinor.shire` (Mac Mini M4) sits outside the rack on a nearby shelf.
- `tuckborough.shire` (Raspberry Pi 5B) is used for development and is not permanently rack-mounted.
- A **0.5U patch panel** provides cable management between the switches and devices.

---

## Future Plans

- Additional U-space is planned for extra patch panels and future devices.
- See [infrastructure/hardware-summary.md](hardware-summary.md) for full device specs.

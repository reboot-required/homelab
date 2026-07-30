---
type: note
tags:
  - infrastructure
  - rack
---

# Rack Layout

A 9U 10" mini rack — not a 19" rack. Everything in it is a mini-PC, an SBC or an
eight-port switch, which is what makes 10" viable.

```mermaid
flowchart TD
    U9["U9 · OPNsense router — the.shire"]
    U8["U8 · Raspberry Pi panel — overhill.shire · bywater.shire · stock.shire"]
    U7["U7 · Netgear GS108E core switch — hobbiton.shire"]
    U6["U6 · Proxmox VE server — bill-the-pony.shire"]
    U5["U5 · 12-port patch panel"]
    U4["U4 · Netgear GS308EP PoE switch — greenway.shire"]
    U3["U3 · K3s shelf — isengard.shire · rohan.shire"]
    U2["U2 · K3s shelf — gondor.shire"]
    U1["U1 · K3s shelf — reserved"]

    U9 ~~~ U8 ~~~ U7 ~~~ U6 ~~~ U5 ~~~ U4 ~~~ U3 ~~~ U2 ~~~ U1

    classDef net fill:#1f6f8b,stroke:#134b5f,color:#fff
    classDef srv fill:#3d6b35,stroke:#294a24,color:#fff
    classDef pas fill:#5a5a5a,stroke:#3d3d3d,color:#fff
    classDef free fill:none,stroke:#8a8a8a,color:#8a8a8a,stroke-dasharray:4 3

    class U9,U7,U4 net
    class U8,U6,U3,U2 srv
    class U5 pas
    class U1 free
```

## Slot detail

| U | Contents | Nodes |
|---|---|---|
| 9 | OPNsense router | [[the.shire]] |
| 8 | Raspberry Pi panel | [[overhill.shire]], [[bywater.shire]], [[stock.shire]] |
| 7 | Core switch | [[hobbiton.shire]] |
| 6 | Proxmox VE server | [[bill-the-pony.shire]] |
| 5 | 12-port patch panel | — |
| 4 | PoE switch | [[greenway.shire]] |
| 3 | K3s shelf | [[isengard.shire]], [[rohan.shire]] |
| 2 | K3s shelf | [[gondor.shire]] |
| 1 | K3s shelf | *free* |

## Outside the rack

| Node | Why |
|---|---|
| [[valinor.shire]] | Mac Mini M4 on a shelf beside the rack |
| [[bree.shire]] | PoE, wall/ceiling mounted for coverage |
| [[tuckborough.shire]] | Moves around — development board, not permanently mounted |
| [[buckland.shire]], [[crickhollow.shire]] | Orange Pi boards, not panel-mounted |
| [[gondolin.shire]] | Position not recorded |
| [[iron-hills.shire]] | Workstation, at the desk |

## Notes

- A 0.5U patch panel handles cable management between the switches and the
  devices. It shares U5 with the 12-port panel.
- One free U at the bottom, reserved for a fourth K3s node.
- The legacy drawio source is kept at `Assets/server-rack-diagram.drawio` until
  this diagram has been checked against the physical rack.

## Related

- [[Hardware Summary]]
- [[Power Budget]]
- [[Future Hardware]]

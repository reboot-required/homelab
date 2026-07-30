---
type: node
hostname: iron-hills.shire
ip: 10.136.50.10
vlan: none
category: workstation
hardware: AMD X570 PC
role: Personal workstation
status: active
tags:
  - node
  - workstation
---

# iron-hills.shire

The personal workstation. It has its own subnet and its own physical port on the
router — it never touches the homelab switch fabric.

## Network

| Property | Value |
|---|---|
| IP | 10.136.50.10 (static) |
| Subnet | 10.136.50.0/24 |
| Gateway | 10.136.20.1 → 10.136.50.1 on [[the.shire]] |
| Uplink | [[the.shire]] port 30 — direct cable, no switch |

> [!info] Not a VLAN
> This is a separate physical interface on the router, not a tagged VLAN. The
> subnet was deliberately chosen as `.50` rather than `.30` so the workstation
> can never be confused with the IoT VLAN in a firewall rule.

Reaches the homelab in both directions; isolated from IoT and guest. See
[[Firewall Rules]].

## Related

- [[Network Topology]]
- [[Firewall Rules]]

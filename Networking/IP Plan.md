---
type: note
tags:
  - networking
  - addressing
---

# IP Plan

Supernet **10.136.0.0/16**. The third octet is the segment, and it matches the
VLAN ID where there is one.

| Segment | Subnet | VLAN |
|---|---|---:|
| Homelab | 10.136.20.0/24 | 20 |
| IoT | 10.136.30.0/24 | 30 |
| Debug | 10.136.40.0/24 | — |
| Workstation | 10.136.50.0/24 | — |
| Guest | 10.136.100.0/24 | 100 |

The workstation breaks the pattern deliberately — see [[VLANs]].

## Allocation within a /24

| Range | Use |
|---|---|
| .1 | Gateway on [[the.shire]] |
| .2 – .9 | Network equipment |
| .10 – .49 | Bare-metal hosts |
| .100 – .149 | Hypervisor and its guests |
| .150 – .200 | DHCP pool |
| .151+ | Static leases inside the pool range (see below) |

> [!warning] bree.shire sits inside the DHCP pool
> [[bree.shire]] is statically assigned 10.136.20.151, which is inside the
> .150 – .200 pool. It works because the address is also reserved, but it breaks
> the convention above. Moving it to .4, alongside the switches, would be
> tidier.

Per-node addresses are on the node notes and indexed in [[Node Registry]].

## Related

- [[Node Registry]]
- [[VLANs]]
- [[DNS]]
- [[OPNsense]]

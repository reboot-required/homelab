---
type: node
hostname: gondor.shire
ip: 10.136.20.13
vlan: 20
category: compute
hardware: N150 Mini-PC
role: K3s worker
power-idle-w: 8
power-peak-w: 30
status: active
tags:
  - node
  - compute
  - kubernetes
---

# gondor.shire

K3s worker node 2.

## Network

| Property | Value |
|---|---|
| IP | 10.136.20.13 (static) |
| Uplink | [[hobbiton.shire]] port 6 — access, VLAN 20 |

## Physical

| Property | Value |
|---|---|
| Hardware | N150 Mini-PC |
| Rack position | U2 — see [[Rack Layout]] |
| Power (idle / peak) | 8 W / 30 W |

## Cluster

Control plane: [[isengard.shire]]. Sibling worker: [[rohan.shire]].

## Related

- [[K3s Cluster]]
- [[K3s Workloads]]

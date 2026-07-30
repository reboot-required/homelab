---
type: node
hostname: isengard.shire
ip: 10.136.20.11
vlan: 20
category: compute
hardware: Cel3867U Mini-PC
role: K3s control plane
power-idle-w: 7
power-peak-w: 25
status: active
tags:
  - node
  - compute
  - kubernetes
---

# isengard.shire

K3s master node — the control plane of the three-node cluster.

## Network

| Property | Value |
|---|---|
| IP | 10.136.20.11 (static) |
| Uplink | [[hobbiton.shire]] port 4 — access, VLAN 20 |

## Physical

| Property | Value |
|---|---|
| Hardware | Cel3867U Mini-PC |
| Rack position | U3, shared shelf with [[rohan.shire]] — see [[Rack Layout]] |
| Power (idle / peak) | 7 W / 25 W |

## Cluster

Workers: [[rohan.shire]], [[gondor.shire]].

## Related

- [[K3s Cluster]]
- [[K3s Workloads]]
- [[Upgrade K3s]] — runbook

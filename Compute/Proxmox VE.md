---
type: note
tags:
  - compute
  - proxmox
---

# Proxmox VE

The hypervisor, running on [[bill-the-pony.shire]].

| Property | Value |
|---|---|
| Host | [[bill-the-pony.shire]] |
| IP | 10.136.20.100 |
| Hardware | N150 Mini-PC |
| Management UI | `http://10.136.20.100:8006` |
| Guests | 7 — see [[VM Overview]] |

## Networking

The uplink to [[hobbiton.shire]] port 3 is a trunk: native VLAN 20, tagged
VLAN 30. The bridge must therefore be VLAN-aware — that is what lets
[[weathertop.shire]] put a NIC directly on the IoT segment.

## To document

> [!todo] Stub
> - Proxmox VE version and update channel
> - Host CPU, RAM and disk layout
> - VLAN-aware bridge configuration
> - Storage pools: what is local, what is thin-provisioned, what is on
>   [[rivendell.shire]]
> - Users, roles and API tokens (structure only — no secrets)
> - Whether a cluster is planned, or this stays a single node

## Runbooks

- [[Create Proxmox VM]]
- [[Add Disk Passthrough]]

## Related

- [[VM Overview]]
- [[Proxmox Backups]]
- [[Future Hardware]]

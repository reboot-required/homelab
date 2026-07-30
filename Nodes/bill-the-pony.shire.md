---
type: node
hostname: bill-the-pony.shire
ip: 10.136.20.100
vlan: 20
category: compute
hardware: N150 Mini-PC
os: Proxmox VE
role: Hypervisor
power-idle-w: 8
power-peak-w: 30
status: active
tags:
  - node
  - compute
  - proxmox
---

# bill-the-pony.shire

The hypervisor. Seven VMs ride on this one N150 mini-PC — hence the name: the
pony carries the luggage.

## Runs

| VM ID | Guest | Role |
|---|---|---|
| 100 | [[radagast.shire]] | Workflow automation — [[n8n]] |
| 101 | [[erebor.shire]] | Source control — [[GitLab CE]] |
| 102 | [[rivendell.shire]] | NAS — [[TrueNAS Scale]] |
| 103 | [[thal.shire]] | Dashboard — [[Heimdall]] |
| 104 | [[palantir.shire]] | Monitoring — [[Prometheus]] + [[Grafana]] |
| 105 | [[khazad-dum.shire]] | Kernel development |
| 106 | [[weathertop.shire]] | Home automation — [[Home Assistant]] |

## Network

| Property | Value |
|---|---|
| IP | 10.136.20.100 (static) |
| Uplink | [[hobbiton.shire]] port 3 |
| Trunk | Native VLAN 20, tagged VLAN 30 |
| Management UI | `http://10.136.20.100:8006` |

VLAN 30 is tagged on this uplink so [[weathertop.shire]] can put its second NIC
directly on the IoT segment.

## Physical

| Property | Value |
|---|---|
| Hardware | N150 Mini-PC |
| Rack position | U6 — see [[Rack Layout]] |
| Power (idle / peak) | 8 W / 30 W |

> [!info] Planned upgrade
> Replace with a Ryzen 9 mini-PC for VM headroom. See [[Future Hardware]].

## Related

- [[Proxmox VE]] — hypervisor configuration
- [[VM Overview]] — resource allocation
- [[Create Proxmox VM]] — runbook

---
type: note
tags:
  - compute
  - proxmox
  - vm
---

# VM Overview

All seven guests of [[bill-the-pony.shire]].

> [!info] Estimates
> Allocations below are the documented intent. Verify against the live Proxmox
> configuration before relying on them for capacity planning.

| ID | Node | OS | Role | vCPU | RAM | Disk |
|---:|---|---|---|---:|---:|---:|
| 100 | [[radagast.shire]] | Debian 12 | [[n8n]] | 1 | 2 GB | 20 GB |
| 101 | [[erebor.shire]] | Debian 12 | [[GitLab CE]] | 2 | 4 GB | 100 GB |
| 102 | [[rivendell.shire]] | TrueNAS Scale | [[TrueNAS Scale]] | 2 | 4 GB | 500 GB+ |
| 103 | [[thal.shire]] | Debian 12 | [[Heimdall]] | 1 | 1 GB | 10 GB |
| 104 | [[palantir.shire]] | Debian 12 | [[Prometheus]] + [[Grafana]] | 1 | 2 GB | 50 GB |
| 105 | [[khazad-dum.shire]] | Ubuntu 24.04 LTS | Kernel development | 4 | 8 GB | 100 GB |
| 106 | [[weathertop.shire]] | Home Assistant OS | [[Home Assistant]] | 1 | 2 GB | 32 GB |
| | | | **Total** | **12** | **23 GB** | **~800 GB** |

> [!warning] The host is oversubscribed
> Twelve vCPU and 23 GB allocated on one N150 mini-PC. CPU oversubscription is
> normal and fine — these workloads are idle most of the time. Memory is the
> real constraint, and [[khazad-dum.shire]] alone claims 8 GB of it. This is the
> argument for the host upgrade in [[Future Hardware]].

## Notes

**[[weathertop.shire]]** has two NICs: homelab (10.136.20.107) and IoT VLAN 30
(10.136.30.5). VLAN 30 must be tagged on the hypervisor's uplink for this to
work — see [[Switch Ports]].

**[[rivendell.shire]]** should use PCIe or USB disk pass-through before it is
treated as production storage. See [[Add Disk Passthrough]].

**[[khazad-dum.shire]]** is the only guest sized for a real workload rather than
a service. Kernel builds want the cores.

## Related

- [[Proxmox VE]]
- [[Create Proxmox VM]]
- [[Proxmox Backups]]

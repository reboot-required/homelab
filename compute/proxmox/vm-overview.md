[Home](../../README.md) › [Compute](../README.md) › [Proxmox](README.md) › VM Overview

# VM Overview

> 🚧 This page is a stub. Content to be added.

All virtual machines hosted on `bill-the-pony.shire` (Proxmox VE, 10.136.20.100).

> Resource allocations are estimates; verify against the actual Proxmox configuration.

---

## VM Table

| VM ID | Hostname | OS | Role | vCPU | RAM | Storage | IP |
|---|---|---|---|---|---|---|---|
| 100 | `radagast.shire` | Debian 12 | Workflow automation — n8n | 2 | 4 GB | 20 GB | 10.136.20.101 |
| 101 | `erebor.shire` | Debian 12 | Source control — GitLab CE | 4 | 8 GB | 100 GB | 10.136.20.102 |
| 102 | `rivendell.shire` | TrueNAS Scale | NAS / file storage | 2 | 8 GB | 500 GB+ | 10.136.20.103 |
| 103 | `thal.shire` | Debian 12 | Service dashboard — Heimdall | 1 | 1 GB | 10 GB | 10.136.20.104 |
| 104 | `palantir.shire` | Debian 12 | Monitoring — Grafana + Prometheus | 2 | 4 GB | 50 GB | 10.136.20.105 |
| 105 | `khazad-dum.shire` | Ubuntu 24.04 LTS | Kernel / low-level development | 4 | 8 GB | 100 GB | 10.136.20.106 |
| 106 | `weathertop.shire` | Home Assistant OS | Home automation & IoT hub | 2 | 4 GB | 32 GB | 10.136.20.107 / 10.136.30.5 |

---

## Notes

- **`weathertop.shire`** has two virtual NICs: homelab (10.136.20.107) and IoT VLAN 30 (10.136.30.5).
- **`rivendell.shire`** should use PCIe/USB disk pass-through for production NAS performance.
- See [backup-strategy.md](backup-strategy.md) for snapshot and retention policy.

### Planned Resource Review for the Hardware Refresh

- Revisit the CPU and RAM allocation for `khazad-dum.shire` once the Ryzen 5 5600X host is in production.
- Confirm whether any Raspberry Pi-hosted workloads are consolidated into existing VMs or new VMs during the migration.
- If the Proxmox host keeps the `bill-the-pony.shire` identity, update only the hardware notes; if it changes hostname, update this page after [node-registry.md](../../infrastructure/node-registry.md).

[Home](../../README.md) › [Compute](../README.md) › Proxmox

# Proxmox VE

> 🚧 This page is a stub. Content to be added.

**Host:** `bill-the-pony.shire` | **IP:** 10.136.20.100  
**Hardware:** N150 Mini-PC  
**Hypervisor:** Proxmox VE  
**Management UI:** `http://10.136.20.100:8006`

---

## Pages

| Page | Description |
|---|---|
| [VM Overview](vm-overview.md) | All VMs: ID, hostname, role, resource allocation |
| [Backup Strategy](backup-strategy.md) | Snapshot schedule and retention policy |
| **Runbooks** | |
| [Create VM](runbooks/create-vm.md) | Step-by-step: create a new VM |
| [Add Disk Passthrough](runbooks/add-disk-passthrough.md) | Step-by-step: pass a physical disk to a VM |
| [Add an Additional Proxmox Host](runbooks/add-proxmox-host.md) | Planning checklist for the incoming Ryzen-based Proxmox node |

---

## Incoming Hardware Refresh

An infrastructure upgrade is planned for this category: a new **AMD Ryzen 5 5600X on an A520 mini-ITX mainboard** will be added to the rack as a second Proxmox platform alongside `bill-the-pony.shire`.

- **Host OS:** Proxmox VE
- **Primary goal:** provide dedicated headroom for the heavyweight kernel-build workload currently associated with `khazad-dum.shire`
- **Current VM estate:** existing VMs remain on `bill-the-pony.shire`
- **Hostname:** still to be assigned; choose a Tolkien-themed hostname before updating the node registry
- **Rack impact:** all Raspberry Pi systems will be removed from permanent rack residency
- **Planning runbook:** [runbooks/add-proxmox-host.md](runbooks/add-proxmox-host.md)

Until the cutover is complete, the live details at the top of this page still describe the currently deployed Proxmox environment.

---

## Planned Content

- Proxmox VE version and configuration overview
- Hardware specs: CPU, RAM, storage
- Network bridge configuration (VLAN-aware bridge)
- Storage pools and configuration
- User and permission management
- Cluster plans (future)

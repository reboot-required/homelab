[Home](../README.md) › [Storage](README.md) › Backup Strategy

# Backup Strategy

> 🚧 This page is a stub. Content to be added.

---

## Overview

The homelab uses a **layered backup strategy**:

1. **Proxmox VM snapshots** — fast, on-hypervisor recovery for all VMs on `bill-the-pony.shire`
2. **TrueNAS RAID1** — `rivendell.shire` provides local disk redundancy (2× 2 TB mirror)
3. **Cold storage** — periodic offline backups to external HDDs for disaster recovery

---

## Planned Content

- Proxmox backup schedule (frequency, retention policy per VM)
- TrueNAS dataset snapshot schedule
- Cold storage rotation procedure
- Recovery time objectives (RTO) and recovery point objectives (RPO)
- Critical data inventory (what must be backed up)
- Restoration testing procedure

---

## See Also

- [truenas.md](truenas.md) — TrueNAS storage configuration
- [compute/proxmox/backup-strategy.md](../compute/proxmox/backup-strategy.md) — Proxmox-specific backup config

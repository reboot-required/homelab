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

## Hardware Migration Considerations

The planned Proxmox hardware refresh adds a new dependency to the backup strategy: enough validated recovery coverage to bring the incoming **AMD Ryzen 5 5600X / A520 mini-ITX** platform online and migrate `khazad-dum.shire` without disrupting the existing VM estate on `bill-the-pony.shire`.

- Treat Proxmox snapshots as short-term migration checkpoints, not the only recovery copy.
- Verify that `khazad-dum.shire` is recoverable before migration and that the existing `bill-the-pony.shire` backups remain healthy during the split-host transition.
- If any Raspberry Pi-hosted workloads are retired or virtualized, update the critical data inventory to reflect their new storage location.
- Mirror final migration notes in [compute/proxmox/backup-strategy.md](../compute/proxmox/backup-strategy.md) so Proxmox-specific and platform-wide backup guidance stay aligned.

---

## See Also

- [truenas.md](truenas.md) — TrueNAS storage configuration
- [compute/proxmox/backup-strategy.md](../compute/proxmox/backup-strategy.md) — Proxmox-specific backup config

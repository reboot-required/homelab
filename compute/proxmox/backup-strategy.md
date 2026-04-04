[Home](../../README.md) › [Compute](../README.md) › [Proxmox](README.md) › Backup Strategy

# Proxmox Backup Strategy

> 🚧 This page is a stub. Content to be added.

---

## Overview

Proxmox VE provides native VM snapshot and backup capabilities. All VMs on `bill-the-pony.shire` are covered by a scheduled backup policy.

---

## Planned Content

- Scheduled backup configuration (Proxmox Backup Server or local storage)
- Snapshot schedule per VM (frequency, retention count)
- Off-site / cold storage strategy
- Restoration procedure
- Integration with [storage/backup.md](../../storage/backup.md) for full backup strategy

---

## See Also

- [storage/truenas.md](../../storage/truenas.md) — TrueNAS RAID1 storage
- [storage/backup.md](../../storage/backup.md) — full backup strategy

---
type: note
tags:
  - compute
  - proxmox
  - backup
---

# Proxmox Backups

The hypervisor-side layer of [[Backup Strategy]].

Proxmox VE can snapshot and back up every guest on [[bill-the-pony.shire]]
natively. That covers fast recovery from a bad change — and nothing else, since
snapshots stored on the hypervisor die with the hypervisor.

## To document

> [!todo] Stub
> - Backup target: local storage, an NFS share on [[rivendell.shire]], or a
>   Proxmox Backup Server
> - Schedule and retention per VM — the seven guests do not all deserve the same
>   frequency
> - Whether backups are verified after they are written
> - Restore procedure, and when it was last actually tested

## Related

- [[Backup Strategy]] — the full picture
- [[VM Overview]]
- [[TrueNAS Scale]]

---
type: moc
tags:
  - moc
  - storage
---

# Storage

## Pages

- [[TrueNAS Scale]] — the NAS, and the caveat about running ZFS in a VM
- [[Backup Strategy]] — the three layers and what each actually protects

## Where data lives

| Data | Where |
|---|---|
| VM disks | [[bill-the-pony.shire]] local storage |
| File shares | [[rivendell.shire]] — 2 TB mirror |
| Git repositories | [[erebor.shire]] — 100 GB VM disk |
| Metrics | [[palantir.shire]] — 50 GB VM disk |
| Cold backups | External HDDs, offline |

## Related

- [[Proxmox Backups]]
- [[Add Disk Passthrough]]
- [[Future Hardware]]

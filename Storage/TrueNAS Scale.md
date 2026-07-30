---
type: note
tags:
  - storage
  - truenas
  - zfs
---

# TrueNAS Scale

File storage for the lab, running as a VM.

| Property | Value |
|---|---|
| Host | [[rivendell.shire]] — VM 102 on [[bill-the-pony.shire]] |
| IP | 10.136.20.103 |
| Disks | 2× 2 TB HDD, RAID1 mirror |
| Usable | 2 TB |

## The virtualisation problem

ZFS is built on the assumption that it owns the physical disks — it wants to see
SMART data, handle write barriers and control caching itself. Inside a VM on top
of the Proxmox storage layer, it sees none of that. Errors it would normally
detect and repair can be masked or invented by the layer underneath.

| Option | Effect |
|---|---|
| Disk pass-through — [[Add Disk Passthrough]] | ZFS gets the real disks. No new hardware. |
| Dedicated physical NAS — [[Future Hardware]] | Storage survives the hypervisor. |

Until one of those happens, treat the mirror as *convenience redundancy*, not as
a backup. The distinction matters — see [[Backup Strategy]].

## To document

> [!todo] Stub
> - Pool name, vdev layout, ashift
> - Datasets and what each holds
> - SMB and NFS shares, and which nodes mount them
> - Snapshot schedule and retention per dataset
> - Replication targets, if any
> - Permissions model
> - SMART monitoring and where the alerts go

## Related

- [[rivendell.shire]]
- [[Backup Strategy]]
- [[Add Disk Passthrough]]

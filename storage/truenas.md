[Home](../README.md) › [Storage](README.md) › TrueNAS

# TrueNAS Scale

> 🚧 This page is a stub. Content to be added.

**Host:** `rivendell.shire` | **IP:** 10.136.20.103  
**VM ID:** 102 on `bill-the-pony.shire`  
**OS:** TrueNAS Scale  
**Role:** NAS / File Storage

---

## Storage Configuration

- **Disks:** 2× 2 TB HDDs in **RAID1** (mirror) — provides redundancy with 2 TB usable capacity
- **Disk access:** PCIe/USB disk pass-through from Proxmox (planned for production)

---

## Planned Content

- ZFS pool configuration (pool name, RAID type, disk layout)
- Datasets and their purposes
- SMB / NFS share configuration
- Snapshot schedule and retention
- Replication (if applicable)
- Access control and permissions
- SMART monitoring and disk health

---

## See Also

- [backup.md](backup.md) — full backup strategy
- [compute/proxmox/runbooks/add-disk-passthrough.md](../compute/proxmox/runbooks/add-disk-passthrough.md) — disk passthrough setup

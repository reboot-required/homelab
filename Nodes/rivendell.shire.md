---
type: node
hostname: rivendell.shire
ip: 10.136.20.103
vlan: 20
category: vm
hardware: Proxmox VM 102 on bill-the-pony.shire
os: TrueNAS Scale
role: NAS / file storage
vcpu: 2
ram-gb: 4
disk-gb: 500
status: active
tags:
  - node
  - vm
  - storage
---

# rivendell.shire

*The last homely house* — file storage for the lab. TrueNAS Scale on 2× 2 TB in
a mirror.

## Host

Guest of [[bill-the-pony.shire]], VM ID 102.

## Resources

| Property | Value |
|---|---|
| vCPU | 2 |
| RAM | 4 GB |
| Disk | 500 GB+ |
| IP | 10.136.20.103 (static) |

> [!warning] Virtualised storage
> Running ZFS inside a VM on top of the Proxmox storage layer means ZFS cannot
> see the physical disks it thinks it is managing. Disk pass-through is a
> prerequisite for treating this as production storage — see
> [[Add Disk Passthrough]]. Long term this should be a dedicated physical NAS,
> see [[Future Hardware]].

## Runs

- [[TrueNAS Scale]]

## Related

- [[Backup Strategy]]
- [[VM Overview]]

---
type: node
hostname: khazad-dum.shire
ip: 10.136.20.106
vlan: 20
category: vm
hardware: Proxmox VM 105 on bill-the-pony.shire
os: Ubuntu 24.04 LTS
role: Kernel and low-level development
vcpu: 4
ram-gb: 8
disk-gb: 100
status: active
tags:
  - node
  - vm
  - development
---

# khazad-dum.shire

*The great dwarven mine* — digging deep. The dedicated environment for kernel
and low-level development work.

## Host

Guest of [[bill-the-pony.shire]], VM ID 105.

## Resources

| Property | Value |
|---|---|
| vCPU | 4 |
| RAM | 8 GB |
| Disk | 100 GB |
| IP | 10.136.20.106 (static) |

The heaviest allocation on the hypervisor — kernel builds are the one workload
in this lab that genuinely wants four cores.

## Related

- [[VM Overview]]
- [[Compute]]

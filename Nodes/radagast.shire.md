---
type: node
hostname: radagast.shire
ip: 10.136.20.101
vlan: 20
category: vm
hardware: Proxmox VM 100 on bill-the-pony.shire
os: Debian 12
role: Workflow automation
vcpu: 1
ram-gb: 2
disk-gb: 20
status: active
tags:
  - node
  - vm
  - automation
---

# radagast.shire

*The wizard who tends to nature* — the VM that tends to everything else. Runs
[[n8n]], which glues the homelab services together.

## Host

Guest of [[bill-the-pony.shire]], VM ID 100.

## Resources

| Property | Value |
|---|---|
| vCPU | 1 |
| RAM | 2 GB |
| Disk | 20 GB |
| IP | 10.136.20.101 (static) |

## Runs

- [[n8n]] — `http://10.136.20.101:5678`

## Related

- [[VM Overview]]
- [[Automation]]

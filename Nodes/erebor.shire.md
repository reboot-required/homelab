---
type: node
hostname: erebor.shire
ip: 10.136.20.102
vlan: 20
category: vm
hardware: Proxmox VM 101 on bill-the-pony.shire
os: Debian 12
role: Source control and CI
vcpu: 2
ram-gb: 4
disk-gb: 100
status: active
tags:
  - node
  - vm
  - git
---

# erebor.shire

*The Lonely Mountain* — the hoard. Every homelab repository lives here.

## Host

Guest of [[bill-the-pony.shire]], VM ID 101.

## Resources

| Property | Value |
|---|---|
| vCPU | 2 |
| RAM | 4 GB |
| Disk | 100 GB |
| IP | 10.136.20.102 (static) |

The largest disk allocation of any VM — GitLab's repositories, artefacts and
container images all land on it.

## Runs

- [[GitLab CE]] — `http://10.136.20.102`

CI jobs do *not* run here. The GitLab Runner is a workload on the K3s cluster —
see [[GitLab CI]].

## Related

- [[VM Overview]]
- [[K3s Workloads]]

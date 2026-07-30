---
type: node
hostname: thal.shire
ip: 10.136.20.104
vlan: 20
category: vm
hardware: Proxmox VM 103 on bill-the-pony.shire
os: Debian 12
role: Service dashboard
vcpu: 1
ram-gb: 1
disk-gb: 10
status: active
tags:
  - node
  - vm
  - dashboard
---

# thal.shire

The lab's front door. Runs [[Heimdall]], the bookmark-style index of every other
service.

## Host

Guest of [[bill-the-pony.shire]], VM ID 103.

## Resources

| Property | Value |
|---|---|
| vCPU | 1 |
| RAM | 1 GB |
| Disk | 10 GB |
| IP | 10.136.20.104 (static) |

The smallest VM in the lab, and deliberately so — it serves one static page.

## Runs

- [[Heimdall]] — `http://10.136.20.104`

## Related

- [[VM Overview]]
- [[Services]]

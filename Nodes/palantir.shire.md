---
type: node
hostname: palantir.shire
ip: 10.136.20.105
vlan: 20
category: vm
hardware: Proxmox VM 104 on bill-the-pony.shire
os: Debian 12
role: Monitoring
vcpu: 1
ram-gb: 2
disk-gb: 50
status: active
tags:
  - node
  - vm
  - monitoring
---

# palantir.shire

*The far-seeing stone.* Scrapes and visualises metrics from every other node.

## Host

Guest of [[bill-the-pony.shire]], VM ID 104.

## Resources

| Property | Value |
|---|---|
| vCPU | 1 |
| RAM | 2 GB |
| Disk | 50 GB |
| IP | 10.136.20.105 (static) |

The 50 GB disk is time-series retention, not application size — revisit it when
[[Prometheus]] scrape targets are expanded to all nodes.

## Runs

- [[Prometheus]] — `http://10.136.20.105:9090`
- [[Grafana]] — `http://10.136.20.105:3000`

## Related

- [[Monitoring Stack]]
- [[VM Overview]]

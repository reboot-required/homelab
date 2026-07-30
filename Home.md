---
type: moc
tags:
  - moc
  - home
---

# The Shire

Documentation for a self-hosted homelab named after Middle-earth, on the
`.shire` domain. Start here.

## Categories

| | |
|---|---|
| [[Infrastructure]] | Hardware, rack, power |
| [[Networking]] | Topology, VLANs, firewall, DNS, wireless |
| [[Compute]] | Proxmox VE and the K3s cluster |
| [[Storage]] | TrueNAS and backups |
| [[Services]] | Everything self-hosted |
| [[IoT]] | Sensors, plugs, MQTT |
| [[Monitoring]] | Prometheus, Grafana, alerting |
| [[Automation]] | CI/CD and configuration management |
| [[Runbooks]] | Procedures |
| [[Journal]] | Lab diary |

## Quick reference

- [[Node Registry]] — every machine, grouped by segment
- [[Network Topology]] — how it is all wired
- [[Firewall Rules]] — what may talk to what
- [[Changelog]] — dated infrastructure changes
- [[Conventions]] — how this vault is written

## The lab in one paragraph

An OPNsense router ([[the.shire]]) fronts a 9U 10" rack holding two managed
switches, a Proxmox hypervisor with seven guests, and a three-node K3s cluster.
A Mac Mini does local LLM inference, a handful of SBCs do development, and seven
IoT devices live on an isolated VLAN talking MQTT to Home Assistant. Roughly
1 400 kWh a year — see [[Power Budget]].

## Known open questions

Things this documentation says that cannot all be true at once. Each is tracked
on the note where it bites:

| Question | Where |
|---|---|
| The MQTT path crosses a boundary the firewall denies | [[gondolin.shire]], [[MQTT]] |
| The MQTT broker has no recorded IP or switch port | [[gondolin.shire]] |
| The core switch is full, but four SBCs claim ports on it | [[Switch Ports]] |
| Prometheus is documented as both a VM service and a K3s workload | [[K3s Workloads]] |
| Node exporters are planned everywhere, deployed nowhere | [[Monitoring Stack]] |
| `bree.shire` is statically addressed inside the DHCP pool | [[IP Plan]] |
| No service records how its data is backed up | [[Backup Strategy]] |

## Related

- [[Future Hardware]] — planned hardware
- [[Future Services]] — planned services

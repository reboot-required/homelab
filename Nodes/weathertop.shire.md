---
type: node
hostname: weathertop.shire
ip: 10.136.20.107
ip-iot: 10.136.30.5
vlan: 20, 30
category: vm
hardware: Proxmox VM 106 on bill-the-pony.shire
os: Home Assistant OS
role: Home automation hub
vcpu: 1
ram-gb: 2
disk-gb: 32
status: active
tags:
  - node
  - vm
  - iot
  - home-assistant
---

# weathertop.shire

*The watchtower* — it watches the house. The only node with a foot in two
networks.

## Host

Guest of [[bill-the-pony.shire]], VM ID 106.

## Resources

| Property | Value |
|---|---|
| vCPU | 1 |
| RAM | 2 GB |
| Disk | 32 GB |
| IP (homelab) | 10.136.20.107 (static) |
| IP (IoT VLAN 30) | 10.136.30.5 (static) |

## Dual-homing

| NIC | VLAN | Address | Purpose |
|---|---|---|---|
| `eth0` | 20 | 10.136.20.107 | Admin UI, reachable from the homelab |
| `eth1` | 30 | 10.136.30.5 | MQTT traffic, same L2 as the IoT devices |

> [!info] Why two NICs instead of a firewall rule
> Putting a second NIC directly on VLAN 30 means IoT traffic never has to be
> routed across a VLAN boundary at all. The firewall keeps a blanket deny
> between VLAN 30 and VLAN 20 and nothing has to be punched through it — see
> [[Firewall Rules]].

## Runs

- [[Home Assistant]] — `http://10.136.20.107:8123`

Subscribes to the MQTT broker on [[gondolin.shire]].

## Related

- [[MQTT]]
- [[IoT]]
- [[VM Overview]]

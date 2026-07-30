---
type: service
host: "[[weathertop.shire]]"
url: http://10.136.20.107:8123
port: 8123
deployment: proxmox-vm
status: running
tags:
  - service
  - iot
  - home-automation
---

# Home Assistant

The home automation hub. Consumes every sensor and controls every plug in the
lab.

## Access

| Property | Value |
|---|---|
| Internal URL | `http://10.136.20.107:8123` |
| Port | 8123 |
| Host | [[weathertop.shire]] — VM 106, Home Assistant OS |

## Network position

Two NICs, and that is the whole design:

| NIC | VLAN | Address | Purpose |
|---|---:|---|---|
| `eth0` | 20 | 10.136.20.107 | Admin UI, reachable from the homelab |
| `eth1` | 30 | 10.136.30.5 | Same L2 as the IoT devices |

Because the IoT-facing interface is *inside* VLAN 30, no traffic between Home
Assistant and the sensors is ever routed, and [[Firewall Rules]] can keep an
unqualified deny between VLAN 30 and VLAN 20.

## Dependencies

- [[MQTT]] broker on [[gondolin.shire]]
- [[proudfoot-00.shire]] – [[proudfoot-04.shire]] — sensors
- [[took-00.shire]], [[took-01.shire]] — plugs

## To document

> [!todo] Stub
> - Configured automations — none are written down
> - MQTT integration configuration
> - Which entities exist, and their naming
> - Backup: HA configuration and history are on the [[Backup Strategy]] critical
>   list. HA's own backup feature writes locally by default — record where the
>   copies actually go.

## Related

- [[weathertop.shire]]
- [[IoT]]
- [[MQTT]]

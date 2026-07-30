---
type: node
hostname: took-01.shire
ip: 10.136.30.21
vlan: 30
category: iot
hardware: Smart plug
role: Power monitoring and switching — living room
status: active
tags:
  - node
  - iot
  - smart-plug
---

# took-01.shire

Smart plug in the living room — power monitoring and remote switching. Took family —
see [[Conventions]].

## Network

| Property | Value |
|---|---|
| IP | 10.136.30.21 (DHCP reservation) |
| VLAN | 30 — IoT |
| SSID | `green-dragon-inn.shire` on [[bree.shire]] |

## Telemetry

Publishes power draw over MQTT to [[gondolin.shire]]; consumed by
[[Home Assistant]] on [[weathertop.shire]] and graphed in [[Grafana]].

## Related

- [[Smart Plugs]]
- [[MQTT]]

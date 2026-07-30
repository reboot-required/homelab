---
type: node
hostname: took-00.shire
ip: 10.136.30.20
vlan: 30
category: iot
hardware: Smart plug
role: Power monitoring and switching — server rack
status: active
tags:
  - node
  - iot
  - smart-plug
---

# took-00.shire

Smart plug in the server rack — power monitoring and remote switching. Took family —
see [[Conventions]].

## Network

| Property | Value |
|---|---|
| IP | 10.136.30.20 (DHCP reservation) |
| VLAN | 30 — IoT |
| SSID | `green-dragon-inn.shire` on [[bree.shire]] |

## Telemetry

Publishes power draw over MQTT to [[gondolin.shire]]; consumed by
[[Home Assistant]] on [[weathertop.shire]] and graphed in [[Grafana]].

## Related

- [[Smart Plugs]]
- [[MQTT]]

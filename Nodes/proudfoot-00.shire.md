---
type: node
hostname: proudfoot-00.shire
ip: 10.136.30.10
vlan: 30
category: iot
hardware: ESP8266
role: Temperature sensor — server rack
status: active
tags:
  - node
  - iot
  - sensor
---

# proudfoot-00.shire

Temperature sensor in the server rack. Proudfoot family — see [[Conventions]].

## Network

| Property | Value |
|---|---|
| IP | 10.136.30.10 (DHCP reservation) |
| VLAN | 30 — IoT |
| SSID | `green-dragon-inn.shire` on [[bree.shire]] |

## Telemetry

Publishes over MQTT to [[gondolin.shire]]; consumed by [[Home Assistant]] on
[[weathertop.shire]].

## Related

- [[Sensors]]
- [[MQTT]]

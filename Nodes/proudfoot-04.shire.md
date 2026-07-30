---
type: node
hostname: proudfoot-04.shire
ip: 10.136.30.14
vlan: 30
category: iot
hardware: ESP8266
role: Temperature and humidity sensor — kitchen
status: active
tags:
  - node
  - iot
  - sensor
---

# proudfoot-04.shire

Temperature and humidity sensor in the kitchen. Proudfoot family — see [[Conventions]].

## Network

| Property | Value |
|---|---|
| IP | 10.136.30.14 (DHCP reservation) |
| VLAN | 30 — IoT |
| SSID | `green-dragon-inn.shire` on [[bree.shire]] |

## Telemetry

Publishes over MQTT to [[gondolin.shire]]; consumed by [[Home Assistant]] on
[[weathertop.shire]].

## Related

- [[Sensors]]
- [[MQTT]]

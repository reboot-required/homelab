---
type: node
hostname: proudfoot-03.shire
ip: 10.136.30.13
vlan: 30
category: iot
hardware: ESP8266
role: Temperature and humidity sensor — bathroom
status: active
tags:
  - node
  - iot
  - sensor
---

# proudfoot-03.shire

Temperature and humidity sensor in the bathroom. Proudfoot family — see [[Conventions]].

## Network

| Property | Value |
|---|---|
| IP | 10.136.30.13 (DHCP reservation) |
| VLAN | 30 — IoT |
| SSID | `green-dragon-inn.shire` on [[bree.shire]] |

## Telemetry

Publishes over MQTT to [[gondolin.shire]]; consumed by [[Home Assistant]] on
[[weathertop.shire]].

## Related

- [[Sensors]]
- [[MQTT]]

---
type: node
hostname: proudfoot-01.shire
ip: 10.136.30.11
vlan: 30
category: iot
hardware: ESP8266
role: Temperature and humidity sensor — living room
status: active
tags:
  - node
  - iot
  - sensor
---

# proudfoot-01.shire

Temperature and humidity sensor in the living room. Proudfoot family — see [[Conventions]].

## Network

| Property | Value |
|---|---|
| IP | 10.136.30.11 (DHCP reservation) |
| VLAN | 30 — IoT |
| SSID | `green-dragon-inn.shire` on [[bree.shire]] |

## Telemetry

Publishes over MQTT to [[gondolin.shire]]; consumed by [[Home Assistant]] on
[[weathertop.shire]].

## Related

- [[Sensors]]
- [[MQTT]]

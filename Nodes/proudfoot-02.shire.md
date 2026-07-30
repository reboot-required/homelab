---
type: node
hostname: proudfoot-02.shire
ip: 10.136.30.12
vlan: 30
category: iot
hardware: ESP8266
role: Temperature and humidity sensor — bedroom
status: active
tags:
  - node
  - iot
  - sensor
---

# proudfoot-02.shire

Temperature and humidity sensor in the bedroom. Proudfoot family — see [[Conventions]].

## Network

| Property | Value |
|---|---|
| IP | 10.136.30.12 (DHCP reservation) |
| VLAN | 30 — IoT |
| SSID | `green-dragon-inn.shire` on [[bree.shire]] |

## Telemetry

Publishes over MQTT to [[gondolin.shire]]; consumed by [[Home Assistant]] on
[[weathertop.shire]].

## Related

- [[Sensors]]
- [[MQTT]]

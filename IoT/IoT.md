---
type: moc
tags:
  - moc
  - iot
---

# IoT

Seven devices, all isolated on VLAN 30, all talking MQTT.

## Pages

- [[Sensors]] — five ESP8266 temperature and humidity sensors
- [[Smart Plugs]] — two power-monitoring plugs
- [[MQTT]] — the message bus, and the open question about where the broker sits

## Devices

Sensors: [[proudfoot-00.shire]] · [[proudfoot-01.shire]] ·
[[proudfoot-02.shire]] · [[proudfoot-03.shire]] · [[proudfoot-04.shire]]

Plugs: [[took-00.shire]] · [[took-01.shire]]

Broker: [[gondolin.shire]] · Consumer: [[weathertop.shire]]

## Isolation

VLAN 30 reaches the Internet for NTP, DNS and OTA only, and reaches nothing on
the homelab network. [[Home Assistant]] talks to these devices through a second
NIC inside VLAN 30 rather than through a firewall hole — see [[Firewall Rules]].

## Open item

The documented MQTT path crosses a boundary the firewall denies. Tracked on
[[gondolin.shire]] and in [[MQTT]].

## Related

- [[Wireless]] — the `green-dragon-inn.shire` SSID
- [[Home Assistant]]

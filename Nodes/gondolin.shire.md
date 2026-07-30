---
type: node
hostname: gondolin.shire
ip: 
vlan: 20
category: sbc
hardware: Raspberry Pi 2B
role: MQTT broker / IoT gateway
status: active
tags:
  - node
  - sbc
  - iot
  - mqtt
---

# gondolin.shire

*The hidden city.* The MQTT broker: every IoT sensor and plug publishes here,
and [[Home Assistant]] on [[weathertop.shire]] subscribes.

## Network

| Property | Value |
|---|---|
| IP | **Unknown** — 10.136.20.x, not yet recorded |
| VLAN | 20 |
| Uplink | Not recorded — no port assigned on [[hobbiton.shire]] or [[greenway.shire]] |

> [!bug] Two open questions on this node
> 1. **The IP is undocumented.** It is the only node in the lab without a
>    recorded address. Read it off the DHCP leases on [[the.shire]] and fill it
>    in here.
> 2. **The path from the sensors to this broker is not explained.** The sensors
>    are on VLAN 30 and [[Firewall Rules]] denies VLAN 30 → VLAN 20 outright,
>    yet they are documented as publishing to a broker on VLAN 20. One of three
>    things is true and the live config decides which:
>    - this node also has an interface on VLAN 30,
>    - there is an allow rule not captured in [[Firewall Rules]], or
>    - the broker the devices actually reach is on
>      [[weathertop.shire]]'s IoT NIC (10.136.30.5) and this node does something
>      else.
>
> Do not build on the MQTT documentation until this is settled.

## Publishers

- [[proudfoot-00.shire]] – [[proudfoot-04.shire]] — temperature / humidity
- [[took-00.shire]], [[took-01.shire]] — smart plugs

## Related

- [[MQTT]]
- [[IoT]]

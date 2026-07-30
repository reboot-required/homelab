---
type: note
tags:
  - networking
  - firewall
  - security
---

# Firewall Rules

All inter-VLAN routing happens on [[the.shire]]. **Default policy is deny.**
Everything below is an explicit exception.

## Matrix

| From ↓ / To → | Homelab 20 | Workstation 50 | IoT 30 | Guest 100 | Internet |
|---|:--:|:--:|:--:|:--:|:--:|
| **Homelab 20** | — | allow | deny | deny | allow |
| **Workstation 50** | allow | — | deny | deny | allow |
| **IoT 30** | deny | deny | — | deny | limited |
| **Guest 100** | deny | deny | deny | — | allow |

## Notes per segment

**Homelab ↔ Workstation** is open in both directions. The workstation is trusted
kit on a separate wire, not a security boundary — the separation exists so
desktop traffic does not share the lab switch fabric.

**IoT → Internet** is limited to NTP, DNS and OTA firmware updates. Nothing else
leaves VLAN 30.

**IoT → Homelab** is denied outright, including
[[weathertop.shire]]'s homelab address (10.136.20.107). The IoT devices reach
Home Assistant on 10.136.30.5 instead, which is the same VLAN and therefore
never sees the firewall at all. See [[VLANs]].

**Guest** is Internet and nothing else. DNS is answered by [[the.shire]] on
10.136.100.1 — that is the only internal address a guest may reach.

## Open question

> [!bug] The MQTT path contradicts this matrix
> [[MQTT]] documents the sensors on VLAN 30 publishing to a broker on
> [[gondolin.shire]], which is on VLAN 20 — a path this matrix denies. Either
> there is a rule missing from this page or the documented broker location is
> wrong. Tracked on [[gondolin.shire]].

## Client placement

| Client | Segment | How |
|---|---|---|
| Laptops, phones | Homelab 20 | Wi-Fi `bag-end.shire` (5 GHz) or wired |
| Workstation | Workstation 50 | Wired, [[the.shire]] port 30 |
| Guests | Guest 100 | Wi-Fi `prancing-pony.shire` |
| Sensors, plugs | IoT 30 | Wi-Fi `green-dragon-inn.shire` |

## Related

- [[VLANs]]
- [[OPNsense]]
- [[Wireless]]

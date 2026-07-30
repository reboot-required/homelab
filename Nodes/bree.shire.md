---
type: node
hostname: bree.shire
ip: 10.136.20.151
vlan: 20
category: network
hardware: Zyxel NWA50AX (Wi-Fi 6, 802.11ax)
os: OpenWRT
role: Wireless access point
power-idle-w: 6
power-peak-w: 12
status: active
tags:
  - node
  - network
  - wireless
---

# bree.shire

The only access point in the homelab. It runs OpenWRT rather than the stock
Zyxel firmware, which is what makes the per-SSID VLAN tagging below possible.

## Virtual APs

Three virtual APs, one per VLAN, all on this one radio pair:

| Virtual AP | Band | Security | VLAN | Subnet |
|---|---|---|---|---|
| `bag-end.shire` | 5 GHz | WPA3-Personal | 20 (native) | 10.136.20.0/24 |
| `green-dragon-inn.shire` | 2.4 GHz | WPA2-Personal | 30 | 10.136.30.0/24 |
| `prancing-pony.shire` | 2.4 GHz | WPA2-Personal | 100 | 10.136.100.0/24 |

> [!info] Why the IoT and guest SSIDs are 2.4 GHz
> The ESP8266 sensors have no 5 GHz radio, and guest range matters more than
> guest throughput.

## Network

| Property | Value |
|---|---|
| Management IP | 10.136.20.151 (static) |
| Uplink | [[greenway.shire]] port 7 — trunk, PoE |
| Tagged VLANs | 30, 100 |
| Native VLAN | 20 |

## Physical

| Property | Value |
|---|---|
| Hardware | Zyxel NWA50AX |
| Mounting | Not rack-mounted — PoE, wall/ceiling |
| Power (idle / peak) | 6 W / 12 W (via PoE from [[greenway.shire]]) |

## Related

- [[Wireless]] — SSID and OpenWRT configuration
- [[VLANs]]
- [[Firewall Rules]]

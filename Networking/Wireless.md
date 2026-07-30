---
type: note
tags:
  - networking
  - wireless
---

# Wireless

One access point, [[bree.shire]], serving three networks from three virtual APs.
It runs OpenWRT rather than stock Zyxel firmware — that is what makes per-SSID
VLAN tagging possible.

## SSIDs

| Virtual AP | Band | Security | VLAN | Subnet |
|---|---|---|---:|---|
| `bag-end.shire` | 5 GHz | WPA3-Personal | 20 | 10.136.20.0/24 |
| `green-dragon-inn.shire` | 2.4 GHz | WPA2-Personal | 30 | 10.136.30.0/24 |
| `prancing-pony.shire` | 2.4 GHz | WPA2-Personal | 100 | 10.136.100.0/24 |

Band choice is not arbitrary: the ESP8266 sensors have no 5 GHz radio, and for
guests, range beats throughput.

WPA2 on the IoT and guest SSIDs is a client-compatibility compromise. Both
networks are firewalled as untrusted, which is what actually contains them —
see [[Firewall Rules]].

## Uplink

Single cable to [[greenway.shire]] port 7: PoE for power, 802.1Q trunk for the
three VLANs. Native VLAN 20, tagged 30 and 100.

## To document

> [!todo] Stub
> - OpenWRT installation on the NWA50AX and how to recover it
> - Bridge-VLAN configuration mapping each VAP to its tag
> - Channel, width and transmit power per band
> - Client isolation on the IoT and guest VAPs
> - Firmware upgrade procedure

## Related

- [[bree.shire]]
- [[VLANs]]
- [[Firewall Rules]]
- [[Future Hardware]] — splitting the VAPs onto separate physical APs

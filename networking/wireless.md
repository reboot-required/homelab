[Home](../README.md) › [Networking](README.md) › Wireless

# Wireless

> 🚧 This page is a stub. Content to be added.

**Hardware:** Zyxel NWA50AX — Wi-Fi 6 (802.11ax), running **OpenWRT**  
**Host:** `bree.shire` | **IP:** 10.136.20.4  
**Connected via:** `greenway.shire` (PoE, port 7)

---

## SSID Overview

| Virtual AP | Band | VLAN | Description |
|---|---|---|---|
| `bag-end.shire` | 5 GHz | 20 | Home Wi-Fi — homelab access |
| `green-dragon-inn.shire` | 2.4 GHz | 30 | IoT Wi-Fi — isolated VLAN 30 |
| `prancing-pony.shire` | 2.4 GHz | 100 | Guest Wi-Fi — Internet only |

---

## Planned Content

- OpenWRT installation and configuration on Zyxel NWA50AX
- Virtual AP (VAP) setup per VLAN
- VLAN tagging configuration in OpenWRT
- WPA3 / WPA2 security settings per SSID
- Channel and band configuration
- Client isolation settings for guest and IoT SSIDs
- Firmware upgrade procedure

---

## See Also

- [overview.md](overview.md) — section 8: Wireless Networks
- [vlans.md](vlans.md) — VLAN architecture

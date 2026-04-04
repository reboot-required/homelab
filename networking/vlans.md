[Home](../README.md) › [Networking](README.md) › VLANs

# VLANs

> 🚧 This page is a stub. Detailed VLAN content will be extracted from [overview.md](overview.md) and expanded here.

For current VLAN architecture, firewall rules, and inter-VLAN routing, refer to [overview.md](overview.md) (sections 4 and 12).

A visual VLAN diagram is available: [vlan-dummy.excalidraw](vlan-dummy.excalidraw)

---

## VLAN Summary

| VLAN ID | Name | Subnet | Gateway | Description |
|---|---|---|---|---|
| 20 | Homelab | 10.136.20.0/24 | 10.136.20.1 | All trusted infrastructure |
| 30 | IoT | 10.136.30.0/24 | 10.136.30.1 | IoT sensors and smart-home devices |
| 100 | Guest | 10.136.100.0/24 | 10.136.100.1 | Untrusted guest Wi-Fi clients |
| — | Workstation | 10.136.50.0/24 | 10.136.50.1 | Personal workstation (dedicated OPNsense port) |

---

## Planned Content

- Detailed VLAN configuration steps on OPNsense
- 802.1Q trunk port configuration per switch
- Inter-VLAN routing rules and firewall policy
- DHCP reservation management

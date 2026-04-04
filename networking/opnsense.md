[Home](../README.md) › [Networking](README.md) › OPNsense

# OPNsense

> 🚧 This page is a stub. Content to be added.

**Host:** `the.shire` | **IP:** 10.136.20.1 | **Hardware:** N150 Mini-PC, 4× NIC

OPNsense is the router, firewall, DNS resolver, and DHCP server for the entire homelab network.

> ⚠️ This page documents configuration structure only. No secrets, passwords, pre-shared keys, or API keys are stored here.

---

## Planned Content

- Interface assignments (WAN, HOMELAB, WORKSTATION, DEBUG)
- Firewall rules per interface/VLAN (structural overview — allowed/blocked)
- NAT / port forwarding rules
- Firewall aliases
- DHCP server configuration per interface
- Unbound DNS resolver settings
- Ad-blocking / DNS blocklist configuration
- Certificate management (if applicable)
- Scheduled tasks and cron jobs

---

## Interface Overview

| Port | Role | Subnet |
|---|---|---|
| 10 | WAN | DHCP from ISP |
| 20 | HOMELAB (LAN) | 10.136.20.0/24 |
| 30 | WORKSTATION | 10.136.50.0/24 |
| 40 | DEBUG | 10.136.40.0/24 |

See [overview.md](overview.md) for current interface and firewall documentation.

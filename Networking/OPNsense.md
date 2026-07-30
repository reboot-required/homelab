---
type: note
tags:
  - networking
  - opnsense
  - firewall
---

# OPNsense

Runs on [[the.shire]]. Router, firewall, DHCP server and DNS resolver in one
box.

> [!warning] No secrets on this page
> Configuration structure only. No passwords, pre-shared keys, API keys or
> certificates — see [[Conventions]].

## Interfaces

| Port | Role | Subnet | Connected to |
|---:|---|---|---|
| 10 | WAN | DHCP from ISP | Fiber modem |
| 20 | HOMELAB | 10.136.20.0/24 | [[hobbiton.shire]], trunk |
| 30 | WORKSTATION | 10.136.50.0/24 | [[iron-hills.shire]], direct |
| 40 | DEBUG | 10.136.40.0/24 | *unconnected* |

VLAN 30 and VLAN 100 are 802.1Q sub-interfaces on port 20.

## Services it provides

| Service | Detail |
|---|---|
| Routing and firewall | [[Firewall Rules]] |
| DHCP | Per-interface pools, see [[IP Plan]] |
| DNS resolver (Unbound) | [[DNS]] |
| Ad-blocking | [[DNS]] |

> [!todo] Stub
> To document: sub-interface configuration, per-interface firewall rule sets,
> NAT and port forwards, firewall aliases, DHCP pools and reservations, Unbound
> settings, blocklist configuration, certificate management, scheduled tasks.

## Related

- [[the.shire]]
- [[Firewall Rules]]
- [[VLANs]]
- [[DNS]]

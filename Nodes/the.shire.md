---
type: node
hostname: the.shire
ip: 10.136.20.1
vlan: all
category: network
hardware: N150 Mini-PC (4× NIC)
os: OPNsense
role: Router, firewall, DNS, DHCP, ad-blocking
power-idle-w: 6
power-peak-w: 15
status: active
tags:
  - node
  - network
  - opnsense
---

# the.shire

The router, firewall, DNS resolver and DHCP server for the entire homelab.
Everything that crosses a subnet boundary crosses this box.

## Role

Four physical interfaces, one per network role. VLAN 30 and VLAN 100 ride as
802.1Q sub-interfaces on port 20 — see [[OPNsense]] for the interface detail.

| Port | Role | Connected to | Subnet |
|---|---|---|---|
| 10 | WAN | Fiber optic modem | DHCP from ISP |
| 20 | HOMELAB | [[hobbiton.shire]] (trunk) | 10.136.20.0/24 |
| 30 | WORKSTATION | [[iron-hills.shire]] (direct) | 10.136.50.0/24 |
| 40 | DEBUG | *unconnected* | 10.136.40.0/24 |

> [!warning] Port 30 is not VLAN 30
> Physical port 30 carries the workstation on 10.136.50.0/24. VLAN 30 is the IoT
> network on 10.136.30.0/24, tagged on port 20. The subnets were chosen to be
> different on purpose so the two can never be confused in a firewall rule.

## Gateway addresses

`the.shire` holds the gateway address in every segment:

| Segment | Address |
|---|---|
| Homelab VLAN 20 | 10.136.20.1 |
| IoT VLAN 30 | 10.136.30.1 |
| Workstation | 10.136.50.1 |
| Guest VLAN 100 | 10.136.100.1 |

## Physical

| Property | Value |
|---|---|
| Hardware | N150 Mini-PC, 4× NIC |
| Rack position | U9 — see [[Rack Layout]] |
| Power (idle / peak) | 6 W / 15 W |

## Related

- [[OPNsense]] — configuration detail
- [[VLANs]] — VLAN architecture
- [[Firewall Rules]] — inter-VLAN policy
- [[DNS]] — Unbound resolver and ad-blocking
- [[Network Topology]]

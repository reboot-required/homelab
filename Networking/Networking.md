---
type: moc
tags:
  - moc
  - networking
---

# Networking

Supernet 10.136.0.0/16, routed and firewalled by [[the.shire]]. Three tagged
VLANs plus a physically separate workstation segment.

## Pages

- [[Network Topology]] — how everything is wired
- [[VLANs]] — segmentation and the trust model
- [[IP Plan]] — addressing scheme
- [[Switch Ports]] — port-by-port on both switches
- [[Firewall Rules]] — the deny-by-default matrix
- [[Wireless]] — SSIDs and the access point
- [[DNS]] — resolution and ad-blocking
- [[OPNsense]] — the router itself

## Network nodes

[[the.shire]] · [[hobbiton.shire]] · [[greenway.shire]] · [[bree.shire]]

## Open items

- [[gondolin.shire]] has no recorded IP and no recorded switch port
- The MQTT path from VLAN 30 contradicts [[Firewall Rules]]
- Several SBCs have no recorded switch port — see [[Switch Ports]]

## Related

- [[Node Registry]]
- [[Infrastructure]]

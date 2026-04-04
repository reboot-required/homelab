[Home](../README.md) › [Networking](README.md) › DNS

# DNS

> 🚧 This page is a stub. Content to be added.

Local DNS is handled by **OPNsense Unbound** on `the.shire` (10.136.20.1). All homelab devices are reachable via their `.shire` hostnames within the homelab network.

---

## Planned Content

- OPNsense Unbound configuration
- Local DNS override entries (hostname → IP mapping for all nodes)
- DNS-based ad-blocking configuration (blocklists, allowlists)
- DNS resolution for IoT VLAN 30 and Guest VLAN 100
- Search domain configuration (`.shire`)

---

## See Also

- [Node Registry](../infrastructure/node-registry.md) — authoritative hostname/IP table
- [OPNsense](opnsense.md) — full OPNsense configuration

---
type: note
tags:
  - networking
  - dns
---

# DNS

Unbound on [[the.shire]] resolves and filters for the whole lab. Every node is
reachable by its `.shire` hostname from the homelab network.

> [!todo] Stub
> The structure below is what needs documenting. None of it is written yet.

## To document

- Unbound configuration on OPNsense
- Host overrides — the hostname → IP map for every node
- Ad-blocking: which blocklists, which allowlist entries, update schedule
- Resolution policy for VLAN 30 and VLAN 100 (guests resolve via 10.136.100.1;
  what they are allowed to resolve is not recorded)
- `.shire` search domain distribution via DHCP

## Note

The host override list duplicates [[Node Registry]] by nature. When documenting
it, record how the two are kept in sync — or accept that Unbound is generated
from the registry and say so.

## Related

- [[OPNsense]]
- [[IP Plan]]
- [[Node Registry]]

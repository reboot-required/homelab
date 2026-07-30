---
type: service
host: "[[thal.shire]]"
url: http://10.136.20.104
port: 80
deployment: proxmox-vm
status: running
tags:
  - service
  - dashboard
---

# Heimdall

The lab's front page — a tile per service, so nobody has to remember which port
lives on which IP.

## Access

| Property | Value |
|---|---|
| Internal URL | `http://10.136.20.104` |
| Port | 80 |
| Host | [[thal.shire]] — VM 103, Debian 12 |

## Tiles

Should point at every entry in [[Services]]. Whether it currently does is not
recorded.

## To document

> [!todo] Stub
> - Install method
> - Tile configuration and where it is stored
> - Whether the tile list is backed up — it is small, easily rebuilt, and
>   equally easily forgotten

## Future plans

- Set as the browser home page on internal clients
- Revisit once a reverse proxy gives services real hostnames — see
  [[Future Services]]

## Related

- [[thal.shire]]
- [[Services]]

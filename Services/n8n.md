---
type: service
host: "[[radagast.shire]]"
url: http://10.136.20.101:5678
port: 5678
deployment: proxmox-vm
status: running
tags:
  - service
  - automation
---

# n8n

Workflow automation — the glue between homelab services.

## Access

| Property | Value |
|---|---|
| Internal URL | `http://10.136.20.101:5678` |
| Port | 5678 |
| Host | [[radagast.shire]] — VM 100, Debian 12 |

## To document

> [!todo] Stub
> - Install method and version
> - **The active workflows.** None are documented. A workflow that silently
>   stops firing is invisible until something downstream is missing, so at
>   minimum record what each one does and what it touches.
> - Credential storage — that it exists and where, never the values
> - Backup of the workflow database. Workflows are on the [[Backup Strategy]]
>   critical list.

## Future plans

- GitLab webhook integration
- Home Assistant integration
- Alert webhook target for [[Alerting]]

## Related

- [[radagast.shire]]
- [[Automation]]

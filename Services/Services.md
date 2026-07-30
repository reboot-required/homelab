---
type: moc
tags:
  - moc
  - services
---

# Services

Everything self-hosted, one note each.

| Service | Host | URL | Status |
|---|---|---|---|
| [[GitLab CE]] | [[erebor.shire]] | `http://10.136.20.102` | running |
| [[Grafana]] | [[palantir.shire]] | `http://10.136.20.105:3000` | running |
| [[Prometheus]] | [[palantir.shire]] | `http://10.136.20.105:9090` | running |
| [[Heimdall]] | [[thal.shire]] | `http://10.136.20.104` | running |
| [[n8n]] | [[radagast.shire]] | `http://10.136.20.101:5678` | running |
| [[Home Assistant]] | [[weathertop.shire]] | `http://10.136.20.107:8123` | running |
| [[LLM Server]] | [[valinor.shire]] | `http://10.136.20.20:3000` | running |
| [[TrueNAS Scale]] | [[rivendell.shire]] | `http://10.136.20.103` | running |

Planned additions: [[Future Services]].

## Everything is an IP and a port

No service has a hostname or TLS. Eight services means eight `IP:port`
combinations to remember, which is what [[Heimdall]] exists to paper over. A
reverse proxy plus DNS overrides on [[the.shire]] would fix the cause rather
than the symptom — see [[Future Services]].

## Common gap

Not one service note records how its data is backed up. [[Backup Strategy]]
lists what ought to be captured; nothing yet describes how.

## Related

- [[Node Registry]]
- [[Monitoring]]

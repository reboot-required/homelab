---
type: service
host: "[[palantir.shire]]"
url: http://10.136.20.105:3000
port: 3000
deployment: proxmox-vm
status: running
tags:
  - service
  - monitoring
---

# Grafana

Visualisation layer of the monitoring stack. Reads from [[Prometheus]] on the
same host.

## Access

| Property | Value |
|---|---|
| Internal URL | `http://10.136.20.105:3000` |
| Port | 3000 |
| Host | [[palantir.shire]] — VM 104, Debian 12 |

## Dependencies

- [[Prometheus]] — data source
- [[bill-the-pony.shire]] — hypervisor

## To document

> [!todo] Stub
> - Install method and version
> - Data source configuration
> - Authentication — local users or something else
> - Dashboard provisioning: are dashboards in git, or clicked together in the UI
>   and lost on a rebuild?

Dashboard inventory lives in [[Dashboards]].

## Future plans

- Dashboards for the K3s cluster
- Power dashboard from the [[Smart Plugs]], to replace the estimates in
  [[Power Budget]]
- Alerting — see [[Alerting]]

## Related

- [[palantir.shire]]
- [[Monitoring Stack]]

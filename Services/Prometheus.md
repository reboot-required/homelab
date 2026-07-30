---
type: service
host: "[[palantir.shire]]"
url: http://10.136.20.105:9090
port: 9090
deployment: proxmox-vm
status: running
tags:
  - service
  - monitoring
---

# Prometheus

Metrics collection and time-series storage.

## Access

| Property | Value |
|---|---|
| Internal URL | `http://10.136.20.105:9090` |
| Port | 9090 |
| Host | [[palantir.shire]] — VM 104, Debian 12 |

> [!bug] Also listed as a K3s workload
> [[K3s Workloads]] lists Prometheus in the `monitoring` namespace. Either that
> is a second instance, or one of the two entries is stale. Settle this before
> building anything else on the monitoring stack.

## Dependencies

- Node exporters on the monitored hosts — **not yet deployed anywhere**

Without exporters, there is very little for this instance to scrape. That is the
first gap to close in [[Monitoring Stack]].

## To document

> [!todo] Stub
> - `prometheus.yml`: scrape targets and intervals
> - Retention settings — the 50 GB disk on [[palantir.shire]] is sized for this
> - Service discovery, or static targets
> - Alert rules — see [[Alerting]]

## Related

- [[Grafana]]
- [[Monitoring Stack]]
- [[palantir.shire]]

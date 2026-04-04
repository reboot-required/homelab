[Home](../README.md) › [Monitoring](README.md) › Stack Overview

# Monitoring Stack Overview

> 🚧 This page is a stub. Content to be added.

The homelab monitoring stack is hosted on `palantir.shire` (10.136.20.105) and consists of **Prometheus** for metrics collection and **Grafana** for visualization.

---

## Architecture

```
                    ┌──────────────────────────────┐
                    │       palantir.shire          │
                    │       10.136.20.105           │
                    │                              │
                    │  ┌──────────┐  ┌──────────┐  │
                    │  │Prometheus│  │ Grafana  │  │
                    │  │ :9090    │◄─│  :3000   │  │
                    │  └────┬─────┘  └──────────┘  │
                    └───────┼──────────────────────┘
                            │ scrape
              ┌─────────────┼─────────────────┐
              │             │                 │
         node exporters   K3s metrics    other targets
         (all nodes)      (isengard etc)  (planned)
```

---

## Planned Content

- Prometheus configuration file overview (scrape intervals, targets)
- Node Exporter deployment on all homelab nodes
- K3s / kube-state-metrics integration
- Grafana data source configuration
- Retention and storage settings

---

## See Also

- [services/prometheus.md](../services/prometheus.md) — Prometheus service page
- [services/grafana.md](../services/grafana.md) — Grafana service page
- [dashboards.md](dashboards.md) — available dashboards
- [alerting.md](alerting.md) — alerting configuration

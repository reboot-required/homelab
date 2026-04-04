[Home](../README.md) › [Services](README.md) › Prometheus

# Prometheus

> 🚧 This page is a stub. Content to be added.

## Overview

Prometheus is the metrics collection and storage backend for the homelab monitoring stack. It scrapes metrics from all nodes, VMs, and Kubernetes workloads, storing them as time-series data for consumption by Grafana.

## Host

| Property | Value |
|---|---|
| Hostname | `palantir.shire` |
| IP | 10.136.20.105 |
| VM ID | 104 |
| Hypervisor | `bill-the-pony.shire` |
| OS | Debian 12 |

See [infrastructure/node-registry.md](../infrastructure/node-registry.md) for the authoritative node listing.

## Access

| Property | Value |
|---|---|
| Internal URL | `http://10.136.20.105:9090` |
| Port | 9090 |

## Deployment

> 🚧 Deployment details to be added.

## Configuration Highlights

> 🚧 Scrape targets to be documented.

## Dependencies

- `bill-the-pony.shire` — Proxmox hypervisor
- Node exporters on all monitored hosts (planned)

## Backup & Recovery

> 🚧 To be documented.

## Runbook

> 🚧 To be documented.

## Future Plans

- Define scrape targets for all homelab nodes
- Add alerting rules (see [monitoring/alerting.md](../monitoring/alerting.md))
- Integrate with Grafana dashboards

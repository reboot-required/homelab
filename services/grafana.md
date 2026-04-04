[Home](../README.md) › [Services](README.md) › Grafana

# Grafana

> 🚧 This page is a stub. Content to be added.

## Overview

Grafana is the visualization and dashboarding layer for the homelab monitoring stack. It connects to Prometheus as a data source and provides dashboards for infrastructure metrics, node health, and Kubernetes workloads.

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
| Internal URL | `http://10.136.20.105:3000` |
| Port | 3000 |

## Deployment

> 🚧 Deployment details to be added.

## Configuration Highlights

> 🚧 To be documented.

## Dependencies

- [Prometheus](prometheus.md) — metrics data source
- `bill-the-pony.shire` — Proxmox hypervisor

## Backup & Recovery

> 🚧 To be documented.

## Runbook

> 🚧 To be documented.

## Future Plans

- Add dashboards for K3s cluster metrics
- Configure alerting via notification channels
- See [monitoring/dashboards.md](../monitoring/dashboards.md)

---
type: note
tags:
  - monitoring
  - grafana
---

# Dashboards

Grafana on [[palantir.shire]], `http://10.136.20.105:3000`.

## Existing

None recorded. If dashboards exist in the running instance, they are not
documented and — see [[Grafana]] — probably not in git either, which means a
rebuild loses them.

## Planned

| Dashboard | Shows | Blocked on |
|---|---|---|
| Node overview | CPU, RAM, disk, network per host | node_exporter deployment |
| Power | Draw at the rack and living room | [[took-00.shire]] data in [[MQTT]] |
| Proxmox | Guest resource usage on [[bill-the-pony.shire]] | Proxmox metrics export |
| K3s cluster | Pods, nodes, resources | kube-state-metrics |
| IoT sensors | Temperature and humidity per room | [[MQTT]] → Prometheus path |
| LLM server | Load on [[valinor.shire]] | node_exporter on macOS |

The power dashboard is the one worth building first: it is the only one that
replaces a documented estimate with a measurement — see [[Power Budget]].

## To document

> [!todo] Stub
> - Where dashboard JSON lives. If the answer is "only in Grafana's database",
>   fix that before building more.
> - Provisioning configuration
> - Template variables for host selection

## Related

- [[Monitoring Stack]]
- [[Grafana]]
- [[Alerting]]

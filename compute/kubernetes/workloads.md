[Home](../../README.md) › [Compute](../README.md) › [Kubernetes](README.md) › Workloads

# K3s Workloads

> 🚧 This page is a stub. Content to be added.

---

## Currently Deployed

| Workload | Namespace | Description |
|---|---|---|
| Prometheus | `monitoring` | Metrics collection and storage |
| GitLab Runner | `gitlab` | CI/CD pipeline executor |

---

## Planned Content

- Full workload inventory with Helm chart versions
- Namespace layout
- Resource requests and limits
- Persistent volume claims
- Ingress / service exposure
- GitOps / deployment method (Helm, Kustomize, raw YAML)

---

## See Also

- [services/prometheus.md](../../services/prometheus.md) — Prometheus service page
- [services/gitlab.md](../../services/gitlab.md) — GitLab service page
- [cluster-setup.md](cluster-setup.md) — cluster configuration

---
type: note
tags:
  - compute
  - kubernetes
---

# K3s Workloads

What actually runs on the cluster.

| Workload | Namespace | Purpose |
|---|---|---|
| Prometheus | `monitoring` | Metrics collection |
| GitLab Runner | `gitlab` | CI/CD executor for [[GitLab CE]] |

> [!bug] Two Prometheus instances?
> [[Prometheus]] is documented as running on [[palantir.shire]] *and* as a
> workload in the `monitoring` namespace here. Either one scrapes the other,
> they are separate instances with separate retention, or one of the two entries
> is stale. Resolve before extending [[Monitoring Stack]].

The GitLab Runner deliberately runs here rather than on [[erebor.shire]] — CI
load stays off the box holding the repositories.

## To document

> [!todo] Stub
> - Full workload inventory with chart versions
> - Namespace layout
> - Resource requests and limits
> - Persistent volume claims and their backing storage
> - How services are exposed — Ingress, NodePort, LoadBalancer
> - Deployment method: Helm, Kustomize, or raw manifests, and where they live

## Related

- [[K3s Cluster]]
- [[GitLab CI]]
- [[Monitoring Stack]]

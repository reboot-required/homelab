---
type: note
tags:
  - compute
  - kubernetes
  - k3s
---

# K3s Cluster

Three nodes, one control plane, no high availability — a single master is a
deliberate simplification for a lab this size.

| Role | Node | IP | Hardware |
|---|---|---|---|
| Control plane | [[isengard.shire]] | 10.136.20.11 | Cel3867U Mini-PC |
| Worker | [[rohan.shire]] | 10.136.20.12 | N150 Mini-PC |
| Worker | [[gondor.shire]] | 10.136.20.13 | N150 Mini-PC |

All three are access ports on VLAN 20 — the cluster does no VLAN work of its
own. A fourth node would go in the free U1 shelf, see [[Rack Layout]].

> [!warning] Single point of failure
> [[isengard.shire]] is the only control-plane node. If it dies the cluster is
> unmanageable until it is restored, and it is also the oldest hardware in the
> cluster.

## To document

> [!todo] Stub
> - K3s version and install method
> - kubeconfig location and how to get one
> - CNI in use (K3s ships Flannel by default — confirm)
> - Ingress: Traefik ships with K3s; is it in use or disabled?
> - Persistent storage — local-path, or NFS from [[rivendell.shire]]?
> - Load balancer (ServiceLB / MetalLB)
> - Node labels and taints
> - The join token and where it is kept — *reference only, never the value*

## Runbooks

- [[Add K3s Node]]
- [[Upgrade K3s]]

## Related

- [[K3s Workloads]]
- [[Compute]]

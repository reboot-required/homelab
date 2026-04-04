[Home](../../README.md) › [Compute](../README.md) › Kubernetes (K3s)

# Kubernetes (K3s)

> 🚧 This page is a stub. Content to be added.

The homelab runs a **3-node K3s cluster** for lightweight Kubernetes workloads.

---

## Cluster Nodes

| Role | Hostname | IP | Hardware |
|---|---|---|---|
| Master | `isengard.shire` | 10.136.20.11 | Cel3867U Mini-PC |
| Worker 1 | `rohan.shire` | 10.136.20.12 | N150 Mini-PC |
| Worker 2 | `gondor.shire` | 10.136.20.13 | N150 Mini-PC |

---

## Pages

| Page | Description |
|---|---|
| [Cluster Setup](cluster-setup.md) | Installation notes, kubeconfig, CNI |
| [Workloads](workloads.md) | Deployed workloads: Prometheus, GitLab Runner |
| **Runbooks** | |
| [Add Node](runbooks/add-node.md) | Step-by-step: add a new K3s node |
| [Upgrade K3s](runbooks/upgrade-k3s.md) | Step-by-step: upgrade K3s version |

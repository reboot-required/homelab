---
type: runbook
target: "[[K3s Cluster]]"
tags:
  - runbook
  - kubernetes
---

# Upgrade K3s

> [!warning] Single control plane
> [[isengard.shire]] is the only master. While it is upgrading, the cluster
> cannot be managed. Running workloads keep running, but nothing can be
> scheduled or changed. Do this when that is acceptable.

## Before you start

- Record the current version on all three nodes.
- Read the K3s release notes between your version and the target — mind the
  Kubernetes deprecations, not just the K3s changelog.
- Confirm the workloads in [[K3s Workloads]] tolerate the target Kubernetes
  version.

## Steps

1. Upgrade [[isengard.shire]] first. The control plane must never be older than
   its agents.
2. Wait until the API server answers and `kubectl get nodes` is healthy.
3. Upgrade [[rohan.shire]]. Drain it, upgrade, uncordon, confirm `Ready`.
4. Upgrade [[gondor.shire]] the same way.

One worker at a time — with only two of them, taking both down leaves nowhere
for pods to go.

## Verify

- All three nodes `Ready` and reporting the target version.
- Every workload in [[K3s Workloads]] is running, including the GitLab Runner.
- A CI job actually completes — see [[GitLab CI]].

## Rollback

K3s does not downgrade cleanly. Rollback means restoring the etcd/SQLite
snapshot from [[isengard.shire]] taken before the upgrade. Confirm that snapshot
exists *before* step 1.

## Afterwards

- Note the new version in [[K3s Cluster]].
- Record it in [[Changelog]].

## Related

- [[K3s Cluster]]
- [[Add K3s Node]]

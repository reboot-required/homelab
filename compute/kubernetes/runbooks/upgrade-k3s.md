[Home](../../../README.md) › [Compute](../../README.md) › [Kubernetes](../README.md) › Runbook: Upgrade K3s

# Runbook: Upgrade K3s

> 🚧 This page is a stub. Content to be added.

---

## Planned Steps

1. Check current K3s version on all nodes
2. Review K3s release notes for breaking changes
3. Drain the master node workloads
4. Upgrade K3s on `isengard.shire` (master)
5. Verify master is healthy
6. Upgrade K3s on `rohan.shire` and `gondor.shire` (workers) one at a time
7. Verify all nodes are Ready
8. Update version documentation

---

## See Also

- [cluster-setup.md](../cluster-setup.md) — cluster configuration
- [add-node.md](add-node.md) — add node runbook

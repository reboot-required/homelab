[Home](../../../README.md) › [Compute](../../README.md) › [Kubernetes](../README.md) › Runbook: Add Node

# Runbook: Add a K3s Node

> 🚧 This page is a stub. Content to be added.

---

## Planned Steps

1. Prepare the new node (install OS, set static IP, register in [node-registry.md](../../../infrastructure/node-registry.md))
2. Install K3s agent with the cluster join token
3. Verify the node appears in `kubectl get nodes`
4. Apply labels and taints as needed
5. Update documentation

---

## See Also

- [cluster-setup.md](../cluster-setup.md) — cluster configuration
- [upgrade-k3s.md](upgrade-k3s.md) — upgrade runbook

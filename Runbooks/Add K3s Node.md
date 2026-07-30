---
type: runbook
target: "[[K3s Cluster]]"
tags:
  - runbook
  - kubernetes
---

# Add K3s Node

> [!info] When to use this
> Adding a worker to the cluster. The free U1 shelf in [[Rack Layout]] is
> reserved for exactly this.

## Before you start

- Hostname per [[Conventions]], address per [[IP Plan]].
- A free switch port. [[hobbiton.shire]] is full — see [[Switch Ports]];
  [[greenway.shire]] has five free.
- The cluster join token from [[isengard.shire]]. Never write it into this
  vault.

## Steps

1. Create the node note from the `Node` template and reserve the hostname and
   IP.
2. Install the OS, set the static IP and hostname.
3. Cable it to a free port on [[greenway.shire]] and configure that port as an
   access port on VLAN 20.
4. Install the K3s agent, pointing at [[isengard.shire]] with the join token.
5. Apply any labels or taints the workloads need.

## Verify

- `kubectl get nodes` shows the node as `Ready`.
- A test pod schedules onto it.

## Afterwards

- Complete the node note and add rows to [[Node Registry]] and [[Switch Ports]].
- Update the node list in [[K3s Cluster]] and the rack slot in [[Rack Layout]].
- Record it in [[Changelog]].

## Related

- [[K3s Cluster]]
- [[Upgrade K3s]]

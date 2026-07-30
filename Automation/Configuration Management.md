---
type: note
tags:
  - automation
  - planning
---

# Configuration Management

**Current state: none.** Every node is configured by hand.

That is the honest reason so many pages in this vault are stubs — there is no
machine-readable configuration to describe, so everything has to be written from
memory.

## Candidates

| Tool | Fits |
|---|---|
| Ansible | Agentless, idempotent. Suits the Debian and Ubuntu VMs and the whole SBC fleet. |
| Terraform | Provisioning: Proxmox VMs, DNS records. Pairs with Ansible rather than replacing it. |

Ansible first. An inventory covering [[Node Registry]] plus a playbook that
installs node_exporter everywhere would close the biggest gap in
[[Monitoring Stack]] and produce the inventory as a side effect.

## To document

> [!todo] Stub
> - Inventory structure and where it lives
> - Playbooks for updates, users, exporter rollout
> - Terraform provider configuration for Proxmox
> - Running it from [[GitLab CI]]

## Related

- [[GitLab CI]]
- [[Monitoring Stack]]
- [[Node Registry]]

---
type: moc
tags:
  - moc
  - runbook
---

# Runbooks

Procedures, written to be followed while something is broken or being changed.

## Proxmox

- [[Create Proxmox VM]]
- [[Add Disk Passthrough]]

## Kubernetes

- [[Add K3s Node]]
- [[Upgrade K3s]]

## Missing

Procedures that should exist and do not:

| Runbook | Why it matters |
|---|---|
| Restore a VM from backup | [[Backup Strategy]] has no tested restore path |
| Recover OPNsense | [[the.shire]] failing takes the whole lab offline |
| Add an IoT device | Seven exist and none of the process is written down |
| Rotate cold storage | Named in [[Backup Strategy]], never described |

## House style

Verb-first titles. Numbered steps in the imperative. Every runbook states its
prerequisites, how to verify it worked, and how to undo it. If a step cannot be
undone, say so — that is the most useful line on the page.

## Related

- [[Conventions]]
- [[Compute]]

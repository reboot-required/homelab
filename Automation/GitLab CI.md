---
type: note
tags:
  - automation
  - ci
---

# GitLab CI

Pipelines for projects hosted on [[erebor.shire]].

| Component | Where |
|---|---|
| GitLab instance | [[erebor.shire]] — 10.136.20.102 |
| Runner | Workload on the [[K3s Cluster]], `gitlab` namespace |

The runner lives on the cluster on purpose: build load lands on
[[rohan.shire]] and [[gondor.shire]] rather than on the VM holding the
repositories.

## To document

> [!todo] Stub
> - Runner registration and executor type
> - Which repositories actually have pipelines
> - Shared pipeline stages, if any
> - Container registry usage
> - CI/CD variables — that they exist and their scope, never their values
> - Deployment pipelines targeting K3s or the Proxmox VMs

## An obvious candidate

This vault is a git repository of Markdown. A pipeline that checks for broken
wikilinks and orphaned notes on push would catch exactly the kind of rot this
restructure was needed to fix.

## Related

- [[GitLab CE]]
- [[K3s Workloads]]
- [[Configuration Management]]

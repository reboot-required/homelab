---
type: service
host: "[[erebor.shire]]"
url: http://10.136.20.102
port: 80
deployment: proxmox-vm
status: running
tags:
  - service
  - git
  - ci
---

# GitLab CE

Self-hosted Git, issue tracking and CI/CD. The source of truth for every
homelab project — including this vault.

## Access

| Property | Value |
|---|---|
| Internal URL | `http://10.136.20.102` |
| Ports | 80 (HTTP), 443 (HTTPS, not yet enabled) |
| Host | [[erebor.shire]] — VM 101, Debian 12 |

## Deployment

Installed from the official package repository on a Debian 12 VM. CI jobs run
elsewhere: the GitLab Runner is a workload on the K3s cluster, so pipeline load
stays off the box holding the repositories. See [[GitLab CI]].

## Dependencies

- [[bill-the-pony.shire]] — hypervisor
- [[K3s Cluster]] — runs the CI runner

## To document

> [!todo] Stub
> - GitLab version and upgrade cadence
> - Backup: `gitlab-backup` schedule and where the tarballs land.
>   Repositories are on the [[Backup Strategy]] critical list and there is
>   currently nothing written about how they are captured.
> - Restore procedure
> - Whether the container registry is enabled

## Future plans

- HTTPS via a local CA
- Container registry
- Runner integration documented properly

## Related

- [[erebor.shire]]
- [[GitLab CI]]
- [[K3s Workloads]]

[Home](../README.md) › [Services](README.md) › GitLab CE

# GitLab CE

> 🚧 This page is a stub. Content to be added.

## Overview

GitLab Community Edition is the self-hosted Git repository manager and CI/CD platform for the homelab. It provides source control, issue tracking, merge requests, and CI/CD pipelines for all homelab projects.

## Host

| Property | Value |
|---|---|
| Hostname | `erebor.shire` |
| IP | 10.136.20.102 |
| VM ID | 101 |
| Hypervisor | `bill-the-pony.shire` |
| OS | Debian 12 |

See [infrastructure/node-registry.md](../infrastructure/node-registry.md) for the authoritative node listing.

## Access

| Property | Value |
|---|---|
| Internal URL | `http://10.136.20.102` |
| Port | 80 (HTTP) / 443 (HTTPS) |

## Deployment

> 🚧 Deployment details to be added.

- Deployed as a Proxmox VM (Debian 12)
- GitLab installed via official package repository

## Configuration Highlights

> 🚧 To be documented.

## Dependencies

- `bill-the-pony.shire` — Proxmox hypervisor
- `rivendell.shire` — storage (if NFS-backed repositories)

## Backup & Recovery

> 🚧 To be documented.

## Runbook

> 🚧 To be documented.

## Future Plans

- Enable HTTPS with a self-signed or local CA certificate
- Configure GitLab Runner integration with K3s cluster
- Enable container registry

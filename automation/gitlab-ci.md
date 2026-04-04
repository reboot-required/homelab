[Home](../README.md) › [Automation](README.md) › GitLab CI

# GitLab CI/CD

> 🚧 This page is a stub. Content to be added.

GitLab CI/CD pipelines are used to automate builds, tests, and deployments for projects hosted on `gondolin.shire` (GitLab CE).

---

## Overview

- GitLab instance: `gondolin.shire` (10.136.20.102)
- CI Runner: GitLab Runner deployed on the K3s cluster (`isengard.shire` / `rohan.shire` / `gondor.shire`)

---

## Planned Content

- GitLab Runner registration and configuration
- Example `.gitlab-ci.yml` pipeline definitions
- Pipeline stages used across homelab repositories
- Docker image registry usage (if enabled)
- Secrets and CI/CD variable management (no hardcoded values)
- Deployment pipelines to K3s or Proxmox VMs

---

## See Also

- [services/gitlab.md](../services/gitlab.md) — GitLab service page
- [compute/kubernetes/workloads.md](../compute/kubernetes/workloads.md) — K3s workloads (GitLab Runner)

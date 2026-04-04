[Home](../README.md) › [Automation](README.md) › Configuration Management

# Configuration Management

> 🚧 This page is a stub. Content to be added.

Configuration management tooling is planned for the homelab to automate provisioning, configuration drift detection, and repeatable node setup.

---

## Current State

No configuration management tooling is currently in place. Nodes are configured manually.

---

## Planned Tooling

The following tools are candidates for adoption:

| Tool | Use Case |
|---|---|
| **Ansible** | Idempotent, agentless configuration — suitable for Debian/Ubuntu VMs and Raspberry Pi nodes |
| **Terraform** | Infrastructure provisioning (Proxmox VMs, DNS records, network config) |

---

## Planned Content

- Ansible inventory structure (targeting all homelab nodes)
- Playbook examples for common tasks (package updates, user management, service deployment)
- Terraform provider configuration for Proxmox
- Integration with GitLab CI/CD pipelines for automated runs

---

## See Also

- [gitlab-ci.md](gitlab-ci.md) — GitLab CI/CD pipelines
- [compute/proxmox/README.md](../compute/proxmox/README.md) — Proxmox configuration

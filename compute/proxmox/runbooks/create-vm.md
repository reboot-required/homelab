[Home](../../../README.md) › [Compute](../../README.md) › [Proxmox](../README.md) › Runbook: Create VM

# Runbook: Create a New VM

> 🚧 This page is a stub. Content to be added.

---

## Prerequisites

- Access to Proxmox web UI at `http://10.136.20.10:8006`
- ISO image uploaded to Proxmox storage (or URL for download)
- IP address reserved in [node-registry.md](../../../infrastructure/node-registry.md)

---

## Planned Steps

1. Log in to Proxmox web UI
2. Click **Create VM**
3. Set VM ID and hostname (following `.shire` naming convention)
4. Select ISO image
5. Configure CPU, RAM, and disk
6. Configure network bridge (VLAN-aware)
7. Start VM and complete OS installation
8. Set static IP, update hostname, and register in node registry

---

## See Also

- [vm-overview.md](../vm-overview.md) — existing VM table
- [add-disk-passthrough.md](add-disk-passthrough.md) — disk passthrough runbook

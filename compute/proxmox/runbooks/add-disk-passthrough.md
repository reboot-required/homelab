[Home](../../../README.md) › [Compute](../../README.md) › [Proxmox](../README.md) › Runbook: Add Disk Passthrough

# Runbook: Add Disk Passthrough

> 🚧 This page is a stub. Content to be added.

Disk passthrough allows a VM (e.g., `rivendell.shire` running TrueNAS) to access a physical disk directly, bypassing the Proxmox storage layer for improved performance and reliability.

---

## Planned Steps

1. Identify the target disk by ID (`/dev/disk/by-id/`)
2. Detach or ensure the disk is not in use by the host
3. Add the disk to the VM configuration via Proxmox CLI or UI
4. Verify the disk appears in the guest OS
5. Update documentation and node registry if needed

---

## See Also

- [vm-overview.md](../vm-overview.md) — VM table (note `rivendell.shire` disk passthrough)
- [storage/truenas.md](../../../storage/truenas.md) — TrueNAS configuration

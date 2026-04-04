[Home](../../../README.md) › [Compute](../../README.md) › [Proxmox](../README.md) › Runbook: Replace Proxmox Host

# Runbook: Replace the Proxmox Host

Use this checklist when the incoming **AMD Ryzen 5 5600X / A520 mini-ITX** platform is ready to be installed in the rack. It is intentionally written as a planning runbook so the live-state documentation can stay accurate until the hardware is operational.

---

## Scope

- New Proxmox host hardware: AMD Ryzen 5 5600X on an A520 mini-ITX mainboard
- Target workload: a larger kernel-build VM in addition to the existing VM estate on `bill-the-pony.shire`
- Rack change: permanently remove Raspberry Pi hardware from the rack

---

## Pre-Cutover Checklist

- [ ] Confirm whether the new host will reuse `bill-the-pony.shire` and `10.136.20.100` or be introduced under a new hostname.
- [ ] Capture the final hardware bill of materials: CPU, board, RAM, storage, NICs, chassis, and rack mounting method.
- [ ] Export the current Proxmox VM inventory from `bill-the-pony.shire`, including VM IDs, disk locations, bridge mappings, and passthrough devices.
- [ ] Verify that the heavyweight kernel-build VM still maps to `khazad-dum.shire`, or record the new hostname before updating the docs.
- [ ] Identify every Raspberry Pi service that is being retired, migrated, or kept online outside the rack.
- [ ] Take fresh backups and test at least one restore path before any shutdown window starts.

---

## Documentation Files to Update During Integration

| File | Required change after hardware is live |
|---|---|
| [infrastructure/hardware-summary.md](../../../infrastructure/hardware-summary.md) | Replace the temporary planning notes with final hardware specs, rack placement, and refreshed power estimates |
| [infrastructure/rack-layout.md](../../../infrastructure/rack-layout.md) | Remove Raspberry Pi rack slots and publish the post-upgrade ASCII layout |
| [infrastructure/node-registry.md](../../../infrastructure/node-registry.md) | Update the Proxmox host entry only after the hostname/IP decision is final |
| [compute/proxmox/README.md](../README.md) | Document the new host OS, management notes, and hardware configuration |
| [compute/proxmox/vm-overview.md](../vm-overview.md) | Adjust VM resource allocations, especially the kernel-build VM |
| [compute/proxmox/backup-strategy.md](../backup-strategy.md) | Record the new snapshot/backup schedule and migration safety window |
| [storage/backup.md](../../../storage/backup.md) | Update cross-platform backup, retention, and recovery notes |
| [CHANGELOG.md](../../../CHANGELOG.md) | Add the dated cutover entry with affected nodes |

---

## Migration and Downtime Planning

### Critical services to review

- `erebor.shire` — GitLab CE
- `radagast.shire` — n8n
- `palantir.shire` — Grafana + Prometheus
- `weathertop.shire` — Home Assistant OS
- `rivendell.shire` — TrueNAS Scale

### Downtime checklist

- [ ] Announce the maintenance window for any VM shutdowns or storage moves.
- [ ] Snapshot or back up each critical VM immediately before migration.
- [ ] Record the order of shutdown, migration, boot, and service validation.
- [ ] Validate network reachability, DNS, and storage mounts before reopening access.
- [ ] Confirm that monitoring on `palantir.shire` reflects the new host after cutover.

---

## Raspberry Pi Rack Decommission Checklist

- [ ] Remove rack-specific references to `overhill.shire`, `bywater.shire`, and `stock.shire` from diagrams and inventory tables.
- [ ] Decide whether `tuckborough.shire` remains an off-rack development system.
- [ ] Confirm whether `gondolin.shire` continues as the MQTT IoT gateway or is replaced by a VM-based service.
- [ ] Archive retired Raspberry Pi build notes instead of leaving them in active rack documentation.

---

## Post-Cutover Verification

- [ ] Update every affected document in the table above with final hardware and networking details.
- [ ] Verify that every hostname remains wrapped in backticks and matches [node-registry.md](../../../infrastructure/node-registry.md).
- [ ] Review backup coverage for the new Proxmox host and the kernel-build VM.
- [ ] Add a dated entry to [CHANGELOG.md](../../../CHANGELOG.md) summarizing the completed migration.

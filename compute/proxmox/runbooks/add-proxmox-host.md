[Home](../../../README.md) › [Compute](../../README.md) › [Proxmox](../README.md) › Runbook: Add an Additional Proxmox Host

# Runbook: Add an Additional Proxmox Host

Use this checklist when the incoming **AMD Ryzen 5 5600X / A520 mini-ITX** platform is ready to be installed in the rack. It is intentionally written as a planning runbook so the live-state documentation can stay accurate until the hardware is operational.

---

## Scope

- New Proxmox host hardware: AMD Ryzen 5 5600X on an A520 mini-ITX mainboard
- Topology change: add a second Proxmox node alongside `bill-the-pony.shire`, not a replacement for it
- Target workload: move the heavyweight kernel-build VM `khazad-dum.shire` to the new node
- Hostname: still to be assigned; it must be a Tolkien-themed `.shire` hostname before the node registry is updated
- Rack change: permanently remove Raspberry Pi hardware from the rack

---

## Pre-Cutover Checklist

- [ ] Assign a Tolkien-themed hostname and final management IP to the new Proxmox node.
- [ ] Capture the final hardware bill of materials: CPU, board, RAM, storage, NICs, chassis, and rack mounting method.
- [ ] Export the current Proxmox VM inventory from `bill-the-pony.shire`, including VM IDs, disk locations, bridge mappings, and passthrough devices.
- [ ] Confirm that only `khazad-dum.shire` is planned to move to the new Proxmox node and that the remaining VMs stay on `bill-the-pony.shire`.
- [ ] Identify every Raspberry Pi service that is being retired, migrated, or kept online outside the rack.
- [ ] Take fresh backups and test at least one restore path before any shutdown window starts.

---

## Documentation Files to Update During Integration

| File | Required change after hardware is live |
|---|---|
| [infrastructure/hardware-summary.md](../../../infrastructure/hardware-summary.md) | Replace the temporary planning notes with final hardware specs, rack placement, and refreshed power estimates |
| [infrastructure/rack-layout.md](../../../infrastructure/rack-layout.md) | Remove Raspberry Pi rack slots and publish the post-upgrade ASCII layout |
| [infrastructure/node-registry.md](../../../infrastructure/node-registry.md) | Add the new Proxmox host only after the hostname/IP decision is final |
| [compute/proxmox/README.md](../README.md) | Document the new host OS, management notes, and hardware configuration alongside `bill-the-pony.shire` |
| [compute/proxmox/vm-overview.md](../vm-overview.md) | Note that `khazad-dum.shire` moves to the new host while the rest of the current VM estate remains on `bill-the-pony.shire` |
| [compute/proxmox/backup-strategy.md](../backup-strategy.md) | Record the new snapshot/backup schedule and migration safety window |
| [storage/backup.md](../../../storage/backup.md) | Update cross-platform backup, retention, and recovery notes |
| [CHANGELOG.md](../../../CHANGELOG.md) | Add the dated cutover entry with affected nodes |

---

## Migration and Downtime Planning

### Critical services to review

- `khazad-dum.shire` — kernel / low-level development VM
- Any Raspberry Pi-hosted workload that will be retired or rehomed during the same rack intervention

### Downtime checklist

- [ ] Announce the maintenance window for the `khazad-dum.shire` move and any rack power work.
- [ ] Snapshot or back up `khazad-dum.shire` immediately before migration.
- [ ] Record the order of new-host provisioning, VM migration, boot, and service validation.
- [ ] Validate network reachability, DNS, and storage mounts for `khazad-dum.shire` on the new host before reopening access.
- [ ] Confirm whether monitoring on `palantir.shire` should add the new Proxmox node after cutover.

---

## Raspberry Pi Rack Decommission Checklist

- [ ] Remove rack-specific references to `overhill.shire`, `bywater.shire`, and `stock.shire` from diagrams and inventory tables.
- [ ] Decide whether `tuckborough.shire` remains an off-rack development system.
- [ ] Confirm whether `gondolin.shire` continues as the MQTT IoT gateway or is replaced by a VM-based service.
- [ ] Archive retired Raspberry Pi build notes instead of leaving them in active rack documentation.

---

## Post-Cutover Verification

- [ ] Update every affected document in the table above with the new host's final hardware, hostname, IP, and networking details.
- [ ] Verify that every hostname remains wrapped in backticks and matches [node-registry.md](../../../infrastructure/node-registry.md).
- [ ] Review backup coverage for both Proxmox hosts and the migrated kernel-build VM.
- [ ] Add a dated entry to [CHANGELOG.md](../../../CHANGELOG.md) summarizing the completed migration.

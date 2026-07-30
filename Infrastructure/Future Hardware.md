---
type: note
tags:
  - infrastructure
  - planning
---

# Future Hardware

Planned and considered hardware changes. Nothing here is bought.

## Dedicated NAS

[[rivendell.shire]] runs TrueNAS Scale as a VM on [[bill-the-pony.shire]], with
ZFS sitting on virtual disks. That is fine for a lab and wrong for storage you
care about — ZFS cannot manage disks it cannot see.

| Step | Effect |
|---|---|
| Disk pass-through — see [[Add Disk Passthrough]] | ZFS gets the real disks. Cheap, no new hardware. |
| Dedicated physical NAS | Storage survives the hypervisor. The actual goal. |

## Proxmox host upgrade

Replace the N150 mini-PC in [[bill-the-pony.shire]] with a Ryzen 9 mini-PC.
Seven VMs on an N150 is the tightest constraint in the lab, and per
[[Power Budget]] consolidation saves more power than retiring SBCs.

## Additional access points

[[bree.shire]] currently serves all three SSIDs as virtual APs from one radio
pair. Deploying `green-dragon-inn.shire` and `prancing-pony.shire` as separate
physical APs would improve whole-home coverage — at the cost of two more PoE
ports on [[greenway.shire]], which has five free.

## Rack expansion

One free U at the bottom of the rack — see [[Rack Layout]] — reserved for a
fourth K3s node. Beyond that, additional U space and patch panels.

## Related

- [[Hardware Summary]]
- [[Rack Layout]]
- [[Future Services]]

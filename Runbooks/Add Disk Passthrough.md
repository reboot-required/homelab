---
type: runbook
target: "[[bill-the-pony.shire]]"
tags:
  - runbook
  - proxmox
  - storage
---

# Add Disk Passthrough

> [!info] When to use this
> Giving a guest direct access to a physical disk instead of a virtual one. The
> open case is [[rivendell.shire]] — see the reasoning in [[TrueNAS Scale]].

> [!warning] This touches real disks
> Passing through a disk that the host is still using will corrupt it. Confirm
> the host has no mount, no LVM volume and no ZFS pool on the target before
> attaching it anywhere.

## Before you start

- Know exactly which physical disk you mean, by `/dev/disk/by-id/` path — never
  by `/dev/sdX`, which is not stable across reboots.
- A current backup of anything on that disk.
- The guest shut down.

## Steps

1. On the Proxmox host, list disks by stable ID:
   `ls -l /dev/disk/by-id/`
2. Identify the target and confirm the host is not using it — check `lsblk`,
   `mount`, `pvs` and `zpool status`.
3. Attach it to the guest:
   `qm set <vmid> -scsi<n> /dev/disk/by-id/<disk-id>`
4. Start the guest.
5. Confirm the guest sees a raw disk of the expected size and, for a NAS guest,
   that SMART data is readable — that being the point of the exercise.

## Verify

- The guest reports the correct model and capacity.
- SMART attributes are visible from inside the guest.
- The host still shows no filesystem of its own on that disk.

## Rollback

Shut the guest down and detach:
`qm set <vmid> -delete scsi<n>`

Detaching does not erase the disk. Anything the guest wrote — a ZFS label, for
instance — is still there.

## Afterwards

- Note the disk assignment on the guest's node note.
- Record it in [[Changelog]].

## Related

- [[TrueNAS Scale]]
- [[rivendell.shire]]
- [[Proxmox VE]]

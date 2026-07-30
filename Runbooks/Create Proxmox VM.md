---
type: runbook
target: "[[bill-the-pony.shire]]"
tags:
  - runbook
  - proxmox
---

# Create Proxmox VM

> [!info] When to use this
> Adding a new guest to [[bill-the-pony.shire]].

## Before you start

- Check [[VM Overview]] for free capacity. The host is already oversubscribed on
  memory — decide what the new guest may take before you allocate it.
- Pick a hostname per [[Conventions]] and an address per [[IP Plan]].
- Have the ISO on Proxmox storage, or a URL to fetch it.
- Access to `http://10.136.20.100:8006`.

## Steps

1. Reserve the hostname and IP by creating the node note first, from the
   `Node` template. Documenting after the fact is how [[gondolin.shire]] ended
   up without a recorded address.
2. In the Proxmox UI, **Create VM**. Use the next free VM ID — [[VM Overview]]
   has the current list.
3. Set the name to the hostname without the `.shire` suffix.
4. Select the ISO.
5. Allocate CPU, RAM and disk. Be conservative; see the oversubscription warning
   in [[VM Overview]].
6. Attach the network device to the VLAN-aware bridge. Leave the VLAN tag empty
   for VLAN 20 — it is the native VLAN on the uplink. Set a tag only if the
   guest genuinely belongs on another segment, as [[weathertop.shire]] does.
7. Start the VM and install the OS.
8. Set the static IP, the hostname and the `.shire` search domain.
9. Add a DNS host override on [[the.shire]] — see [[DNS]].

## Verify

- `ping <hostname>.shire` resolves and answers from another homelab node.
- The guest appears in the Proxmox guest list with the intended resources.

## Afterwards

- Fill in the node note you created in step 1.
- Add a row to [[Node Registry]].
- If it runs a service, add a service note from the `Service` template and a row
  to [[Services]].
- Record it in [[Changelog]].

## Related

- [[Proxmox VE]]
- [[VM Overview]]
- [[Add Disk Passthrough]]

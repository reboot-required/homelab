---
type: journal
date: 2026-07-30
linkedin: false
tags:
  - journal
  - documentation
---

# Rebuilding the Docs as an Obsidian Vault

The category-based layout from
[[2026-04-04 Homelab Documentation Kickoff|April]] was the right instinct and
the wrong shape. Three months later the folders were full of pages that were
mostly cross-references to each other, and the same facts — hostnames, IPs, VM
resources — appeared in four places and had already started to disagree.

So: branched back to before that restructure and rebuilt it as an Obsidian
vault.

## What changed

**One note per thing.** Every machine has its own note under `Nodes/`. Its IP,
role, uplink and rack position live there and nowhere else. [[Node Registry]] is
now explicitly an index, not a second source of truth — there is no second copy
to forget to update.

**Wikilinks everywhere.** Every hostname is a link, which means the backlink
pane answers "what touches this box?" without grepping, and the graph view shows
the shape of the lab.

**Mermaid instead of ASCII.** The topology and rack diagrams are text now —
they diff, they render in Obsidian and on GitHub, and updating one is editing a
line rather than realigning box drawings.

## What it turned up

Rewriting the whole thing surfaced problems that reading it never did. Once
facts sit next to each other, the ones that disagree are obvious:

- The **MQTT path is impossible as documented.** The sensors are on VLAN 30, the
  broker is on VLAN 20, and the firewall denies exactly that. One of the three
  pages is wrong. Tracked on [[gondolin.shire]].
- **[[gondolin.shire]] has no IP on record** and no switch port. The only node
  in the lab like that.
- **[[hobbiton.shire]] is full**, yet four SBCs claim to be wired somewhere.
  Something is cabled in a way nothing describes.
- **[[Prometheus]] is documented twice**, once as a VM service and once as a K3s
  workload.
- **The monitoring stack scrapes nothing** — node exporters are planned
  everywhere and deployed nowhere.
- **[[bree.shire]] is statically addressed inside the DHCP pool.**
- **VM resource figures disagreed** between two tables. Reconciled to the lower
  set.
- **[[gondolin.shire]] was missing from the power budget** entirely.

None of these are new. They have all been true for months. They just weren't
visible while every page repeated everything.

## What's next

Close the open questions above — most are five minutes with a browser tab open
on [[the.shire]]. Then node_exporter everywhere, which is the change that turns
[[Monitoring Stack]] from installed into working.

---

*The documentation was never the point. Finding out what I'd got wrong was.*

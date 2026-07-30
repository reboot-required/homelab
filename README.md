# The Shire — Homelab

Documentation for a self-hosted homelab built on a Middle-earth hostname scheme
with the `.shire` domain suffix.

**This repository is an [Obsidian](https://obsidian.md) vault.** Clone it and
open the folder as a vault to get backlinks, the graph view and working
`[[wikilinks]]`. It also reads fine on GitHub — the Mermaid diagrams render
here too — but wikilinks are plain text in this view, so navigation is better in
Obsidian.

Start at **[Home.md](Home.md)**.

## Layout

| Folder | Contents |
|---|---|
| [`Nodes/`](Nodes/) | One note per machine — the authoritative record for each |
| [`Infrastructure/`](Infrastructure/) | Hardware, rack layout, power budget |
| [`Networking/`](Networking/) | Topology, VLANs, firewall, DNS, wireless |
| [`Compute/`](Compute/) | Proxmox VE and the K3s cluster |
| [`Storage/`](Storage/) | TrueNAS and backup strategy |
| [`Services/`](Services/) | One note per self-hosted service |
| [`IoT/`](IoT/) | Sensors, smart plugs, MQTT |
| [`Monitoring/`](Monitoring/) | Prometheus, Grafana, alerting |
| [`Automation/`](Automation/) | CI/CD, configuration management |
| [`Runbooks/`](Runbooks/) | Step-by-step procedures |
| [`Journal/`](Journal/) | Lab diary |
| [`_meta/`](_meta/) | Conventions and note templates |
| [`Assets/`](Assets/) | Attachments and legacy diagram sources |

## Conventions

Facts live in exactly one place — a node's IP is on its node note, not repeated
in five tables. [`_meta/Conventions.md`](_meta/Conventions.md) has the full set:
naming scheme, frontmatter schema, link style, and the rule that diagrams are
Mermaid and matrices are tables.

No secrets are stored in this repository — not passwords, keys, tokens or
certificates.

## Status

Much of the vault is deliberately marked as a stub. Pages state what is not yet
documented rather than implying completeness, and
[`Home.md`](Home.md#known-open-questions) lists the contradictions this
documentation currently contains.

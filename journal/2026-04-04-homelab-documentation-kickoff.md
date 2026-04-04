---
date: 2026-04-04
tags: [documentation, infrastructure, homelab]
linkedin: true
---

# Homelab Documentation Kickoff

Today marks the beginning of a proper documentation effort for my homelab. What started as a collection of scattered notes and a couple of Markdown files has grown into a full category-based documentation structure — and it's about time.

## What Changed

The repository now has a clear, opinionated folder layout:

- **`infrastructure/`** — hardware summary, node registry, rack layout
- **`networking/`** — full network topology, VLANs, DNS, OPNsense, wireless
- **`compute/`** — Proxmox VE and K3s Kubernetes cluster documentation
- **`storage/`** — TrueNAS Scale and backup strategy
- **`services/`** — all running services with dedicated pages
- **`iot/`** — ESP8266 sensors and smart plugs
- **`automation/`** — GitLab CI and future configuration management
- **`monitoring/`** — Prometheus + Grafana stack
- **`journal/`** — this diary

## Why Bother?

A homelab without documentation is just a pile of hardware that only works when you remember what you did six months ago. Documentation forces clarity — it reveals inconsistencies, highlights gaps, and makes the whole setup transferable (even if only to future-me).

The Lord of the Rings hostname scheme (`.shire` domain, Middle-earth names for every node) has been a fun touch that also makes the infrastructure feel like a coherent world rather than a random collection of machines.

## What's Next

Most pages are stubs for now. The goal over the coming weeks is to fill in the details — especially for services, monitoring, and the K3s cluster — and to start using this documentation as the single source of truth for the homelab.

---

*First entry. More to follow.*

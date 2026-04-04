[Home](../README.md) › [Services](README.md) › Future Services

# Future Services

This page is a curated, opinionated shortlist of services recommended for this homelab. Each entry includes a description, why it fits the specific homelab setup, and a suggested deployment target.

---

## Vaultwarden

**Category:** Security  
**Repository:** [dani-garcia/vaultwarden](https://github.com/dani-garcia/vaultwarden)

Vaultwarden is a lightweight, self-hosted implementation of the Bitwarden password manager API. It provides a full-featured password vault — including browser extensions and mobile apps — while running on minimal hardware. All credentials are stored locally, never leaving the homelab.

**Why it fits:** The homelab already manages a complex set of services with many credentials. A centralized, self-hosted password manager is essential for security hygiene and removes dependence on cloud password managers.

**Suggested deployment:** Docker container on `tuckborough.shire` (Raspberry Pi 5B) or as a new Proxmox VM on `bill-the-pony.shire`. Requires persistent storage for the SQLite database (backed up to `rivendell.shire`).

---

## Uptime Kuma

**Category:** Monitoring  
**Repository:** [louislam/uptime-kuma](https://github.com/louislam/uptime-kuma)

Uptime Kuma is a lightweight, self-hosted service uptime monitoring tool. It provides HTTP/TCP/ICMP checks with a clean dashboard, historical uptime graphs, and configurable alerting (email, Telegram, webhook, etc.). It complements Prometheus and Grafana by focusing on service availability rather than metrics.

**Why it fits:** With 7+ services running on the homelab, quick visibility into service availability is valuable. Uptime Kuma is simple to deploy, has very low resource requirements, and fills the gap between Grafana metrics dashboards and raw availability monitoring.

**Suggested deployment:** Docker container on `tuckborough.shire` or as a lightweight VM on `bill-the-pony.shire`. Can coexist with Vaultwarden on the same host.

---

## Nextcloud

**Category:** Productivity / File Sync  
**Website:** [nextcloud.com](https://nextcloud.com)

Nextcloud is a self-hosted productivity platform offering file sync (similar to Dropbox), calendar (CalDAV), contacts (CardDAV), and a large ecosystem of apps. It replaces Google Drive, Google Calendar, and related cloud services with a fully self-controlled alternative.

**Why it fits:** The homelab already has `rivendell.shire` (TrueNAS Scale) providing storage infrastructure. Nextcloud can use TrueNAS NFS or SMB shares as its data backend, providing a polished interface to existing storage with multi-device sync, web access, and mobile apps.

**Suggested deployment:** Proxmox VM on `bill-the-pony.shire` (Debian 12, Docker or direct install), backed by NFS mount from `rivendell.shire`. Alternatively as an AIO (All-in-One) Docker container on `tuckborough.shire` for lighter usage.

---

## Immich

**Category:** Photo Management  
**Repository:** [immich-app/immich](https://github.com/immich-app/immich)

Immich is a self-hosted, high-performance photo and video management solution — a full Google Photos alternative. It features automatic mobile backup, face recognition, object detection, map view, and a polished web and mobile UI. It uses machine learning for media classification.

**Why it fits:** Photo management is a common pain point for homelab owners who want to avoid cloud photo storage. `valinor.shire` (Mac Mini M4) has strong computational capabilities that could accelerate ML tasks if needed, but Immich can also run comfortably on a Proxmox VM. Storage is provided by `rivendell.shire`.

**Suggested deployment:** Proxmox VM on `bill-the-pony.shire` with Docker Compose, using NFS-mounted storage from `rivendell.shire` for the media library. RAM requirement: 4–8 GB for ML features.

---

## Nginx Proxy Manager

**Category:** Networking / Reverse Proxy  
**Repository:** [NginxProxyManager/nginx-proxy-manager](https://github.com/NginxProxyManager/nginx-proxy-manager)

Nginx Proxy Manager (NPM) provides a user-friendly web UI for managing Nginx reverse proxy configurations, including SSL/TLS certificate management via Let's Encrypt. It enables friendly domain names (e.g., `grafana.shire`) and HTTPS for all internal services without manually editing Nginx config files.

**Why it fits:** As the number of services grows, accessing them by IP and port becomes unwieldy. NPM would sit in front of all services and provide clean internal URLs. Paired with OPNsense's local DNS overrides on `the.shire`, all services become accessible via hostnames with automatic certificate management.

**Suggested deployment:** Docker container or Proxmox VM on `bill-the-pony.shire`, with a dedicated IP (or the existing homelab IP with port 80/443 forwarded). DNS entries managed via OPNsense Unbound on `the.shire`.

> **Alternative:** [Caddy](https://caddyserver.com/) — a simpler reverse proxy with automatic HTTPS that may be more maintainable for a homelab of this size.

---

## Authentik

**Category:** Identity & Access Management  
**Website:** [goauthentik.io](https://goauthentik.io)

Authentik is a self-hosted identity provider and SSO (Single Sign-On) platform. It supports OAuth2, OIDC, SAML, and LDAP, allowing all homelab services to use a single login. It also provides user management, MFA, and an application portal.

**Why it fits:** As the service count grows, managing separate credentials for each service becomes a security and usability burden. Authentik integrates with GitLab, Grafana, n8n, Nextcloud, and many other services via OIDC/OAuth2, providing a unified authentication experience. Complements Vaultwarden well.

**Suggested deployment:** Proxmox VM on `bill-the-pony.shire` (Debian 12, Docker Compose). Requires PostgreSQL and Redis — typically bundled in the official Docker Compose setup. Minimum 2 vCPU, 2–4 GB RAM.

---

## Portainer

**Category:** Container Management  
**Website:** [portainer.io](https://www.portainer.io)

Portainer is a web-based container management UI for Docker and Kubernetes. It provides a visual interface for managing containers, images, volumes, networks, and stacks without needing CLI access. It supports both Docker standalone and Docker Swarm, and has a Kubernetes integration.

**Why it fits:** `valinor.shire` already runs Docker containers (OpenWebUI). `tuckborough.shire` is used for local app testing. Portainer would give a unified view of all Docker workloads across hosts, simplifying container lifecycle management. Also useful for managing K3s via the Kubernetes UI.

**Suggested deployment:** Docker container on `tuckborough.shire` or `valinor.shire`. The Portainer agent can be deployed on all Docker hosts for centralized management.

---

## Paperless-ngx

**Category:** Document Management  
**Repository:** [paperless-ngx/paperless-ngx](https://github.com/paperless-ngx/paperless-ngx)

Paperless-ngx is a document management system that scans, indexes, and organizes physical and digital documents. It uses OCR to make documents searchable, supports automatic tagging and classification, and provides a clean web UI for browsing the document archive.

**Why it fits:** Digitizing and indexing physical documents (bills, contracts, receipts) is a common homelab use case. Paperless-ngx integrates well with existing infrastructure: documents can be stored on `rivendell.shire` (TrueNAS NFS), and the service can run as a lightweight VM or Docker container.

**Suggested deployment:** Docker Compose on `tuckborough.shire` (Raspberry Pi 5B) or a Proxmox VM on `bill-the-pony.shire`. Requires PostgreSQL and Redis (bundled in the official Docker Compose setup). Storage backend: NFS from `rivendell.shire`.

---

## Frigate

**Category:** Security / Home Automation  
**Repository:** [blakeblackshear/frigate](https://github.com/blakeblackshear/frigate)

Frigate is an AI-powered network video recorder (NVR) with real-time object detection. It processes camera streams locally using a hardware accelerator (Google Coral USB TPU, or GPU via NVIDIA/AMD), detecting motion and specific objects (people, cars, animals) with high accuracy. It integrates natively with Home Assistant.

**Why it fits:** `weathertop.shire` (Home Assistant OS) is already the home automation hub. Adding Frigate would extend the smart home setup with intelligent camera monitoring. Native Home Assistant integration means detections trigger automations, notifications, and logging without cloud dependencies.

**Suggested deployment:** Dedicated Proxmox VM on `bill-the-pony.shire` with hardware passthrough (Coral USB TPU or Intel Quick Sync for hardware-accelerated decoding), or a separate mini-PC if camera stream processing load is high. Camera storage on `rivendell.shire` (TrueNAS NFS).

---

## Not Included

- **Ollama** — the homelab uses **LM Studio** on `valinor.shire` for LLM inference. Ollama is an alternative and is intentionally excluded.

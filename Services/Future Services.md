---
type: note
tags:
  - services
  - planning
---

# Future Services

Shortlist, in rough order of what this lab would actually benefit from. Nothing
here is deployed.

## Worth doing first

### Nginx Proxy Manager

**Reverse proxy with a UI and Let's Encrypt integration.**
[Repository](https://github.com/NginxProxyManager/nginx-proxy-manager)

Every service in [[Services]] is currently an IP and a port. A reverse proxy in
front of them, paired with DNS overrides on [[the.shire]], turns all of them
into names — and gives them TLS at the same time. It is the change that makes
every other service on this page nicer to run.

Deploy on [[tuckborough.shire]] or as a VM on [[bill-the-pony.shire]].

> **Alternative:** [Caddy](https://caddyserver.com/) — automatic HTTPS, no UI,
> less to maintain. For a lab this size that is arguably the better trade.

### Uptime Kuma

**Service availability monitoring.**
[Repository](https://github.com/louislam/uptime-kuma)

[[Prometheus]] currently has no node exporters deployed, which means there is no
alerting on anything. Uptime Kuma is an afternoon of work and answers "is it
up?" for all eight services — worth having even after the metrics stack is
finished, because it fails independently of it.

Deploy on [[tuckborough.shire]]. Very low resource requirements.

### Vaultwarden

**Self-hosted Bitwarden-compatible password vault.**
[Repository](https://github.com/dani-garcia/vaultwarden)

The lab already has more credentials than can be remembered, and
[[Conventions]] forbids writing any of them down here — which only works if
there is somewhere proper to put them.

Deploy on [[tuckborough.shire]] or as a VM. SQLite database needs to be on the
[[Backup Strategy]] critical list from day one.

## Bigger projects

### Nextcloud

**File sync, calendar and contacts.** [nextcloud.com](https://nextcloud.com)

[[rivendell.shire]] already provides the storage; Nextcloud puts a usable
interface and mobile sync on top. Worth doing *after* the disk pass-through
question in [[TrueNAS Scale]] is settled — do not build a sync target on storage
that is not trusted yet.

VM on [[bill-the-pony.shire]], backed by NFS from [[rivendell.shire]].

### Immich

**Photo and video management with local ML.**
[Repository](https://github.com/immich-app/immich)

A Google Photos replacement. Needs 4–8 GB RAM for the ML features — which
[[VM Overview]] shows the hypervisor does not currently have spare. This one
waits for the host upgrade in [[Future Hardware]].

### Authentik

**Identity provider and SSO.** [goauthentik.io](https://goauthentik.io)

Single sign-on across GitLab, Grafana, n8n and Nextcloud via OIDC. Pairs with
Vaultwarden: the vault holds what SSO cannot cover.

Needs PostgreSQL and Redis, 2 vCPU and 2–4 GB. Only worth it once there are
enough services behind it to justify the moving parts.

### Paperless-ngx

**Document management with OCR.**
[Repository](https://github.com/paperless-ngx/paperless-ngx)

Scans, OCRs and indexes bills and contracts. Storage from [[rivendell.shire]],
PostgreSQL and Redis bundled in the official compose file.

### Frigate

**NVR with local object detection.**
[Repository](https://github.com/blakeblackshear/frigate)

Integrates natively with [[Home Assistant]] on [[weathertop.shire]], so
detections become automations. Wants a Coral USB TPU or Intel Quick Sync passed
through, and there are no cameras yet — this is the furthest out.

## Portainer

**Container management UI.** [portainer.io](https://www.portainer.io)

Would give one view over the Docker workloads on [[valinor.shire]] and
[[tuckborough.shire]], plus the K3s cluster. Useful, but it manages complexity
rather than removing it — worth revisiting once there are more containers than
can be tracked by hand.

## Deliberately not

**Ollama** — [[LLM Server]] uses LM Studio on [[valinor.shire]]. Running both
would mean two model libraries and two ways to be wrong about which is serving.

## Related

- [[Services]]
- [[Future Hardware]]

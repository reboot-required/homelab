[Home](../README.md) › [Services](README.md) › LLM Server

# LLM Server

> 🚧 This page is a stub. Content to be added.

## Overview

The LLM server provides local large language model inference for the homelab, using **LM Studio** as the inference backend and **OpenWebUI** as the web frontend (running as a Docker container). This allows private, offline LLM usage without sending data to external APIs.

## Host

| Property | Value |
|---|---|
| Hostname | `valinor.shire` |
| IP | 10.136.20.20 |
| Hardware | Mac Mini M4 |
| OS | macOS |

See [infrastructure/node-registry.md](../infrastructure/node-registry.md) for the authoritative node listing.

## Access

| Property | Value |
|---|---|
| OpenWebUI URL | `http://10.136.20.20:3000` |
| LM Studio API | `http://10.136.20.20:1234` |

## Deployment

- **Inference backend:** [LM Studio](https://lmstudio.ai/) — running natively on macOS
- **Frontend:** [OpenWebUI](https://openwebui.com/) — running as a Docker container on `valinor.shire`
- OpenWebUI connects to LM Studio's local API endpoint

## Configuration Highlights

> 🚧 To be documented (model selection, context window, OpenWebUI settings).

## Dependencies

- `valinor.shire` — Mac Mini M4 (the host itself)
- Docker (for OpenWebUI container)

## Backup & Recovery

> 🚧 To be documented.

## Runbook

> 🚧 To be documented.

## Future Plans

- Document loaded models and their use cases
- Expose OpenWebUI via reverse proxy for cleaner URL
- Integrate with n8n workflows for automated LLM tasks

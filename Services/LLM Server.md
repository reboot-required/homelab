---
type: service
host: "[[valinor.shire]]"
url: http://10.136.20.20:3000
port: 3000
deployment: native
status: running
tags:
  - service
  - llm
---

# LLM Server

Local language model inference. Private by construction — nothing leaves the
lab.

## Access

| Property | Value |
|---|---|
| OpenWebUI | `http://10.136.20.20:3000` |
| LM Studio API | `http://10.136.20.20:1234` |
| Host | [[valinor.shire]] — Mac Mini M4, macOS |

## Deployment

Two pieces:

| Component | How |
|---|---|
| [LM Studio](https://lmstudio.ai/) | Native macOS app — the inference backend |
| [OpenWebUI](https://openwebui.com/) | Docker container — the frontend |

OpenWebUI talks to LM Studio's OpenAI-compatible API on `:1234`.

LM Studio runs natively rather than in a container because that is what gets it
access to the M4's unified memory — the reason this box does inference at all.

## To document

> [!todo] Stub
> - Which models are loaded and what each is for
> - Context window and quantisation settings
> - Whether LM Studio starts on boot, or needs a login session
> - OpenWebUI user accounts and data persistence

## Future plans

- Reverse proxy for a real hostname — see [[Future Services]]
- Expose to [[n8n]] for automated LLM tasks

## Related

- [[valinor.shire]]
- [[Power Budget]] — the largest single draw in the lab under load

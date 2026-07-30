---
type: node
hostname: valinor.shire
ip: 10.136.20.20
vlan: 20
category: compute
hardware: Mac Mini M4
os: macOS
role: Local LLM inference
power-idle-w: 10
power-peak-w: 50
status: active
tags:
  - node
  - compute
  - llm
---

# valinor.shire

The LLM box. LM Studio does inference natively on the M4's unified memory;
OpenWebUI runs in Docker in front of it.

## Network

| Property | Value |
|---|---|
| IP | 10.136.20.20 (static) |
| Uplink | [[greenway.shire]] port 1 — access, VLAN 20 |

## Physical

| Property | Value |
|---|---|
| Hardware | Mac Mini M4 |
| Position | Shelf next to the rack — not rack-mounted |
| Power (idle / peak) | 10 W / 50 W |

The single largest power draw in the lab under load, and the only macOS host.

## Runs

- [[LLM Server]] — LM Studio (`:1234`) + OpenWebUI (`:3000`)

## Related

- [[LLM Server]]
- [[Hardware Summary]]

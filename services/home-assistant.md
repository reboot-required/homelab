[Home](../README.md) › [Services](README.md) › Home Assistant

# Home Assistant

> 🚧 This page is a stub. Content to be added.

## Overview

Home Assistant OS is the home automation hub for the homelab. It runs on `weathertop.shire` and manages all IoT devices — ESP8266 temperature/humidity sensors and smart plugs — by subscribing to the MQTT broker on `gondolin.shire`. It has two network interfaces: one on the homelab network for management, and one on IoT VLAN 30 for communication with the MQTT gateway.

## Host

| Property | Value |
|---|---|
| Hostname | `weathertop.shire` |
| IP (homelab) | 10.136.20.107 |
| IP (IoT VLAN 30) | 10.136.30.5 |
| VM ID | 106 |
| Hypervisor | `bill-the-pony.shire` |
| OS | Home Assistant OS |

See [infrastructure/node-registry.md](../infrastructure/node-registry.md) for the authoritative node listing.

## Access

| Property | Value |
|---|---|
| Internal URL | `http://10.136.20.107:8123` |
| Port | 8123 |

## Deployment

> 🚧 Deployment details to be added.

## Configuration Highlights

- Two virtual NICs:
  - `eth0`: homelab VLAN 20 (10.136.20.107) — admin access
  - `eth1`: IoT VLAN 30 (10.136.30.5) — direct L2 communication with IoT devices

## Dependencies

- `bill-the-pony.shire` — Proxmox hypervisor
- MQTT broker: `gondolin.shire` (Raspberry Pi 2B MQTT IoT gateway)
- `proudfoot-00..04.shire` — IoT sensors
- `took-00..01.shire` — smart plugs

## Backup & Recovery

> 🚧 To be documented.

## Runbook

> 🚧 To be documented.

## Future Plans

- Document all configured automations
- Integrate with n8n workflows (`radagast.shire`)
- Expand IoT device coverage

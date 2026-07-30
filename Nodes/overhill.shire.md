---
type: node
hostname: overhill.shire
ip: 10.136.20.22
vlan: 20
category: sbc
hardware: Raspberry Pi B+
role: Hello App
power-idle-w: 1.5
power-peak-w: 3
status: active
tags:
  - node
  - sbc
---

# overhill.shire

The oldest board in the lab, running a single trivial app.

> [!info] Why not `bag-end.shire`
> The obvious Hobbit-hole name is reserved for the home Wi-Fi SSID on
> [[bree.shire]]. See [[Conventions]].

## Network

| Property | Value |
|---|---|
| IP | 10.136.20.22 (static) |
| Uplink | [[hobbiton.shire]] port 8 — access, VLAN 20 |

## Physical

| Property | Value |
|---|---|
| Hardware | Raspberry Pi B+ |
| Rack position | U8, shared Pi panel — see [[Rack Layout]] |
| Power (idle / peak) | 1.5 W / 3 W |

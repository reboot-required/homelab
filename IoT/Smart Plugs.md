---
type: note
tags:
  - iot
  - smart-plug
---

# Smart Plugs

Two plugs, Took family. Power monitoring and remote switching, both on VLAN 30.

| Node | Location | IP |
|---|---|---|
| [[took-00.shire]] | Server rack | 10.136.30.20 |
| [[took-01.shire]] | Living room | 10.136.30.21 |

## The rack plug matters more than it looks

[[took-00.shire]] measures the whole rack. Every figure in [[Power Budget]] is
an estimate, and this plug is the one device in the lab that can replace them
with measurements. Getting its data into [[Grafana]] is the cheapest real
improvement available to the monitoring stack.

> [!warning] Switching the rack plug
> It carries the rack. Remote switching is documented as a capability; treat
> actually using it as pulling the power on [[the.shire]], both switches and the
> hypervisor at once.

## To document

> [!todo] Stub
> - Model and firmware — stock, Tasmota, ESPHome?
> - MQTT topics for measurement and for commands
> - Home Assistant entity names
> - Whether switching is disabled or guarded for the rack plug
> - Measurement interval and accuracy

## Related

- [[MQTT]]
- [[Power Budget]]
- [[Dashboards]]

[Home](../README.md) › [IoT](README.md) › Smart Plugs

# Smart Plugs — Took Family

> 🚧 This page is a stub. Content to be added.

Two smart plugs are deployed for power monitoring and switching. All follow the `took-NN.shire` naming convention (VLAN 30).

---

## Smart Plug Table

| Hostname | Location | Function | IP | Protocol |
|---|---|---|---|---|
| `took-00.shire` | Server rack | Power monitoring & switching | 10.136.30.20 | MQTT → `weathertop.shire` |
| `took-01.shire` | Living room | Power monitoring & switching | 10.136.30.21 | MQTT → `weathertop.shire` |

---

## Planned Content

- Smart plug model and firmware details
- MQTT topic structure
- Home Assistant entity configuration
- Power monitoring dashboard integration (Grafana via `palantir.shire`)
- Wi-Fi SSID: `green-dragon-inn.shire` (VLAN 30, 10.136.30.x)

---

## See Also

- [mqtt.md](mqtt.md) — MQTT broker configuration
- [services/home-assistant.md](../services/home-assistant.md) — Home Assistant integration

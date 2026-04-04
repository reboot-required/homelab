[Home](../README.md) › [IoT](README.md) › Sensors

# IoT Sensors — Proudfoot Family

> 🚧 This page is a stub. Content to be added.

Five ESP8266-based temperature and humidity sensors are deployed around the home and server rack. All follow the `proudfoot-NN.shire` naming convention (VLAN 30).

---

## Sensor Table

| Hostname | Location | Sensors | IP | Protocol |
|---|---|---|---|---|
| `proudfoot-00.shire` | Server rack | Temperature | 10.136.30.10 | MQTT → `weathertop.shire` |
| `proudfoot-01.shire` | Living room | Temperature + Humidity | 10.136.30.11 | MQTT → `weathertop.shire` |
| `proudfoot-02.shire` | Bedroom | Temperature + Humidity | 10.136.30.12 | MQTT → `weathertop.shire` |
| `proudfoot-03.shire` | Bathroom | Temperature + Humidity | 10.136.30.13 | MQTT → `weathertop.shire` |
| `proudfoot-04.shire` | Kitchen | Temperature + Humidity | 10.136.30.14 | MQTT → `weathertop.shire` |

---

## Planned Content

- ESP8266 firmware details (ESPHome or custom firmware)
- MQTT topic structure
- Home Assistant entity configuration
- Wi-Fi SSID: `green-dragon-inn.shire` (VLAN 30, 10.136.30.x)
- DHCP reservation management

---

## See Also

- [mqtt.md](mqtt.md) — MQTT broker configuration
- [services/home-assistant.md](../services/home-assistant.md) — Home Assistant integration

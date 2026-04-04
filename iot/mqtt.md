[Home](../README.md) › [IoT](README.md) › MQTT

# MQTT

> 🚧 This page is a stub. Content to be added.

MQTT (Message Queuing Telemetry Transport) is the lightweight publish/subscribe protocol used for communication between all IoT devices and `weathertop.shire` (Home Assistant OS).

---

## Architecture

All IoT devices on VLAN 30 publish sensor data and receive commands via MQTT. The MQTT broker runs on or is integrated with `weathertop.shire` at **10.136.30.5** (IoT NIC).

---

## Planned Content

- MQTT broker software (Mosquitto or Home Assistant Mosquitto add-on)
- Broker host and port configuration
- Topic naming convention (`homelab/sensors/`, `homelab/plugs/`, etc.)
- QoS levels per topic
- Retained messages and LWT (Last Will and Testament) configuration
- Home Assistant MQTT integration configuration
- Security: ACL, authentication

---

## See Also

- [sensors.md](sensors.md) — ESP8266 sensor configuration
- [smart-plugs.md](smart-plugs.md) — smart plug configuration
- [services/home-assistant.md](../services/home-assistant.md) — Home Assistant integration

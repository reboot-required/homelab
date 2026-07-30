---
type: note
tags:
  - iot
  - sensors
---

# Sensors

Five ESP8266 boards, Proudfoot family. All on VLAN 30 via the
`green-dragon-inn.shire` SSID.

| Node | Location | Measures | IP |
|---|---|---|---|
| [[proudfoot-00.shire]] | Server rack | Temperature | 10.136.30.10 |
| [[proudfoot-01.shire]] | Living room | Temperature, humidity | 10.136.30.11 |
| [[proudfoot-02.shire]] | Bedroom | Temperature, humidity | 10.136.30.12 |
| [[proudfoot-03.shire]] | Bathroom | Temperature, humidity | 10.136.30.13 |
| [[proudfoot-04.shire]] | Kitchen | Temperature, humidity | 10.136.30.14 |

`proudfoot-00.shire` is the odd one out — temperature only, and the only one
measuring equipment rather than rooms. Together with [[took-00.shire]] it makes
the rack's thermal and power behaviour visible, which is the pairing worth
graphing first.

## To document

> [!todo] Stub
> - Firmware: ESPHome or hand-written, and where the source lives
> - Sensor hardware — DHT22, BME280, something else
> - Reporting interval
> - MQTT topics per device
> - Home Assistant entity names
> - Wi-Fi credential handling on the devices
> - OTA update procedure — VLAN 30 permits OTA to the Internet, see
>   [[Firewall Rules]]

## Related

- [[MQTT]]
- [[Home Assistant]]
- [[IoT]]

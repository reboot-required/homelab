# Hardware Setup

## 🔧 System overview

| Device                | Role                          | Notes       | Idle (W) |  Peak (W) |   kWh/Year(≈Avg) |
| --------------------- | ----------------------------- | ----------- | -------: | --------: | ---------------: |
| N150 Router           | opnSense Router, DNS, Adblock |             |        6 |        15 |               92 |
| N150 Mini-PC 01       | Proxmox Server                |             |        8 |        30 |              166 |
| Cel3867U Mini-PC 01   | Cluster Node                  | K3s Master1 |        7 |        25 |              140 |
| N150 Mini-PC 02       | Cluster Node                  | K3s Worker1 |        8 |        30 |              166 |
| N150 Mini-PC 03       | Cluster Node                  | K3s Worker2 |        8 |        30 |              166 |
| Netgear GS108E        | Managed switch                |             |        5 |         8 |               57 |
| Netgear GS308EP       | Managed switch                |             |        7 |        10 |               61 |
| Zyxel NWA50AX         | Access Point                  | openWRT     |        6 |        12 |               79 |
| ESP8266               | Sensor Node                   | 5x          |  0.2 (1) | 0.5 (2.5) |           3 (15) |
| **Total (estimated)** | —                             | —           |        — |         — | **942 kWh/Year** |

### Additional

| Device                            | Role            | Notes | Idle (W) | Peak (W) | kWh/Year(≈Avg) |
| --------------------------------- | --------------- | ----- | -------: | -------: | -------------: |
| Mac Mini M4                       | LLM Server      |       |       10 |       50 |            263 |
| Raspberry Pi B+                   | Hello App       |       |      1.5 |        3 |             20 |
| Raspberry Pi 3B                   | Dev             |       |      2.5 |        5 |             33 |
| Raspberry Pi 5B (8 GB)            | Dev             |       |        5 |       12 |             74 |
| Orange Pi Zero 3 (4 GB)           | Dev             |       |        2 |        4 |             26 |
| Orange Pi Zero 3 (1 GB)           | Dev             |       |      1.5 |        3 |             20 |
| TP-Link TL-SG105 Unmanaged Switch | Network Testing |       |        3 |        5 |             35 |

---

## 📡 Network overview

- **Router**: opnSense DIY-Router
- **Switches**:
  - Netgear GS108E (8-Port, managed)
  - Netgear GS308EP (8-Port, managed, PoE)
- **Cable management**: 0.5U Patch panel

---

## 🗄️ Rack layout (9U, 10")

| U   | Gerät                     |
| --- | ------------------------- |
| 09  | opnSense Router           |
| 08  | R-Pi Panel                |
| 07  | Netgear 8-Port Switch     |
| 06  | proxmox Server            |
| 05  | 12-Port Patch panel       |
| 04  | Netgear 8-Port PoE Switch |
| 03  | K3s Shelf                 |
| 02  | K3s Shelf                 |
| 01  | K3s Shelf                 |

---

## 🧩 Future & Extension

- NAS-Extension
- Proxmox Server with Ryzen 9
- Optional: more Units in server rack for additional devices and patch panels

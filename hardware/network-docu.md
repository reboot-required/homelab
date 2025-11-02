# Homelab Devices

//TODO: Add drawio diagram\
//TODO: IP Address Overview\
//TODO: Add VLAN documentation

## Homelab Network

```text
├── WAN / Internet
│ └── Fiber optic modem
│
├── Router / Firewall
│ └── opnSense Mini-PC
│
├── Switches
│ ├── Netgear GS108E
│ │ ├── Port 1: opnSense (LAN)
│ │ ├── Port 2: RPi 5B
│ │ ├── Port 3: Proxmox Server
│ │ ├── Port 4: K3s_Master01
│ │ ├── Port 5: K3s_Worker01
│ │ ├── Port 6: K3s_Worker01
│ │ ├── Port 7: Netgear GS108E
│ │ └── Port 8: RPi 3B
│ │
│ └── Netgear GS308EP
│   ├── Port 1: Mac Mini M4
│   ├── Port 2: -/-
│   ├── Port 3: -/-
│   ├── Port 4: -/-
│   ├── Port 5: -/-
│   ├── Port 6: -/-
│   ├── Port 7: Zyxel AP (PoE)
│   └── Port 8: Netgear GS108E
|
└── WLAN (via Zyxel Access Point)
  ├── SSID: Home-Net (5GHz)
  └── SSID: IoT-WiFi (2.4GHz)
```

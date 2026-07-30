---
type: note
tags:
  - networking
  - topology
---

# Network Topology

The lab sits on the **10.136.0.0/16** supernet. Every segment is a subnet of it,
routed and firewalled by [[the.shire]].

## Physical topology

```mermaid
flowchart TD
    INET(["Internet"])
    MODEM["Fiber modem<br>ISP"]

    subgraph RTR["the.shire — OPNsense · N150, 4× NIC"]
        direction LR
        P10["port 10<br>WAN"]
        P20["port 20 · HOMELAB<br>10.136.20.1<br>trunk: native 20, tagged 30 + 100"]
        P30["port 30 · WORKSTATION<br>10.136.50.1"]
        P40["port 40 · DEBUG<br>unconnected"]
    end

    HOB["hobbiton.shire<br>Netgear GS108E · 10.136.20.2"]
    GRW["greenway.shire<br>Netgear GS308EP PoE · 10.136.20.3"]
    BRE["bree.shire<br>Zyxel NWA50AX · 10.136.20.151"]

    BTP["bill-the-pony.shire<br>Proxmox VE · .100"]
    ISG["isengard.shire<br>K3s master · .11"]
    ROH["rohan.shire<br>K3s worker · .12"]
    GON["gondor.shire<br>K3s worker · .13"]
    TUC["tuckborough.shire<br>RPi 5B · .21"]
    OVH["overhill.shire<br>RPi B+ · .22"]
    VAL["valinor.shire<br>Mac Mini M4 · .20"]
    IRN["iron-hills.shire<br>Workstation · 10.136.50.10"]

    subgraph WIFI["Virtual APs on bree.shire"]
        direction LR
        SSID20["bag-end.shire<br>5 GHz · VLAN 20"]
        SSID30["green-dragon-inn.shire<br>2.4 GHz · VLAN 30"]
        SSID100["prancing-pony.shire<br>2.4 GHz · VLAN 100"]
    end

    IOT["IoT devices · VLAN 30<br>proudfoot-00…04 · took-00…01<br>10.136.30.10–.21"]
    GUEST["Guest clients<br>10.136.100.100–.199"]

    INET --- MODEM --- P10
    P20 -->|trunk| HOB
    P30 -->|"direct cable"| IRN

    HOB -->|P2| TUC
    HOB -->|"P3 · trunk +30"| BTP
    HOB -->|P4| ISG
    HOB -->|P5| ROH
    HOB -->|P6| GON
    HOB -->|"P7 · trunk"| GRW
    HOB -->|P8| OVH

    GRW -->|P1| VAL
    GRW -->|"P7 · trunk, PoE"| BRE

    BRE --- SSID20
    BRE --- SSID30
    BRE --- SSID100
    SSID30 --- IOT
    SSID100 --- GUEST

    classDef rtr fill:#8b3a2f,stroke:#5f251d,color:#fff
    classDef sw fill:#1f6f8b,stroke:#134b5f,color:#fff
    classDef ap fill:#6b4a8b,stroke:#46305c,color:#fff
    classDef host fill:#3d6b35,stroke:#294a24,color:#fff
    classDef iot fill:#8b7a2f,stroke:#5f531d,color:#fff

    class HOB,GRW sw
    class BRE ap
    class BTP,ISG,ROH,GON,TUC,OVH,VAL,IRN host
    class IOT,GUEST,SSID30,SSID100 iot
```

Not shown: [[gondolin.shire]] has no recorded switch port. See its note.

## Proxmox guests

Everything below hangs off one host and never touches a physical cable.

```mermaid
flowchart LR
    BTP["bill-the-pony.shire<br>Proxmox VE · 10.136.20.100"]

    RAD["radagast.shire · .101<br>n8n"]
    ERE["erebor.shire · .102<br>GitLab CE"]
    RIV["rivendell.shire · .103<br>TrueNAS Scale"]
    THA["thal.shire · .104<br>Heimdall"]
    PAL["palantir.shire · .105<br>Prometheus + Grafana"]
    KHA["khazad-dum.shire · .106<br>Kernel development"]
    WEA["weathertop.shire · .107<br>Home Assistant OS"]
    WEA30["IoT NIC<br>10.136.30.5 · VLAN 30"]

    BTP --> RAD
    BTP --> ERE
    BTP --> RIV
    BTP --> THA
    BTP --> PAL
    BTP --> KHA
    BTP --> WEA
    WEA -.->|"second NIC"| WEA30

    classDef host fill:#3d6b35,stroke:#294a24,color:#fff
    classDef vm fill:#2f6b6b,stroke:#1d4747,color:#fff
    classDef iot fill:#8b7a2f,stroke:#5f531d,color:#fff
    class BTP host
    class RAD,ERE,RIV,THA,PAL,KHA,WEA vm
    class WEA30 iot
```

## Layers

| Layer | Node | Hardware |
|---|---|---|
| WAN | — | Fiber modem, ISP-supplied |
| Router / firewall | [[the.shire]] | OPNsense on N150 Mini-PC |
| Core switch | [[hobbiton.shire]] | Netgear GS108E |
| PoE switch | [[greenway.shire]] | Netgear GS308EP |
| Access point | [[bree.shire]] | Zyxel NWA50AX, OpenWRT |
| Hypervisor | [[bill-the-pony.shire]] | Proxmox VE |
| Kubernetes | [[isengard.shire]], [[rohan.shire]], [[gondor.shire]] | K3s |

## Related

- [[VLANs]] — segmentation
- [[IP Plan]] — address assignments
- [[Switch Ports]] — port-by-port
- [[Firewall Rules]] — what may talk to what
- [[Wireless]]

<div align="center">

<br/>

```
███████╗████████╗      ██████╗ ████████╗██╗    ██╗██╗███╗   ██╗
╚══███╔╝╚══██╔══╝     ██╔══██╗╚══██╔══╝██║    ██║██║████╗  ██║
  ███╔╝    ██║        ██║  ██║   ██║   ██║ █╗ ██║██║██╔██╗ ██║
 ███╔╝     ██║        ██║  ██║   ██║   ██║███╗██║██║██║╚██╗██║
███████╗   ██║        ╚██████╔╝   ██║   ╚███╔███╔╝██║██║ ╚████║
╚══════╝   ╚═╝         ╚═════╝    ╚═╝    ╚══╝╚══╝ ╚═╝╚═╝  ╚═══╝
```

### 🛡️ Network Digital Twin with Adaptive Zero-Trust Defense
#### *Live Attack Simulation · TCP Congestion Benchmarking · Anomaly Detection*

<br/>

[![Course](https://img.shields.io/badge/CE313-Computer_Networks-1a1a2e?style=for-the-badge&logo=cisco&logoColor=00d4ff)](.)
[![Institute](https://img.shields.io/badge/GIK_Institute-Spring_2026-0f3460?style=for-the-badge)](.)
[![ZTA](https://img.shields.io/badge/NIST_SP_800--207-Zero--Trust-e94560?style=for-the-badge)](.)
[![Simulator](https://img.shields.io/badge/Cisco_Packet_Tracer-8.x-049fd4?style=for-the-badge&logo=cisco&logoColor=white)](.)
[![Status](https://img.shields.io/badge/Status-In_Progress-f5a623?style=for-the-badge)](.)
[![License](https://img.shields.io/badge/License-Academic-16213e?style=for-the-badge)](.)

<br/>

> **"The only CE313 project that measures TCP performance degradation under live attack traffic  
> AND demonstrates real-time Zero-Trust mitigation with quantitative KPIs."**

<br/>

[📋 Proposal PDF](./docs/ZT-DTwin_Proposal.pdf) · [🗺️ Topology](#-network-topology) · [🔴 Attacks](#-live-attack-simulation) · [📊 Benchmarks](#-tcp-congestion-benchmarking) · [🚀 Getting Started](#-getting-started)

</div>

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Network Topology](#-network-topology)
- [IP Addressing Scheme](#-ip-addressing-scheme)
- [Five-Layer Coverage](#-five-layer-coverage)
- [Zero-Trust Architecture](#-zero-trust-architecture)
- [Live Attack Simulation](#-live-attack-simulation)
- [TCP Congestion Benchmarking](#-tcp-congestion-benchmarking)
- [SIEM-Style Observability](#-siem-style-observability)
- [Tools & Technologies](#-tools--technologies)
- [Project Milestones](#-project-milestones)
- [CLO & Grading Alignment](#-clo--grading-alignment)
- [Bonus Opportunities](#-bonus-opportunities)
- [Repository Structure](#-repository-structure)
- [Getting Started](#-getting-started)
- [Team](#-team)

---

## 🔭 Overview

**ZT-DTwin** is a high-fidelity **Network Digital Twin (NDT)** — a complete simulated replica of a real enterprise campus network. It safely hosts live cyberattack scenarios, measures their quantitative impact on TCP/UDP performance, and demonstrates how a **Zero-Trust Architecture (ZTA)** policy layer mitigates each attack in real time.

This is not just a connectivity lab. It is a research-grade simulation platform that mirrors workflows used by:

| Domain | Real-World Mirror |
|--------|------------------|
| 🏢 Enterprise Security | SOC analysts defending against SYN floods and ARP poisoning |
| ☁️ Cloud Networking | Hyperscalers (Google, Meta, Cisco) using NDTs for pre-deployment testing |
| 🔒 Zero-Trust | NIST SP 800-207 & U.S. Executive Order 14028 mandated architecture |
| 📡 TCP Research | BBR vs. Reno comparison mirrors active IETF work (RFC 9002, BBRv2 Draft) |

**Full title:** *"ZT-DTwin: A Cyber-Resilient Network Digital Twin with Real-Time Threat Response and Performance Analytics"*

---

## 🚨 Problem Statement

Modern enterprise networks face three simultaneous challenges this project solves:

```
┌─────────────────────────────────────────────────────────────────┐
│  CHALLENGE 1 │ Security teams cannot test live attack           │
│              │ responses on production networks without         │
│              │ risking outages → Need a safe Digital Twin       │
├─────────────────────────────────────────────────────────────────┤
│  CHALLENGE 2 │ Engineers cannot benchmark congestion algorithms │
│              │ (BBR vs. Reno) under active attack traffic —     │
│              │ data critical for SLA design                     │
├─────────────────────────────────────────────────────────────────┤
│  CHALLENGE 3 │ ZTA is NIST-mandated & EO 14028 required, yet   │
│              │ most graduates have never designed or            │
│              │ validated one end-to-end                         │
└─────────────────────────────────────────────────────────────────┘
```

ZT-DTwin addresses **all three** in a single, portfolio-worthy simulation.

---

## 🗺️ Network Topology

The network implements a **multi-zone enterprise architecture** with Edge, Core, Distribution, Access, DMZ, OT/IIoT, and Management planes — as shown in the topology diagram below.

<div align="center">

![ZT-DTwin Network Topology](./docs/topology.png)

*Full enterprise topology: Edge firewalls (HA), Core L3 switching (MLAG), wired/wireless user LANs,  
server farm, DMZ zone, Industrial/OT network, and a dedicated management & services plane.*

</div>

### Zone Summary

| Zone | VLAN | Subnet | Key Devices |
|------|------|--------|-------------|
| 🔵 Management | VLAN 10 | `10.10.10.0/24` | NMS, Syslog, AAA/RADIUS, vCenter, SIEM, ZT-Twin Server |
| 🟢 User LAN (Wired) | VLAN 20 | `10.10.20.0/24` | Access-SW-1…m → Dist-SW-1, User PCs |
| 🩵 User LAN (Wireless) | VLAN 30 | `10.10.30.0/24` | WLC, Access Points, Laptops |
| 🟣 Server Farm / DC | VLAN 40 | `10.10.40.0/24` | AD/DNS, File, App, DB, Web servers |
| 🔴 DMZ Zone | VLAN 50 | `10.10.50.0/24` | Web/Portal Server, Proxy/Reverse Proxy |
| 🟠 Industrial / OT (IIoT) | VLAN 60 | `10.10.60.0/24` | PLCs, HMIs, SCADA Nodes, Sensors, Historian |

### Physical Layer Design

```
                        ☁️  INTERNET
                             │
                        [ISP Router]
                             │
              ┌──────────────┴──────────────┐
         [Firewall-1]═══════HA ════════[Firewall-2]
           (Active)                    (Standby)
              └──────────────┬──────────────┘
                             │
              ┌──────────────┴──────────────┐
          [Core-SW1]══════MLAG/Stack══════[Core-SW2]
              (L3)                          (L3)
              └──────────────┬──────────────┘
                             │ OSPF / Dynamic Routing
        ┌────────────────────┴─────────────────────┐
   [Dist-SW-1 L3]                            [Dist-SW-2 L3]
        │                                          │
   ┌────┤                                     ┌────┤
Access-SW-1..m                         [WLC]──Access Points
(USER VLAN 20)                         (WLAN VLAN 30)
        │
   [Server-Farm-SW]──[DMZ-SW]──[IIoT-Agg-SW]──[Mgmt-SW]
     VLAN 40          VLAN 50    VLAN 60        VLAN 10
```

---

## 📡 IP Addressing Scheme

### Management & Server Subnets

| Segment | Network | Notable Hosts |
|---------|---------|--------------|
| Management (VLAN 10) | `10.10.10.0/24` | NMS `.10`, Syslog `.20`, AAA `.30`, Backup `.40`, vCenter `.50` |
| User LAN Wired (VLAN 20) | `10.10.20.0/24` | DHCP pool for User PCs |
| User LAN Wireless (VLAN 30) | `10.10.30.0/24` | DHCP pool for Laptops |
| Server Farm (VLAN 40) | `10.10.40.0/24` | AD/DNS `.10`, File `.20`, App `.30`, DB `.40`, Web `.50` |
| DMZ (VLAN 50) | `10.10.50.0/24` | Web/Portal `.10`, Proxy `.20` |
| IIoT (VLAN 60) | `10.10.60.0/24` | Historian `.10`, Asset/Inv `.20` |

---

## 🧱 Five-Layer Coverage

Every TCP/IP layer is explicitly implemented and mapped to CE313 weekly topics:

| Layer | Weeks | Features Implemented |
|-------|-------|---------------------|
| **Physical** | 2 | Star + Spine-Leaf hybrid; copper/fiber/wireless; TIA/EIA-568 cabling; transmission impairment modeling |
| **Data Link** | 3–4 | VLANs, 802.1Q trunking, MAC learning, CRC detection, CSMA/CD vs CSMA/CA, STP loop prevention, DAI, port security |
| **Network** | 5, 11–13 | IPv4/IPv6 dual-stack, VLSM subnetting, NAT/PAT, OSPF + RIP comparison, BGP stub AS, MPLS basics, ICMP |
| **Transport** | 8–10 | TCP Tahoe/Reno/Cubic/BBR vs UDP; iPerf3 benchmarks; RTT, jitter, loss measurement under attack traffic |
| **Application** | 6–7 | HTTP/1.1 vs HTTP/2 vs HTTP/3 latency, DNS anycast, REST API simulation, optional BitTorrent P2P |

---

## 🔒 Zero-Trust Architecture

Full ZTA policy stack per **NIST SP 800-207** and **U.S. Executive Order 14028**:

```
┌─────────────────────────────────────────────────────────┐
│              ZERO-TRUST POLICY ENGINE                   │
│                                                         │
│  ┌─────────────┐    ┌──────────────┐   ┌─────────────┐ │
│  │  Identity   │    │    Policy    │   │  Continuous │ │
│  │   Source    │───▶│   Decision   │──▶│ Verification│ │
│  │(802.1X/WPA3)│    │  Point (PDP) │   │  per flow   │ │
│  └─────────────┘    └──────────────┘   └─────────────┘ │
│          │                │                   │         │
│  ┌───────▼────────────────▼───────────────────▼──────┐ │
│  │         MICRO-SEGMENTATION ENFORCEMENT            │ │
│  │  VLAN10  VLAN20  VLAN30  VLAN40  VLAN50  VLAN60   │ │
│  │  Mgmt    Users   WiFi    Servers  DMZ     OT/IIoT  │ │
│  │  [ACL]   [ACL]   [ACL]   [ACL]   [ACL]   [ACL]    │ │
│  └───────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────┘
```

| ZTA Pillar | Implementation |
|------------|---------------|
| **Identity-Based Micro-Segmentation** | Every VLAN = one trust zone; cross-zone traffic requires explicit ACL permit — no implicit trust |
| **Continuous Verification** | 802.1X port auth for wired endpoints; WPA3 for wireless segments |
| **Least-Privilege Access** | Separate VLANs for IT staff, end users, IoT, and management plane; per-group ACLs |
| **Encrypted East-West Traffic** | IPsec tunnels between DC VLANs; WireGuard-style VPN for remote access |
| **Policy Decision Point** | Central firewall/router as PDP — every new flow evaluated against ZT policy table before forwarding |

---

## 🔴 Live Attack Simulation

> This module is what separates ZT-DTwin from every other CE313 submission.

Four attack scenarios scripted and executed inside the simulation environment:

| Attack | Layer | Tool / Method | ZT Mitigation | Metric |
|--------|-------|---------------|---------------|--------|
| **SYN Flood (DoS)** | Transport (TCP) | Scapy script | ACL rate-limiting + SYN cookies | Throughput drop %, recovery time |
| **DNS Cache Poisoning** | Application (DNS) | Manual DNS injection | DNSSEC + DNS filtering ACL | Resolution failure rate |
| **ARP Spoofing / MITM** | Data Link (ARP) | Dynamic ARP spoofing | DAI + Static ARP entries | Intercepted packets count |
| **Rogue AP / Lateral Movement** | Physical / Network | Unauthorized host injection | 802.1X + NAC policy | Blocked flows / auth failures |

**For every attack, three phases are captured:**

```
BEFORE ATTACK          DURING ATTACK          AFTER ZT MITIGATION
─────────────          ─────────────          ───────────────────
Baseline Wireshark  →  Attack Wireshark    →  Mitigation Wireshark
iPerf3 normal bw    →  iPerf3 degraded    →  iPerf3 recovered
RTT: baseline       →  RTT: elevated      →  RTT: near-baseline
```

---

## 📊 TCP Congestion Benchmarking

Research-grade comparison of **four TCP congestion-control algorithms** under three network conditions — directly targeting CLO_3:

| Condition | TCP Tahoe | TCP Reno | TCP Cubic | TCP BBR |
|-----------|-----------|----------|-----------|---------|
| Normal (0% loss) | Baseline | Baseline | Baseline | Baseline |
| Congested (5% loss) | Measured | Measured | Measured | Measured |
| Under SYN Flood | Measured | Measured | Measured | Measured |

**Metrics per scenario:**

```
📈  Throughput (Mbps)     — time-series graph
📉  RTT (ms)              — before/during/after
📶  Jitter (ms)           — UDP stream variance
❌  Packet Loss (%)        — per algorithm comparison
🔁  Retransmission Rate    — congestion response speed
```

This mirrors active IETF research on **BBRv2** (RFC 9002, BBRv2 Internet Draft).

---

## 📡 SIEM-Style Observability

```
Network Events ──▶ Syslog Server ──▶ Correlation Engine ──▶ Dashboard
                                            │
                              ┌─────────────▼──────────────┐
                              │     Event Timeline          │
                              │  T+00s  ARP flood detected  │
                              │  T+03s  DAI blocks attacker │
                              │  T+05s  Throughput recovers │
                              │  T+12s  ACL log entry fired │
                              └────────────────────────────┘
```

| Observability Feature | Tool | Output |
|-----------------------|------|--------|
| SNMP v2c/v3 polling | Network devices | Interface stats, error counters |
| Packet telemetry | Wireshark PCAP | Anomaly signatures, flood patterns |
| Syslog correlation | Syslog Server | Timestamped attack ↔ performance events |
| NETCONF documentation | Conceptual (Week 14) | YANG model reference |

---

## 🛠️ Tools & Technologies

| Category | Tool | Purpose |
|----------|------|---------|
| **Simulation** | Cisco Packet Tracer 8.x | Primary — all layers, VLANs, routing, ACLs, servers |
| **Advanced Sim** | GNS3 + real IOS *(bonus)* | BGP, advanced routing, real IOS behavior |
| **Protocol Analysis** | Wireshark | Packet capture, attack forensics, telemetry |
| **Performance Testing** | iPerf3 | TCP/UDP throughput, RTT, jitter benchmarking |
| **Attack Scripting** | Python + Scapy *(bonus)* | SYN flood generation, DNS injection scripts |
| **Diagramming** | Draw.io / Lucidchart | IEEE/TIA-compliant topology diagrams |
| **Graphing** | Python (matplotlib) / Excel | Performance comparison charts |
| **SDN** | Mininet + OpenFlow *(bonus)* | Dynamic flow-rule policy enforcement |
| **Observability** | Prometheus + Grafana *(bonus)* | Live performance dashboard |

---

## 🗓️ Project Milestones

```
WEEK 2–3        WEEK 7–8              WEEK 15
   │               │                     │
   ▼               ▼                     ▼
[M1: Proposal] [M2: Mid-Progress]  [M3: Final Submission]
  ✅ Complete    🔄 In Progress       ⏳ Upcoming
  
  • Title         • Working VLANs      • Full IEEE report (15–20 pp)
  • Group info    • OSPF routing       • Live demo
  • Topology      • Wireshark caps     • Slides (12 slides)
  • Tools list    • 5-min demo         • PCAP files
  • CLO mapping                        • Scapy scripts
```

---

## 📐 CLO & Grading Alignment

### Course Learning Outcomes

| CLO | Project Weight | Grade % | How This Project Addresses It |
|-----|---------------|---------|-------------------------------|
| **CLO_1** Hardware & Software Understanding | 30% of project | 3% of total | Full 5-layer documentation, physical topology with media types, protocol stack diagrams across all layers |
| **CLO_2** Configuration & Optimization | 30% of project | 3% of total | VLAN config, OSPF/RIP routing, ACL/firewall rules, VPN tunnels, SSL/TLS — all configured, tested, and optimized |
| **CLO_3** Analysis & Diagnosis | 40% of project | 4% of total | Attack simulation with quantitative KPIs, TCP 4-algorithm benchmark, ZT mitigation effectiveness, root-cause troubleshooting |

### Rubric Alignment

| Criterion | Weight | How Addressed |
|-----------|--------|--------------|
| Technical Implementation & Correctness | 35% | Full 5-layer simulation with all mandatory technologies across 6 network zones |
| Analysis & Optimization | 30% | TCP benchmark graphs, attack impact data, OSPF vs RIP convergence timing |
| Security & Industry Best Practices | 15% | NIST ZTA, NIST SP 800-207, IPsec VPN, ACLs, 802.1X, cryptographic primitives |
| Documentation Quality | 10% | IEEE-format report, Draw.io diagrams, this README, structured appendices |
| Presentation & Demo Quality | 10% | Live troubleshooting demo + attack scenario walkthrough |

### ZT-DTwin vs. Typical CE313 Project

| Typical CE313 Project | ✅ ZT-DTwin |
|-----------------------|------------|
| Static topology, no threats modeled | Live attack simulation with quantitative impact measurement |
| Security as an afterthought (one firewall rule) | Full Zero-Trust policy stack across all VLANs and layers |
| Single TCP variant, no comparison | 4-algorithm TCP benchmarking under 3 distinct conditions |
| No observability or logging | SIEM-style event correlation with Wireshark telemetry |
| Pass/fail connectivity testing only | Quantitative KPIs: throughput, RTT, jitter, packet loss graphs |
| One routing protocol, no comparison | OSPF vs. RIP performance comparison with convergence timing |

---

## 🌟 Bonus Opportunities (+5%)

| Bonus Feature | Alignment | Status |
|---------------|-----------|--------|
| HTTP/3 QUIC latency vs HTTP/1.1 under packet loss | Week 6 + IETF research | ⏳ Planned |
| Mininet + OpenFlow SDN with dynamic attack-response flow rules | Week 13 (SDN/OpenFlow) | ⏳ Planned |
| Prometheus + Grafana observability dashboard | Network Management | ⏳ Planned |
| BBRv2 analysis referencing IETF Internet Draft | TCP Research | ⏳ Planned |
| BitTorrent-style P2P DHT simulation | Week 7 | ⏳ Planned |

---

## 📁 Repository Structure

```
ZT-DTwin/
│
├── 📄 README.md                        ← You are here
│
├── 📂 docs/
│   ├── ZT-DTwin_Proposal.pdf           ← Full project proposal (PDF)
│   └── topology.png                    ← Network topology diagram
│
├── 📂 simulation/
│   ├── ZT_DTwin_Enterprise.pkt         ← Cisco Packet Tracer file
│   └── configs/                        ← Per-device CLI configurations
│       ├── CORE-R1.txt
│       ├── CORE-R2.txt
│       ├── DIST-SW1.txt
│       ├── DIST-SW2.txt
│       ├── ACC-SW-IT.txt
│       ├── ACC-SW-HR.txt
│       ├── ACC-SW-FIN.txt
│       ├── ACC-SW-SALES.txt
│       └── ACC-SW-SRV.txt
│
├── 📂 attacks/
│   ├── syn_flood.py                    ← Scapy SYN flood script
│   ├── dns_poison.py                   ← DNS cache poisoning script
│   └── arp_spoof.py                    ← ARP spoofing script
│
├── 📂 pcaps/
│   ├── baseline_traffic.pcap           ← Normal traffic capture
│   ├── syn_flood_attack.pcap           ← SYN flood capture
│   ├── syn_flood_mitigated.pcap        ← Post-mitigation capture
│   └── arp_spoof_dai_blocked.pcap      ← DAI block evidence
│
├── 📂 benchmarks/
│   ├── tcp_comparison_results.xlsx     ← iPerf3 data (all algorithms)
│   └── plot_results.py                 ← matplotlib graph generator
│
└── 📂 report/
    └── ZT-DTwin_Final_Report.pdf       ← IEEE-format final report
```

---

## 🚀 Getting Started

### Prerequisites

- [Cisco Packet Tracer 8.x](https://www.netacad.com/courses/packet-tracer) (free with NetAcad account)
- Python 3.8+ (for attack scripts and graphing)
- Wireshark (for PCAP analysis)

### Open the Simulation

```bash
# Clone the repository
git clone https://github.com/shehroz/ZT-DTwin.git
cd ZT-DTwin

# Open the Packet Tracer file
# Double-click simulation/ZT_DTwin_Enterprise.pkt
# OR
open simulation/ZT_DTwin_Enterprise.pkt
```

### Manual Build (if PKT version mismatch)

```bash
# All device configurations are in simulation/configs/
# Open Packet Tracer → build topology → paste each config into device CLI

# Order of configuration:
# 1. CORE-R1, CORE-R2  (routers first)
# 2. DIST-SW1, DIST-SW2  (L3 switches)
# 3. ACC-SW-* (access switches)
# 4. Configure servers via GUI (see simulation/configs/SERVER_SETUP.txt)
# 5. Set PCs to DHCP
```

### Run Attack Scripts *(GNS3 / real environment only)*

```bash
pip install scapy
python attacks/syn_flood.py --target 10.10.40.50 --rate 1000
python attacks/arp_spoof.py --gateway 10.10.20.1 --target 10.10.20.50
```

### Generate Performance Graphs

```bash
pip install matplotlib pandas openpyxl
python benchmarks/plot_results.py
```

### Verify Connectivity (inside Packet Tracer CLI)

```
# On CORE-R1:
show ip ospf neighbor
show ip route
show ip nat translations

# On DIST-SW1:
show vlan brief
show interfaces trunk
show standby brief

# Test from IT-PC1:
ping 8.8.8.8          (Internet via NAT)
ping 10.10.40.50      (Web server)
ping 10.10.20.50      (Cross-VLAN)
traceroute 10.10.40.30
```

---

## 👤 Team

<div align="center">

| | Details |
|---|---|
| **Name** | Shehroz |
| **Course** | CE313 — Computer Communications & Networks |
| **Institution** | GIK Institute of Engineering Sciences & Technology |
| **Instructor** | Engr. Muhammad Ahmad Nawaz |
| **Semester** | Spring 2026 |
| **Project Theme** | Hybrid: Zero-Trust + SDN + Attack Simulation |

</div>

---

<div align="center">

### 📄 Full Proposal

The complete project proposal is available as a PDF:

**[📥 Download ZT-DTwin_Proposal.pdf](./docs/ZT-DTwin_Proposal.pdf)**

---

*CE313 — GIK Institute · Spring 2026 · Instructor: Engr. Muhammad Ahmad Nawaz*

*Built with 🛡️ by Shehroz*

</div>

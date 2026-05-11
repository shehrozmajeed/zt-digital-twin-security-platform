<div align="center">

<br/>

```
███████╗████████╗      ██████╗ ████████╗██╗    ██╗██╗███╗   ██╗
╚══███╔╝╚══██╔══╝     ██╔══██╗╚══██╔══╝██║    ██║██║████╗  ██║
  ███╔╝    ██║        ██║  ██║   ██║   ██║ █╗ ██║██║██╔██╗ ██║
 ███╔╝     ██║        ██║  ██║   ██║   ██║███╗██║██║██║╚██╗██║
███████╗   ██║        ╚██████╔╝  ██║   ╚███╔███╔╝██║██║ ╚████║
╚══════╝   ╚═╝         ╚═════╝   ╚═╝    ╚══╝╚══╝ ╚═╝╚═╝  ╚═══╝
```

<h3>🛡️ Network Digital Twin with Adaptive Zero-Trust Defense</h3>
<p><em>Live Attack Simulation · TCP Congestion Benchmarking · Anomaly Detection · SIEM Observability</em></p>

<br/>

[![Course](https://img.shields.io/badge/CE313-Computer_Networks-1a1a2e?style=for-the-badge&logo=cisco&logoColor=00d4ff)](.)
[![Institute](https://img.shields.io/badge/GIK_Institute-Spring_2026-0f3460?style=for-the-badge)](.)
[![ZTA](https://img.shields.io/badge/NIST_SP_800--207-Zero--Trust-e94560?style=for-the-badge)](.)
[![Simulator](https://img.shields.io/badge/Cisco_Packet_Tracer-8.x-049fd4?style=for-the-badge&logo=cisco&logoColor=white)](.)
[![Status](https://img.shields.io/badge/Status-In_Progress-f5a623?style=for-the-badge)](.)
[![License](https://img.shields.io/badge/License-Academic-16213e?style=for-the-badge)](.)

<br/>

> **"The only CE313 project that measures TCP performance degradation under live attack traffic**  
> **and demonstrates real-time Zero-Trust mitigation with quantitative KPIs."**

<br/>

[📋 Proposal PDF](./docs/ZT-DTwin_Proposal.pdf) · [🗺️ Topology](#-network-topology) · [🔴 Attacks](#-live-attack-simulation) · [📊 Benchmarks](#-tcp-congestion-benchmarking) · [🚀 Getting Started](#-getting-started) · [👤 Team](#-team)

</div>

---

## 📖 Table of Contents

1. [Project Overview](#-project-overview)
2. [Problem Statement](#-problem-statement)
3. [Network Topology](#-network-topology)
4. [IP Addressing Scheme](#-ip-addressing-scheme)
5. [Five-Layer Coverage](#-five-layer-coverage)
6. [Zero-Trust Architecture](#-zero-trust-architecture)
7. [Live Attack Simulation](#-live-attack-simulation)
8. [TCP Congestion Benchmarking](#-tcp-congestion-benchmarking)
9. [SIEM-Style Observability](#-siem-style-observability)
10. [Tools & Technologies](#-tools--technologies)
11. [Project Milestones](#-project-milestones)
12. [CLO & Grading Alignment](#-clo--grading-alignment)
13. [Bonus Opportunities](#-bonus-opportunities)
14. [Repository Structure](#-repository-structure)
15. [Getting Started](#-getting-started)
16. [Team](#-team)

---

## 🔭 Project Overview

**ZT-DTwin** is a high-fidelity **Network Digital Twin (NDT)** — a complete, simulated replica of a real enterprise campus network — designed to safely host live cyberattack scenarios, quantitatively measure their impact on TCP/UDP performance, and demonstrate how a **Zero-Trust Architecture (ZTA)** policy layer mitigates each threat in real time.

This is not a connectivity lab. It is a **research-grade simulation platform** that mirrors workflows used by security operations centers, cloud networking teams, and protocol researchers worldwide.

<br/>

<div align="center">

| Domain | Real-World Parallel |
|:------:|:-------------------:|
| 🏢 **Enterprise Security** | SOC analysts defending against SYN floods and ARP poisoning at scale |
| ☁️ **Cloud Networking** | Hyperscalers (Google, Meta, Cisco) using NDTs for pre-deployment validation |
| 🔒 **Zero-Trust** | NIST SP 800-207 & U.S. Executive Order 14028 mandated architecture |
| 📡 **TCP Research** | BBR vs. Reno benchmarking mirrors active IETF work (RFC 9002, BBRv2 Draft) |

</div>

<br/>

**Full Title:** *"ZT-DTwin: A Cyber-Resilient Network Digital Twin with Real-Time Threat Response and Performance Analytics"*

---

## 🚨 Problem Statement

Modern enterprise networks face three simultaneous, compounding challenges. ZT-DTwin is engineered to address all three within a single, portfolio-grade simulation.

```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                     │
│  CHALLENGE 1 ─ SAFE ATTACK TESTING                                  │
│  Security teams cannot run live attack response exercises on        │
│  production networks without risking service outages. A Digital     │
│  Twin provides a faithful, isolated replica for safe experimentation │
│                                                                     │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  CHALLENGE 2 ─ CONGESTION ALGORITHM BENCHMARKING                    │
│  Engineers lack empirical data on how BBR, Cubic, Reno, and Tahoe  │
│  behave under active attack traffic — data that is critical for     │
│  SLA design and capacity planning in adversarial environments       │
│                                                                     │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  CHALLENGE 3 ─ ZERO-TRUST SKILLS GAP                                │
│  ZTA is federally mandated (NIST SP 800-207 / EO 14028), yet most   │
│  graduates have never designed, configured, or validated a          │
│  Zero-Trust policy stack end-to-end in a multi-zone environment     │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 🗺️ Network Topology

The network implements a **multi-zone enterprise architecture** spanning Edge, Core, Distribution, Access, DMZ, OT/IIoT, and Management planes — all interconnected through a hardened policy enforcement layer.

<div align="center">

![ZT-DTwin Network Topology](./docs/topology.png)

*Full enterprise topology: HA edge firewalls, MLAG core switching, wired/wireless user LANs,  
server farm, DMZ zone, Industrial/OT network, and a dedicated management & services plane.*

</div>

<br/>

### Zone Summary

| Zone | VLAN | Subnet | Purpose & Key Devices |
|:----:|:----:|:------:|:----------------------|
| 🔵 **Management** | VLAN 10 | `10.10.10.0/24` | NMS, Syslog, AAA/RADIUS, vCenter, SIEM, ZT-Twin Server |
| 🟢 **User LAN (Wired)** | VLAN 20 | `10.10.20.0/24` | Access switches → Dist-SW-1; DHCP pool for User PCs |
| 🩵 **User LAN (Wireless)** | VLAN 30 | `10.10.30.0/24` | WLC, Access Points, Laptops; WPA3 enforcement |
| 🟣 **Server Farm / DC** | VLAN 40 | `10.10.40.0/24` | AD/DNS, File, Application, DB, Web servers |
| 🔴 **DMZ Zone** | VLAN 50 | `10.10.50.0/24` | Public-facing Web/Portal server, Reverse Proxy |
| 🟠 **Industrial / OT (IIoT)** | VLAN 60 | `10.10.60.0/24` | PLCs, HMIs, SCADA Nodes, Sensors, Historian |

<br/>

### Physical Layer Architecture

```
                              ☁️  INTERNET
                                   │
                             [ISP Router]
                                   │
                ┌──────────────────┴──────────────────┐
           [Firewall-1] ══════════HA══════════ [Firewall-2]
             (Active)           Failover          (Standby)
                └──────────────────┬──────────────────┘
                                   │
                ┌──────────────────┴──────────────────┐
            [Core-SW1] ════════MLAG/Stack════════ [Core-SW2]
              (L3 Switching)                   (L3 Switching)
                └──────────────────┬──────────────────┘
                                   │  OSPF / Dynamic Routing
          ┌────────────────────────┴──────────────────────────┐
     [Dist-SW-1 L3]                                    [Dist-SW-2 L3]
          │                                                    │
     ┌────┤                                               ┌────┤
Access-SW-1..m                                     [WLC] ──── Access Points
(USER VLAN 20)                                     (WLAN VLAN 30)
          │
   [Server-Farm-SW] ── [DMZ-SW] ── [IIoT-Agg-SW] ── [Mgmt-SW]
      VLAN 40            VLAN 50      VLAN 60           VLAN 10
```

---

## 📡 IP Addressing Scheme

### Subnet Allocation Table

| Segment | Network | Mask | Notable Static Hosts |
|:--------|:-------:|:----:|:---------------------|
| Management (VLAN 10) | `10.10.10.0` | `/24` | NMS `.10` · Syslog `.20` · AAA `.30` · Backup `.40` · vCenter `.50` |
| User LAN Wired (VLAN 20) | `10.10.20.0` | `/24` | DHCP pool — dynamic assignment for all User PCs |
| User LAN Wireless (VLAN 30) | `10.10.30.0` | `/24` | DHCP pool — dynamic assignment for Laptops |
| Server Farm (VLAN 40) | `10.10.40.0` | `/24` | AD/DNS `.10` · File `.20` · App `.30` · DB `.40` · Web `.50` |
| DMZ (VLAN 50) | `10.10.50.0` | `/24` | Web/Portal `.10` · Reverse Proxy `.20` |
| IIoT / OT (VLAN 60) | `10.10.60.0` | `/24` | Historian `.10` · Asset Inventory `.20` |

> All inter-VLAN routing enforced through the Core switches and firewall ACL policy — no implicit trust between segments.

---

## 🧱 Five-Layer Coverage

Every layer of the TCP/IP stack is explicitly implemented, tested, and mapped to CE313 weekly lecture topics.

| Layer | Weeks | Features Implemented |
|:-----:|:-----:|:---------------------|
| **Physical** | 2 | Star + Spine-Leaf hybrid topology; copper / fiber / wireless media; TIA/EIA-568 cabling standards; transmission impairment modeling |
| **Data Link** | 3–4 | VLANs, 802.1Q trunking, MAC learning & aging, CRC detection, CSMA/CD vs CSMA/CA, STP loop prevention, Dynamic ARP Inspection (DAI), port security |
| **Network** | 5, 11–13 | IPv4/IPv6 dual-stack, VLSM subnetting, NAT/PAT, OSPF + RIP comparison, BGP stub AS, MPLS basics, ICMP diagnostics |
| **Transport** | 8–10 | TCP Tahoe / Reno / Cubic / BBR vs. UDP; iPerf3 benchmarking; RTT, jitter, and loss measurement under attack and baseline conditions |
| **Application** | 6–7 | HTTP/1.1 vs HTTP/2 vs HTTP/3 latency testing; DNS anycast; REST API simulation; optional BitTorrent P2P DHT |

---

## 🔒 Zero-Trust Architecture

ZT-DTwin implements a full **Zero-Trust policy stack** per [NIST SP 800-207](https://csrc.nist.gov/publications/detail/sp/800-207/final) and [U.S. Executive Order 14028](https://www.whitehouse.gov/briefing-room/presidential-actions/2021/05/12/executive-order-on-improving-the-nations-cybersecurity/).

```
┌───────────────────────────────────────────────────────────────┐
│                   ZERO-TRUST POLICY ENGINE                    │
│                                                               │
│  ┌──────────────┐    ┌───────────────┐    ┌────────────────┐  │
│  │   Identity   │    │    Policy     │    │   Continuous   │  │
│  │    Source    │───▶│   Decision    │───▶│  Verification  │  │
│  │ (802.1X/WPA3)│    │  Point (PDP)  │    │   (per flow)   │  │
│  └──────────────┘    └───────────────┘    └────────────────┘  │
│          │                  │                     │            │
│  ┌───────▼──────────────────▼─────────────────────▼────────┐  │
│  │              MICRO-SEGMENTATION ENFORCEMENT             │  │
│  │                                                         │  │
│  │  VLAN10   VLAN20   VLAN30   VLAN40   VLAN50   VLAN60    │  │
│  │  Mgmt     Users    WiFi     Servers   DMZ      OT/IIoT  │  │
│  │  [ACL]    [ACL]    [ACL]    [ACL]    [ACL]     [ACL]    │  │
│  └─────────────────────────────────────────────────────────┘  │
└───────────────────────────────────────────────────────────────┘
```

<br/>

### ZTA Pillar Implementation

| ZTA Pillar | Implementation Detail |
|:-----------|:----------------------|
| **Identity-Based Micro-Segmentation** | Every VLAN constitutes an independent trust zone; cross-zone traffic requires an explicit ACL `permit` — zero implicit trust |
| **Continuous Verification** | 802.1X port authentication for all wired endpoints; WPA3-Enterprise for wireless segments |
| **Least-Privilege Access** | Separate VLANs for IT staff, end users, IoT devices, and the management plane — per-group ACLs enforced at every boundary |
| **Encrypted East-West Traffic** | IPsec tunnels between Data Center VLANs; WireGuard-style VPN for remote access paths |
| **Policy Decision Point (PDP)** | Central firewall/router acts as PDP — every new flow is evaluated against the ZT policy table before any forwarding decision |

---

## 🔴 Live Attack Simulation

> This module is the primary technical differentiator of ZT-DTwin from all other CE313 submissions.

Four complete attack scenarios are scripted, executed, and mitigated within the simulation environment, each producing quantitative before/during/after performance data.

<br/>

### Attack Scenarios

| # | Attack | OSI Layer | Tool / Method | ZT Mitigation | Primary Metric |
|:-:|:------:|:---------:|:-------------:|:-------------:|:--------------:|
| 1 | **SYN Flood (DoS)** | Transport (L4) | Scapy script | ACL rate-limiting + SYN cookies | Throughput drop % + recovery time |
| 2 | **DNS Cache Poisoning** | Application (L7) | Manual DNS injection | DNSSEC + DNS filtering ACL | Resolution failure rate |
| 3 | **ARP Spoofing / MITM** | Data Link (L2) | Dynamic ARP spoofing | DAI + static ARP binding | Intercepted packet count |
| 4 | **Rogue AP / Lateral Movement** | Physical / Network | Unauthorized host injection | 802.1X + NAC policy enforcement | Blocked flows + auth failure logs |

<br/>

### Three-Phase Measurement Protocol

For every attack scenario, three measurement phases are captured and compared:

```
  ╔══════════════════╗     ╔══════════════════╗     ╔══════════════════╗
  ║  PHASE 1         ║     ║  PHASE 2         ║     ║  PHASE 3         ║
  ║  BEFORE ATTACK   ║────▶║  DURING ATTACK   ║────▶║  AFTER ZT        ║
  ║                  ║     ║                  ║     ║  MITIGATION      ║
  ║ • Baseline PCAP  ║     ║ • Attack PCAP    ║     ║ • Recovery PCAP  ║
  ║ • iPerf3 normal  ║     ║ • iPerf3 degraded║     ║ • iPerf3 restored║
  ║ • RTT: baseline  ║     ║ • RTT: elevated  ║     ║ • RTT: recovered ║
  ╚══════════════════╝     ╚══════════════════╝     ╚══════════════════╝
```

---

## 📊 TCP Congestion Benchmarking

A research-grade comparison of **four TCP congestion control algorithms** across three distinct network conditions — directly addressing CLO_3 analysis requirements and mirroring active IETF standardization work.

<br/>

### Benchmark Matrix

| Condition | TCP Tahoe | TCP Reno | TCP Cubic | TCP BBR |
|:---------:|:---------:|:--------:|:---------:|:-------:|
| Baseline — 0% loss | ✅ Measured | ✅ Measured | ✅ Measured | ✅ Measured |
| Congested — 5% loss | ✅ Measured | ✅ Measured | ✅ Measured | ✅ Measured |
| Under Active SYN Flood | ✅ Measured | ✅ Measured | ✅ Measured | ✅ Measured |

<br/>

### Performance Metrics Captured

```
  📈  Throughput (Mbps)       — time-series graph per algorithm per condition
  📉  Round-Trip Time (ms)    — before / during / after each scenario
  📶  Jitter (ms)             — UDP stream variance under load
  ❌  Packet Loss (%)          — per algorithm comparison across conditions
  🔁  Retransmission Rate      — measures congestion response agility
```

> This benchmark mirrors active IETF research on **BBRv2** ([RFC 9002](https://datatracker.ietf.org/doc/rfc9002/), [BBRv2 Internet Draft](https://datatracker.ietf.org/doc/draft-cardwell-iccrg-bbr-congestion-control/)).

---

## 📡 SIEM-Style Observability

ZT-DTwin implements a full event correlation pipeline — from raw network telemetry to a correlated attack timeline — replicating the workflow of a Security Information and Event Management (SIEM) system.

```
  Network Events
       │
       ▼
  [Syslog Server] ──▶ [Correlation Engine] ──▶ [Event Dashboard]
                               │
                  ┌────────────▼─────────────┐
                  │      Event Timeline       │
                  │                           │
                  │  T+00s  ARP flood detected│
                  │  T+03s  DAI blocks attack │
                  │  T+05s  Throughput recov. │
                  │  T+12s  ACL log entry     │
                  │  T+18s  SNMP alert fired  │
                  └───────────────────────────┘
```

<br/>

### Observability Stack

| Feature | Tool | Output |
|:--------|:----:|:------:|
| **SNMP v2c/v3 Polling** | Network devices | Interface stats, error counters, utilization trends |
| **Packet Telemetry** | Wireshark PCAP | Anomaly signatures, flood pattern fingerprints |
| **Syslog Correlation** | Syslog Server | Timestamped attack ↔ performance event mapping |
| **NETCONF / YANG** | Conceptual (Week 14) | YANG model reference documentation |

---

## 🛠️ Tools & Technologies

| Category | Tool | Role in Project |
|:---------|:----:|:----------------|
| **Primary Simulation** | Cisco Packet Tracer 8.x | All layers — VLANs, routing, ACLs, servers, wireless |
| **Advanced Simulation** | GNS3 + real IOS *(bonus)* | BGP, advanced routing protocols, true IOS behavior |
| **Protocol Analysis** | Wireshark | Packet capture, attack forensics, telemetry extraction |
| **Performance Testing** | iPerf3 | TCP/UDP throughput, RTT, jitter benchmarking |
| **Attack Scripting** | Python + Scapy *(bonus)* | SYN flood generation, DNS injection, ARP spoofing |
| **Topology Diagrams** | Draw.io / Lucidchart | IEEE/TIA-568-compliant network diagrams |
| **Data Visualization** | Python (matplotlib) / Excel | Performance comparison charts and KPI graphs |
| **SDN** | Mininet + OpenFlow *(bonus)* | Dynamic flow-rule policy enforcement |
| **Observability** | Prometheus + Grafana *(bonus)* | Live real-time performance dashboard |

---

## 🗓️ Project Milestones

```
  MILESTONE 1              MILESTONE 2                MILESTONE 3
  ─────────────            ─────────────              ─────────────
  Weeks 2–3                Weeks 7–8                  Week 15
       │                        │                          │
       ▼                        ▼                          ▼
  ✅ Proposal             🔄 Mid-Progress             ⏳ Final Submission
  ─────────               ──────────────              ────────────────────
  • Title & scope         • Working VLANs             • IEEE report (15–20 pp)
  • Team information      • OSPF routing live         • Live demo session
  • Topology draft        • Wireshark captures        • Slide deck (12 slides)
  • Tools selection       • 5-minute demo             • All PCAP files
  • CLO mapping           • Attack draft scripts      • Attack scripts
                                                      • Benchmark graphs
```

---

## 📐 CLO & Grading Alignment

### Course Learning Outcomes

| CLO | Weight | Grade % | Project Coverage |
|:----|:------:|:-------:|:-----------------|
| **CLO_1** — Hardware & Software Understanding | 30% of project | 3% total | Full 5-layer documentation; physical topology with media types; complete protocol stack mapping |
| **CLO_2** — Configuration & Optimization | 30% of project | 3% total | VLAN configuration, OSPF/RIP routing, ACL/firewall rules, VPN tunnels, SSL/TLS — all configured, tested, and optimized |
| **CLO_3** — Analysis & Diagnosis | 40% of project | 4% total | Attack simulation with quantitative KPIs; 4-algorithm TCP benchmark; ZT mitigation effectiveness analysis; root-cause troubleshooting |

<br/>

### Rubric Alignment

| Criterion | Weight | How Addressed |
|:----------|:------:|:--------------|
| Technical Implementation & Correctness | 35% | Full 5-layer simulation across 6 network zones with all mandatory technologies |
| Analysis & Optimization | 30% | TCP benchmark graphs, attack impact data, OSPF vs. RIP convergence timing comparison |
| Security & Industry Best Practices | 15% | NIST ZTA, NIST SP 800-207, IPsec VPN, ACLs, 802.1X port authentication, cryptographic primitives |
| Documentation Quality | 10% | IEEE-format final report, Draw.io topology diagrams, structured README, appendices |
| Presentation & Demo Quality | 10% | Live troubleshooting demo with full attack scenario walkthrough |

<br/>

### Competitive Differentiation

| Typical CE313 Submission | ✅ ZT-DTwin |
|:------------------------|:-----------|
| Static topology — no threats modeled | Live attack simulation with quantitative pre/during/post impact measurement |
| Security as an afterthought (one firewall rule) | Full NIST-compliant Zero-Trust policy stack across all VLANs and network layers |
| Single TCP variant — no comparative analysis | 4-algorithm TCP benchmarking under 3 distinct network conditions |
| No observability or logging infrastructure | SIEM-style event correlation with Wireshark telemetry and Syslog timeline |
| Pass/fail connectivity checks only | Quantitative KPIs: throughput, RTT, jitter, packet loss — graphed per scenario |
| One routing protocol — no convergence analysis | OSPF vs. RIP performance comparison with measured convergence timing |

---

## 🌟 Bonus Opportunities

> Bonus features target an additional **+5%** on the final project grade.

| # | Bonus Feature | CE313 Alignment | Status |
|:-:|:-------------|:---------------:|:------:|
| 1 | HTTP/3 QUIC latency vs HTTP/1.1 under simulated packet loss | Week 6 + IETF research | ⏳ Planned |
| 2 | Mininet + OpenFlow SDN with dynamic attack-response flow rules | Week 13 (SDN/OpenFlow) | ⏳ Planned |
| 3 | Prometheus + Grafana live observability dashboard | Network Management | ⏳ Planned |
| 4 | BBRv2 analysis referencing IETF Internet Draft | Active TCP Research | ⏳ Planned |
| 5 | BitTorrent-style P2P DHT overlay simulation | Week 7 (Application Layer) | ⏳ Planned |

---

## 📁 Repository Structure

```
ZT-DTwin/
│
├── 📄 README.md                          ← Project documentation (this file)
│
├── 📂 docs/
│   ├── ZT-DTwin_Proposal.pdf             ← Full project proposal
│   └── topology.png                      ← Network topology diagram
│
├── 📂 simulation/
│   ├── ZT_DTwin_Enterprise.pkt           ← Cisco Packet Tracer simulation file
│   └── configs/                          ← Per-device CLI configurations
│       ├── ip address.pdf                   
│       
│                         
├── 📂 attacks/
│   ├── syn_flood.py                      ← Scapy SYN flood DoS script
│   ├── dns_poison.py                     ← DNS cache poisoning script
│   └── arp_spoof.py                      ← ARP spoofing / MITM script
│
├── 📂 pcaps/
│   ├── baseline_traffic.pcap             ← Normal traffic baseline capture
│   ├── syn_flood_attack.pcap             ← SYN flood attack capture
│   ├── syn_flood_mitigated.pcap          ← Post-ACL mitigation capture
│   └── arp_spoof_dai_blocked.pcap        ← DAI enforcement evidence
│
├── 📂 benchmarks/
│   ├── tcp_comparison_results.xlsx       ← iPerf3 raw data (all algorithms)
│   └── plot_results.py                   ← matplotlib performance graph generator
│
└── 📂 report/
    └── ZT-DTwin_Final_Report.pdf         ← IEEE-format final report
```

---

## 🚀 Getting Started

### Prerequisites

Before opening or building the simulation, ensure the following tools are installed:

| Tool | Version | Purpose | Download |
|:-----|:-------:|:-------:|:--------:|
| Cisco Packet Tracer | 8.x | Primary simulation environment | [NetAcad](https://www.netacad.com/courses/packet-tracer) |
| Python | 3.8+ | Attack scripts and benchmark graphing | [python.org](https://python.org) |
| Wireshark | Latest | PCAP analysis and traffic forensics | [wireshark.org](https://wireshark.org) |

<br/>

### 1. Clone the Repository

```bash
git clone https://github.com/shehroz/ZT-DTwin.git
cd ZT-DTwin
```

### 2. Open the Simulation

```bash
# Option A — Double-click the .pkt file in your file explorer
# Option B — Open via terminal (macOS/Linux)
open simulation/ZT_DTwin_Enterprise.pkt
```

### 3. Manual Build (if PKT version mismatch)

If the pre-built `.pkt` file does not open due to a version mismatch, follow this configuration order:

```bash
# Step 1: Open Cisco Packet Tracer and build the physical topology

# Step 2: Paste each config into the corresponding device CLI
#         (Simulation > CLI > paste config text)

# Configuration order:
#   1. CORE-R1, CORE-R2         (routers — routing protocols first)
#   2. DIST-SW1, DIST-SW2       (L3 distribution switches)
#   3. ACC-SW-IT through SRV    (access layer switches)
#   4. Servers                  (configure via GUI per SERVER_SETUP.txt)
#   5. End devices              (set all PCs/Laptops to DHCP)
```

### 4. Run Attack Scripts *(GNS3 or physical lab environment only)*

> ⚠️ **Warning:** These scripts generate real attack traffic. Run only in isolated lab environments. Never use on production or shared networks.

```bash
# Install dependencies
pip install scapy

# SYN Flood against web server
python attacks/syn_flood.py --target 10.10.40.50 --rate 1000

# ARP Spoofing between gateway and target host
python attacks/arp_spoof.py --gateway 10.10.20.1 --target 10.10.20.50

# DNS Cache Poisoning
python attacks/dns_poison.py --target 10.10.10.20
```

### 5. Generate Performance Benchmark Graphs

```bash
# Install graphing dependencies
pip install matplotlib pandas openpyxl

# Generate all TCP comparison plots
python benchmarks/plot_results.py
# Output: benchmarks/plots/tcp_comparison_all.png
```

### 6. Verify Connectivity (inside Packet Tracer CLI)

```
! ── On CORE-R1 ──────────────────────────────────────────
show ip ospf neighbor
show ip route
show ip nat translations
show access-lists

! ── On DIST-SW1 ──────────────────────────────────────────
show vlan brief
show interfaces trunk
show standby brief
show spanning-tree summary

! ── From IT-PC1 (User VLAN 20) ───────────────────────────
ping 8.8.8.8               ! Internet reachability (NAT)
ping 10.10.40.50           ! Cross-zone: Web server
ping 10.10.20.50           ! Same VLAN: peer host
traceroute 10.10.40.30     ! Hop-by-hop path to App server
```

---

## 👤 Team

<div align="center">

<br/>

| Field | Details |
|:-----:|:-------:|
| **Name** | Shehroz Majeed |
| **Student ID** | *(see institutional records)* |
| **Course** | CE313 — Computer Communications & Networks |
| **Institution** | GIK Institute of Engineering Sciences & Technology |
| **Instructor** | Engr. Muhammad Ahmad Nawaz |
| **Semester** | Spring 2026 |
| **Project Theme** | Zero-Trust · Network Digital Twin · Attack Simulation · TCP Benchmarking |

<br/>

---

### 📄 Full Proposal Document

The complete project proposal — including scope, methodology, and CLO justification — is available as a PDF:

**[📥 Download ZT-DTwin\_Proposal.pdf](./docs/ZT-DTwin_Proposal.pdf)**

---

<sub>CE313 — GIK Institute of Engineering Sciences & Technology · Spring 2026</sub>  
<sub>Instructor: Engr. Muhammad Ahmad Nawaz</sub>

<br/>

*Built with 🛡️ by Shehroz · Pursuing rigorous, portfolio-grade network engineering*

</div>

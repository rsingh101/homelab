# Cybersecurity Homelab Portfolio

> A self-built, production-grade SOC simulation environment — virtualized on Proxmox, instrumented with Sysmon, Suricata, and Cowrie, and engineered for detection engineering practice.

**Live site:** `https://rsingh101.github.io/homelab`

---

## About This Repository

This is the source code for my cybersecurity homelab portfolio website. It documents a real, actively-built hybrid wireless SOC lab environment running on dedicated hardware at home.

Everything here is factual and in progress. The site reflects the live state of the lab — what is built, what is being built, and what is planned next.

---

## File Structure

```
homelab/
├── index.html            ← Home page (hero, network diagram, system status)
├── documentation.html    ← Technical docs for all lab components
├── timeline.html         ← Chronological build log
├── about.html            ← About me, contact info, technical skills
├── style.css             ← All styles shared across every page
└── README.md             ← This file
```

**No frameworks. No build tools. No dependencies** beyond Google Fonts.
Each page is a standalone HTML file. `style.css` is the single shared stylesheet.
Easy to read, easy to update, easy for anyone to review.

---

## Pages

### `index.html` — Home
- Animated hero with lab summary
- SVG network topology diagram (4-layer: internet → isolation → lab LAN → Proxmox VMs)
- System status panel (live node statuses)
- Documentation quick-links
- Technologies & tools strip

### `documentation.html` — Documentation
Eight technical doc pages accessible via a sidebar:

| Page | Status |
|---|---|
| Proxmox Configuration | 🟠 In Progress  |
| Ubuntu Server Setup | 🟠 In Progress  |
| Windows 11 Deployment | 🟠 In Progress |
| Active Directory Integration | ⧖ Pending |
| Network Segmentation & Routing | ✅ Complete |
| Raspberry Pi Cluster | ✅ Complete |
| Kali Linux Attacker Environment | ⧖ Pending |
| SIEM & Detection Engineering | ⧖ Planned |

You can deep-link to any doc page: `documentation.html#proxmox`

### `timeline.html` — Build Timeline
Chronological log of every phase from first hardware to planned SIEM and detection engineering milestones.

### `about.html` — About
Personal background, contact info, and technical skills (all factual — sourced from real work history and lab).

---

## Lab Architecture

### Hardware

| Device | Role |
|---|---|
| Mac Mini i5 8th gen, 32GB, 512GB SSD | Proxmox VE hypervisor |
| ASUS RT-AX88U | Lab router / gateway |
| Raspberry Pi 3B | WAN bridge — Wi-Fi NAT, isolates lab from home |
| Raspberry Pi 4 | Suricata IDS gateway sensor |
| Raspberry Pi 4 | Cowrie honeypot (SSH/Telnet) |

### Network Topology

```
Home Network (10.0.0.0/24)
  └── Wi-Fi
        └── Raspberry Pi 3B  [wlan0: 10.0.0.16 | eth0: 192.168.100.2]
              NAT · DHCP · Firewall isolation
              └── ASUS RT-AX88U  [LAN: 192.168.50.0/24]
                    ├── Pi 4 — Suricata IDS
                    ├── Pi 4 — Cowrie Honeypot
                    └── Proxmox (Mac Mini)
                          ├── Ubuntu Server VM    ✅  SOC server
                          ├── Windows 11 VM       🟠  Endpoint (in progress)
                          ├── Windows Server 2022 ⧖   Active Directory
                          └── Kali Linux VM       ⧖   Attacker (post-AD)
```

### Build Roadmap

| Phase | Milestone | Date | Status |
|---|---|---|---|
| 01 | Network Restructuring — Pi 3B WAN bridge | Jan 2026 | ✅ |
| 02 | Suricata IDS Deployment | Jan 2026 | ✅ |
| 03 | Cowrie Honeypot Deployment | Jan 2026 | ✅ |
| 04 | Proxmox Hypervisor Setup | Feb 2026 | ✅ |
| 05 | Ubuntu SOC VM Deployment | Feb 2026 | ✅ |
| 06 | Windows 11 VM + Sysmon | Mar 2026 | 🟠 |
| 07 | Windows Server + Active Directory | Q2 2026 | ⧖ |
| 08 | Kali Linux Deployment | Q2 2026 | ⧖ |
| 09 | Wazuh Manager Integration | Q2 2026 | ⧖ |
| 10 | Elastic Stack + SIEM Dashboard | Q2 2026 | ⧖ |
| 11 | Detection Rules + MITRE ATT&CK Mapping | Q3 2026 | ⧖ |

---

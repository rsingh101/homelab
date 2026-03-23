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
| Proxmox Configuration | ✅ Complete |
| Ubuntu Server Setup | ✅ Complete |
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

## How to Deploy to GitHub Pages

### Step 1 — Create a GitHub account
Go to [github.com](https://github.com) → Sign up. Use a professional username — it becomes part of your URL.

### Step 2 — Create a new repository
1. Click **+** → **New repository**
2. Name it: `homelab`
3. Set visibility to: **Public**
4. Leave everything else unchecked
5. Click **Create repository**

### Step 3 — Upload all files
1. On the empty repo page click **"uploading an existing file"**
2. Drag and drop all 6 files at once:
   `index.html` · `documentation.html` · `timeline.html` · `about.html` · `style.css` · `README.md`
3. Write a commit message: `Initial upload`
4. Click **Commit changes**

### Step 4 — Enable GitHub Pages
1. Go to your repo → **Settings** tab
2. Left sidebar → **Pages**
3. Source: **Deploy from a branch**
4. Branch: **main** · Folder: **/ (root)**
5. Click **Save**

### Step 5 — Your site is live
Wait ~2 minutes. Visit:
```
https://your-username.github.io/homelab
```

### Step 6 — Fill in your details before publishing
Open `about.html` and replace:

```
Your Name            → your real full name
your@email.com       → your real email address
(000) 000-0000       → your phone number
your-profile         → your LinkedIn profile slug
your-username        → your GitHub username
```

---

## Updating the Site After Publishing

1. Go to your repo on GitHub
2. Click the file you want to edit
3. Click the **pencil / edit icon**
4. Make your change
5. Click **Commit changes**

The site rebuilds automatically within ~1 minute.

---

## Design

| Choice | Reason |
|---|---|
| Dark terminal aesthetic | Matches the work — the entire lab runs in terminal environments |
| JetBrains Mono | Monospace font used in professional IDEs and terminals |
| Syne display font | Contrast for headings without breaking the technical feel |
| `#00d4ff` cyan accent | High contrast on dark backgrounds, reads as technical |
| Scanline overlay | Subtle CRT texture via CSS — atmospheric without being distracting |
| No JS frameworks | Plain HTML + CSS + minimal vanilla JS — readable by anyone |

---

## Technologies Used in the Lab

`Proxmox VE` `Ubuntu Server 22.04` `Windows 11` `Windows Server 2022`
`Active Directory` `Sysmon` `Wazuh` `Elastic Stack` `Elasticsearch`
`Logstash` `Kibana` `Suricata IDS` `Cowrie Honeypot` `Kali Linux`
`Raspberry Pi` `ASUS RT-AX88U`

---

*Calgary, AB · Last updated March 2026 · Actively building*

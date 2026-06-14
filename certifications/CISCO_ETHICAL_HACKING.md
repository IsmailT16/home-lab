# Cisco — Junior Ethical Hacker

**Platform:** Cisco Skills for All
**Status:** 🔄 In Progress
**Focus:** Penetration Testing · Reconnaissance · Legal & Compliance Frameworks

> All practical work performed in a personal isolated lab environment on personally owned and authorized equipment.

---

## Skills Acquired

### Core Competencies

![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=flat&logo=kalilinux&logoColor=white)
![Nmap](https://img.shields.io/badge/Nmap-0E83CD?style=flat&logo=nmap&logoColor=white)
![Wireshark](https://img.shields.io/badge/Wireshark-1679A7?style=flat&logo=wireshark&logoColor=white)
![Scapy](https://img.shields.io/badge/Scapy-Python-3776AB?style=flat&logo=python&logoColor=white)
![Shodan](https://img.shields.io/badge/Shodan-FF0000?style=flat&logoColor=white)
![OSINT](https://img.shields.io/badge/OSINT-Google_Dorks-4285F4?style=flat&logo=google&logoColor=white)

| Domain | Skills |
|---|---|
| **Reconnaissance** | Passive & active recon, OSINT, DNS enumeration, SSL certificate analysis, Google Dorking, Shodan, employee intelligence gathering |
| **Network Analysis** | Nmap scan types (SYN, Connect, UDP, OS detection), packet crafting with Scapy, network sniffing with Wireshark |
| **Legal & Compliance** | GDPR, PCI-DSS, HIPAA, Rules of Engagement (RoE), penetration testing agreements, scope definition |
| **Methodology** | OSSTMM, OWASP, NIST, PTES — black box / grey box / white box testing strategies |
| **Lab Operations** | Kali Linux VM deployment, isolated lab environments, vulnerability target setup |

---

## Course Structure

### Module 1 — Introduction to Ethical Hacking and Penetration Testing

Understanding the foundations of penetration testing: why it exists, who performs it, and how to build a controlled lab environment.

**Key Topics:** Threat actors · Penetration testing careers · Lab design · Kali Linux setup

| Lab | Description |
|---|---|
| 1.1.3 | Researching PenTesting Careers |
| 1.2.6 | Compare Pentesting Methodologies (OSSTMM, OWASP, NIST, PTES) |
| 1.3.6 | Deploy a Pre-Built Kali Linux VM |
| 1.3.7 | Investigate Kali Linux |

---

### Module 2 — Planning and Scoping (Governance, Risk, and Compliance)

The legal and ethical framework that separates a professional penetration tester from an unauthorized attacker. This module covers everything that must be in place *before* a single packet is sent.

**Key Topics:** GDPR · PCI-DSS · HIPAA · Rules of Engagement · Black/Grey/White Box · Pentesting agreements · Code of conduct

> **Why this matters:** Employers verify that junior testers understand authorization boundaries. No engagement is legal without a signed scope, defined RoE, and compliance with local regulations.

| Lab | Description |
|---|---|
| 2.1.9 | Compliance Requirements and Local Restrictions |
| 2.2.9 | Pre-Engagement Scope and Planning |
| 2.2.10 | Create a Pentesting Agreement |
| 2.3.3 | Personal Code of Conduct |

---

### Module 3 — Information Gathering and Vulnerability Identification (Reconnaissance)

The most time-intensive phase of any real engagement. Covers both passive (no direct target contact) and active (direct interaction) reconnaissance techniques using industry-standard tools.

**Key Topics:** OSINT · DNS lookups · SSL certificate analysis · Social media scraping · Google Dorking · Shodan · Nmap · Scapy · Wireshark

#### 3.1 Passive Reconnaissance

Gathering intelligence without touching the target — legally and stealthily.

| Lab | Tool(s) | Description |
|---|---|---|
| 3.1.4 | OSINT Framework | Using OSINT Tools |
| 3.1.9 | nslookup · dig · whois | DNS Lookups |
| 3.1.12 | LinkedIn · OSINT | Employee Intelligence Gathering |
| 3.1.14 | crt.sh · OpenSSL | Finding Information from SSL Certificates |
| 3.1.18 | Multiple | Finding Out About the Organization |
| 3.1.19 | Google Dorks | Advanced Searches |
| 3.1.21 | Shodan | Shodan Searches |

#### 3.2 Active Reconnaissance

Direct interaction with the target — requires explicit authorization (RoE signed).

| Lab | Tool(s) | Description |
|---|---|---|
| 3.2.6 | Nmap | Enumeration with Nmap |
| 3.2.9 | Scapy | Packet Crafting |
| 3.2.10 | Wireshark | Network Sniffing |

---

## Hands-on Lab Evidence

> Evidence files are added as each lab is completed.

```
cisco-ethical-hacker/
├── module-1/
│   ├── lab-1.3.6-kali-vm-setup/
│   │   └── screenshots/
│   └── lab-1.3.7-kali-investigation/
│       └── terminal-output.txt
├── module-2/
│   ├── lab-2.2.10-pentesting-agreement/
│   │   └── agreement-template.md
│   └── lab-2.3.3-code-of-conduct/
│       └── personal-code-of-conduct.md
└── module-3/
    ├── lab-3.1.9-dns-lookups/
    │   └── dig-nslookup-output.txt
    ├── lab-3.1.19-google-dorking/
    │   └── dork-results.md
    ├── lab-3.1.21-shodan/
    │   └── shodan-results.md
    ├── lab-3.2.6-nmap-enumeration/
    │   └── nmap-scan-output.txt
    ├── lab-3.2.9-scapy/
    │   └── packet-craft-log.txt
    └── lab-3.2.10-wireshark/
        └── capture-analysis.md
```

---

## Methodology Reference

| Standard | Focus |
|---|---|
| OSSTMM | Technical security metrics and controls |
| OWASP | Web application security testing |
| NIST SP 800-115 | Federal technical guide for security testing |
| PTES | End-to-end penetration testing execution standard |

---

*[← Back to README](../README.md)*

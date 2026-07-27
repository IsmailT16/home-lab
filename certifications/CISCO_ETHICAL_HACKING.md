# Cisco Junior Ethical Hacker

**Platform:** Cisco Skills for All
**Status:** 🔄 In Progress
**Focus:** Penetration Testing, Reconnaissance, Legal & Compliance Frameworks

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
| **Legal & Compliance** | GDPR, PCI DSS, HIPAA, Rules of Engagement (RoE), penetration testing agreements, scope definition |
| **Methodology** | OSSTMM, OWASP, NIST, PTES; black box, grey box, and white box testing strategies |
| **Lab Operations** | Kali Linux VM deployment, isolated lab environments, vulnerability target setup |

---

## Module 1: Ethical Hacking Foundations & Environment Setup

Understanding the foundations of penetration testing: why it exists, who performs it, and how to build a controlled lab environment.

### Key Concepts & Knowledge Gained

* **Threat Actor Taxonomy:** motivations, capabilities, and tactics of different threat actors (script kiddies, hacktivists, organized crime syndicates, state sponsored APTs, insider threats).
* **Testing Methodologies:** structured security testing frameworks including OSSTMM, OWASP, NIST SP 800 115, and PTES, and how they keep a methodology consistent across an engagement.
* **Environment Sandboxing:** setting up isolated virtual environments to conduct offensive security testing without risking host network exposure or unintended side effects.

### Practical Implementation & Hands on Labs

| Lab | Description |
|---|---|
| 1.1.3 | Researching PenTesting Careers, mapping roles (Junior Pentester, Red Team Specialist, Security Consultant), certifications (CompTIA PenTest+, CEH, OSCP), and industry expectations |
| 1.2.6 | Compare Pentesting Methodologies, mapping standard phases (Reconnaissance → Enumeration → Exploitation → Post Exploitation → Reporting) across OWASP, NIST, and PTES |
| 1.3.6 | Deploy a Pre Built Kali Linux VM |
| 1.3.7 | Investigate Kali Linux, verifying core pentesting tools (nmap, wireshark, netcat, python3), system logs, and networking parameters |

---

## Module 2: Governance, Risk, Compliance & Scoping

The legal and ethical framework that separates a professional penetration tester from an unauthorized attacker. This module covers everything that must be in place before a single packet is sent.

> **Why this matters:** Employers verify that junior testers understand authorization boundaries. No engagement is legal without a signed scope, defined RoE, and compliance with local regulations.

### Key Concepts & Knowledge Gained

* **Regulatory Compliance:** GDPR, PCI DSS, and HIPAA, and their impact on data handling, legal liability, and testing parameters.
* **Rules of Engagement (RoE):** clear testing boundaries, authorization limits, time windows, forbidden targets, and emergency contact protocols.
* **Testing Strategies:** comparing Black Box (unknown environment), Gray Box (partial information), and White Box (known environment, full access) strategies.

### Practical Implementation & Hands on Labs

| Lab | Description |
|---|---|
| 2.1.9 | Compliance Requirements and Local Restrictions: legal restrictions and jurisdictional boundaries governing unauthorized access and security testing |
| 2.2.9 | Pre Engagement Scope and Planning: constructing formal scope documents defining in scope vs. out of scope IP ranges and domains |
| 2.2.10 | Create a Pentesting Agreement: drafting a binding penetration testing agreement |
| 2.3.3 | Personal Code of Conduct: ethical guidelines and professional standards on non disclosure, integrity, and data handling |

---

## Module 3: Reconnaissance and Vulnerability Identification

The most time intensive phase of any real engagement. Covers both passive (no direct target contact) and active (direct interaction) reconnaissance techniques using industry standard tools.

### 3.1 Passive Reconnaissance (OSINT)

Extracting target metadata, administrative contact details, and organization structures without sending any packets to the target infrastructure.

**Tools & Techniques Used:**

* **DNS Enumeration:** `nslookup` and `dig` for zone information, MX, TXT, and NS records.
* **SSL/TLS Inspection:** querying certificate transparency logs (crt.sh) and OpenSSL to extract hidden subdomains and internal naming schemes.
* **Advanced Google Dorking:** search operators such as `filetype:pdf`, `site:`, `inurl:`, and `intitle:"index of"` to uncover exposed documents and directory listings.
* **Shodan Search Engine:** querying internet connected devices, open ports, and banner information via Shodan filters.
* **Employee Intelligence Gathering:** LinkedIn and OSINT techniques to build a picture of an organization's staff and structure.

| Lab | Tool(s) | Description |
|---|---|---|
| 3.1.4 | OSINT Framework | Using OSINT Tools |
| 3.1.9 | nslookup, dig, whois | DNS Lookups |
| 3.1.12 | LinkedIn, OSINT | Employee Intelligence Gathering |
| 3.1.14 | crt.sh, OpenSSL | Finding Information from SSL Certificates |
| 3.1.18 | Multiple | Finding Out About the Organization |
| 3.1.19 | Google Dorks | Advanced Searches |
| 3.1.21 | Shodan | Shodan Searches |

### 3.2 Active Reconnaissance

Direct interaction with the target, requiring explicit authorization (signed RoE).

**Tools & Techniques Used:**

* **Nmap Port Scanning:** SYN Stealth (`-sS`), TCP Connect (`-sT`), UDP (`-sU`), Service Versioning (`-sV`), and OS Detection (`-O`) scans.
* **Scapy Packet Crafting:** using Python's scapy library to build custom IP/TCP packets, manipulate TCP flags (SYN, FIN, NULL, XMAS), and analyze raw response behavior.
* **Wireshark Traffic Analysis:** sniffing and inspecting pcap files to capture credentials, dissect protocol handshakes, and identify unencrypted traffic (HTTP, FTP, Telnet).

| Lab | Tool(s) | Description |
|---|---|---|
| 3.2.6 | Nmap | Enumeration with Nmap |
| 3.2.9 | Scapy | Packet Crafting |
| 3.2.10 | Wireshark | Network Sniffing |

---

## Methodology Reference

| Standard | Focus |
|---|---|
| OSSTMM | Technical security metrics and controls |
| OWASP | Web application security testing |
| NIST SP 800 115 | Federal technical guide for security testing |
| PTES | End to end penetration testing execution standard |

---

*[← Back to README](../README.md)*

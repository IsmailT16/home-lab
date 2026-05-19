# Lab 01 - Home Network Assessment

**Date:** May 2026
**Status:** ✅ Completed
**Environment:** Kali Linux · VirtualBox (Bridged Adapter) · Home LAN /24

---

## Goal

Perform a full reconnaissance of the home network — discover all devices, fingerprint services, analyze traffic, and demonstrate a Man-in-the-Middle attack on a personally owned device.

All testing performed on personally owned and authorized equipment.

---

## Network Setup

Initial issue: VM was running in NAT mode (IP: 10.0.2.15) — VirtualBox responded to all ICMP probes resulting in 256 fake hosts.

**Fix: Switched to Bridged Adapter**

| Detail | Value |
|---|---|
| Kali IP | 192.168.x.156 |
| Network | 192.168.x.0/24 |
| Interface | eth0 (Bridged) |

---

## Phase 1 - Network Reconnaissance

```bash
sudo nmap -sn 192.168.x.0/24
```

**Discovered 6 live hosts:**

| Device Type | MAC Vendor | Notes |
|---|---|---|
| Home Router | [redacted] | Main gateway |
| Mobile Phone | Randomized | MAC privacy active |
| Mobile Phone | Randomized | MAC privacy active |
| Windows PC | Intel Corporate | Fully firewalled |
| IoT Streaming Device | Amazon Technologies | Android-based |
| Kali Machine | VirtualBox | Tester |

> Randomized MACs = Android/iOS MAC privacy feature. Normal behavior.

---

## Phase 2 - Service & OS Fingerprinting

```bash
sudo nmap -A <target>
sudo nmap --script vuln <target>
```

**Home Router:**
- Port 53/TCP — DNS
- Port 80/TCP — HTTP, Apache — web admin panel
- Port 8443/TCP — HTTPS, vendor SSL certificate
- Port 5060/TCP — SIP/VoIP (filtered)
- OS: OpenWrt, Linux kernel 4.x

**IoT Streaming Device:**
- Port 8009/TCP — AJP (tcpwrapped)
- OS: Android 5.0.2 (EOL since 2014)
- Vuln scan: no exploitable findings on exposed port

**Windows PC:**
- All 1000 ports filtered - Windows Firewall active
- No OS details leaked - well hardened

---

## Phase 3 - Traffic Analysis (Wireshark)

```bash
sudo wireshark
```

Captured traffic passively on eth0. Key observations:

- mDNS from IoT device to `224.0.0.251` — device announcing services on LAN
- DNS queries visible in plaintext between hosts and router
- HTTPS traffic: domains visible, content encrypted (TLS)
- Background app traffic - devices contacting servers without user interaction

**Useful filters:**
```
dns
ip.addr == <target>
ip.addr == <target> && !mdns
http && ip.addr == <target>
```

---

## Phase 4 - ARP Spoofing / MITM

Performed ARP poisoning between personal Android device and router using Ettercap:

```bash
sudo ettercap -T -q -i eth0 -M arp:remote /<gateway>// /<target>//
```

**Results:**
- ARP cache of phone successfully poisoned
- Kali MAC visible as source on phone packets in Wireshark ✅
- DNS queries intercepted in real time ✅
- google.com lookup captured live ✅
- HTTPS content remained encrypted — only domains visible

**Key insight:** This is exactly how attackers operate on public WiFi. HTTPS protects content. HTTP exposes everything. VPN protects both.

---

## Findings Summary

| Device | Risk | Finding |
|---|---|---|
| Router | Medium | HTTP admin panel exposed, web server fingerprinted |
| Router | Low | Overly long SSL certificate validity (vendor issue) |
| IoT Device | Medium | Android 5.0.2 EOL — no updates since 2014 |
| Windows PC | Low | Fully firewalled, no information leaked |
| Mobile Phones | Low | MAC randomization active |

---

## Skills Practiced

- [x] VM network configuration (NAT vs Bridged)
- [x] Subnet scanning and host discovery
- [x] Port scanning and service enumeration
- [x] OS and banner fingerprinting
- [x] Vulnerability scanning with nmap scripts
- [x] Passive packet capture and protocol analysis
- [x] ARP spoofing and MITM execution
- [x] DNS interception and traffic inspection
- [x] Risk assessment and findings documentation

---

## Tools Used

| Tool | Version | Purpose |
|---|---|---|
| Nmap | 7.98 | Scanning and fingerprinting |
| arp-scan | 1.10.0 | Host discovery with MAC info |
| Wireshark | Latest | Packet capture and analysis |
| Ettercap | 0.8.4 | ARP spoofing / MITM |

---

*[← Back to README](../README.md)*

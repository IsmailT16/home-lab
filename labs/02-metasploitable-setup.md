# Lab 02 - Metasploitable 2 Setup

**Date:** May 2026
**Status:** 🔄 In Progress
**Environment:** Kali Linux · VirtualBox · Internal Network

---

## Goal

Set up Metasploitable 2 as an intentionally vulnerable target VM to practice real exploitation techniques in a legal, controlled environment.

---

## What is Metasploitable 2?

A deliberately vulnerable Linux VM designed for security training. It runs outdated, misconfigured services with known vulnerabilities — a legal target to practice against.

---

## Network Setup

The challenge was getting both VMs to communicate without exposing Metasploitable to the real network.

**Solution: VirtualBox Internal Network**

| VM | Adapter | Type | IP |
|---|---|---|---|
| Kali | eth0 | NAT | 10.0.2.15 (Internet) |
| Kali | eth1 | Internal Network (intnet) | 192.168.56.20 |
| Metasploitable | eth0 | Internal Network (intnet) | 192.168.56.10 |

This way Kali has internet access AND can reach Metasploitable, while Metasploitable is completely isolated from the real network.

---

## Setup Steps

**1. Import Metasploitable VMDK into VirtualBox**
- New VM → Linux → Ubuntu 32-bit → Use existing disk → select `.vmdk`
- RAM: 512MB is enough

**2. Configure network on both VMs**
- Metasploitable: Adapter 1 → Internal Network → name: `intnet`
- Kali: Adapter 1 → NAT | Adapter 2 → Internal Network → name: `intnet`

**3. Set static IPs (required after every reboot)**

On Metasploitable:
```bash
sudo ifconfig eth0 192.168.56.10 netmask 255.255.255.0
```

On Kali:
```bash
sudo ip addr add 192.168.56.20/24 dev eth1
sudo ip link set eth1 up
sudo ip route add 192.168.56.0/24 dev eth1
```

**4. Verify connectivity**
```bash
ping 192.168.56.10
```

---

## Results

```
ping 192.168.56.10
10 packets transmitted, 10 received, 0% packet loss ✅
```

Nmap scan confirmed multiple open ports on Metasploitable ✅

---

## Challenges

- Host-only adapter failed due to conflicting VPN drivers (NordVPN, WireGuard, Cisco AnyConnect)
- Internal Network used as workaround - no host driver needed
- IPs must be set manually after each reboot (no DHCP on internal network)

---

## Skills Practiced

- VirtualBox network modes (NAT, Bridged, Host-only, Internal)
- Manual static IP assignment
- Cross-VM routing configuration
- Diagnosing network adapter conflicts

---

## Next Steps

- [ ] Full Nmap service scan - document all open ports
- [ ] Identify exploitable services
- [ ] First exploit with Metasploit Framework
- [ ] Privilege escalation
- [ ] Document findings in Lab 03

---

*[← Back to README](../README.md)*

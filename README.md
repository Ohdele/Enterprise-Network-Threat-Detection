## Enterprise Network Threat Detection Project

This project simulates a realistic enterprise network, executes an ARP‑based man‑in‑the‑middle attack to intercept plaintext credentials, and performs packet‑level forensics and ARP‑cache intrusion detection across isolated VirtualBox environments.
All commands and raw outputs from the environment have been captured verbatim.

### Environment
* **Virtualization:** VirtualBox
* **VMs:**
    * VPN Server (Attacker) – 192.168.10.11
    * Client Server (Target) – 192.168.10.20
* **Network:** Isolated /24 segment over enp0s8

### What This Project Demonstrates
* ARP spoofing between target and gateway
* Traffic interception and packet capture
* Extraction of plaintext credentials from captured packets
* Detection of spoofing activity using ARP‑cache inspection
* Documentation of complete command‑line workflow

### Artifacts
All commands and full terminal output are stored in:
[docs/network-forensics-output.txt](docs/network-forensics-output.txt)

This file documents:
* IP discovery and network validation
* Ettercap ARP‑poisoning attempts
* TShark and packet‑capture operations
* Packet 14 credential bytes
* ARP‑cache inspection (intrusion detection)

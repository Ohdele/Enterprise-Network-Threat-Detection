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

## 5. Expanded Scope: Protocol Analysis and Suspicious Behavior Detection

The following sections document the fulfillment of the expanded project requirements, focusing on analyzing standard network protocol insecurity and detecting anomalous traffic.

### 5.1 Protocol Analysis (DNS, HTTP, SMTP)

* **Goal:** Demonstrate that communication over standard, unencrypted protocols exposes sensitive data to network eavesdroppers.
* **Findings:**
    * **HTTP:** Full request URI and server response (200 OK) captured and extracted in **plaintext**.
    * **DNS:** The query domain was confirmed to be transmitted in **plaintext** when forced across the network.
    * **SMTP:** The email sender, recipient, and message body were confirmed to be transmitted in **plaintext**.
* **Conclusion:** Unencrypted protocols present a critical network security vulnerability, confirming the need for encrypted alternatives (HTTPS, DNS over TLS, SMTPS).

### 5.2 Suspicious Behavior Detection

* **Goal:** Simulate reconnaissance or beaconing activity and verify that it generates a detectable signature in packet captures.
* **Simulation:** An anomalous TCP connection attempt was made from the Client to a high, non-standard port (`44444`) on the VPN Server.
* **Detection:** Packet analysis successfully captured the TCP SYN request (`0x0002`) followed by the immediate RST, ACK (`0x0014`) from the server.
* **Conclusion:** This pattern is a clear indicator of **anomalous lateral movement** or **network reconnaissance**, which would be immediately flagged by an intrusion detection system for further investigation.

---

**Full command-line workflow and all raw output are detailed in:**

 [docs/network-forensics-output.txt](docs/network-forensics-output.txt)

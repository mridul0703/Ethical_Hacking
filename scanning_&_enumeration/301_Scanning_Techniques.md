# 301. Scanning Techniques

Scanning is a vital part of the ethical hacking process, allowing hackers to discover vulnerabilities, active systems, open ports, and services. It is the step where they identify potential weaknesses in a target's infrastructure.

> 🔍 *“Scanning provides a map of potential attack surfaces.”*

---

## 📡 Network Scanning

Network scanning is the process of identifying live hosts, active devices, and other systems within a network. It helps to map out the network and discover reachable devices.

### 🧰 Techniques:
- **Ping Sweep**: Checks which hosts are live by sending ICMP requests.
- **Traceroute**: Identifies the path packets take from one system to another, revealing network architecture.

### 🛠 Tools:
- **Nmap**: A powerful tool used for discovering hosts and services on a computer network.
- **Angry IP Scanner**: A fast IP scanner that detects live hosts.
- **Netdiscover**: Used for network discovery via ARP (Address Resolution Protocol).

> 🎯 **Objective**: Find which systems are on the network and identify potential vulnerabilities based on open services.

---

## 🔓 Port Scanning (TCP, UDP)

Port scanning involves checking open ports on a target system to find services that are running and may be vulnerable.

### 🧰 Types of Port Scanning:
#### 1. **TCP Scanning**:
   - **SYN Scan (Stealth Scan)**: Sends SYN packets and waits for a response to identify open ports.
   - **Connect Scan**: Completes the TCP handshake to confirm open ports.
   - **FIN Scan**: Sends a FIN packet, which can sometimes bypass firewalls.

#### 2. **UDP Scanning**:
   - **UDP Scan**: Sends UDP packets to target ports and waits for a response to determine open or closed ports.
   - **UDP Connect Scan**: Similar to TCP, but with UDP packets.

### 🛠 Tools:
- **Nmap**: The most widely used tool for port scanning.
  - Command example: `nmap -sS [Target IP]` for SYN scan or `nmap -sU [Target IP]` for UDP scanning.
- **Masscan**: A faster alternative to Nmap, useful for scanning large networks.
- **Netcat**: A networking tool often used for banner grabbing or simple port scans.

> 📌 **Note**: Port scanning should only be done with permission as it can trigger intrusion detection systems (IDS) or firewalls.

---

## 🔍 Vulnerability Scanning

Vulnerability scanning involves using automated tools to search for known vulnerabilities in systems, services, or applications.

### 🧰 Techniques:
- **Service Fingerprinting**: Identifying services on open ports to match them to known vulnerability databases.
- **Configuration Scanning**: Checking for weak configurations or security settings in software and hardware systems.
- **Patch Scanning**: Verifying if systems are up to date with the latest security patches.

### 🛠 Tools:
- **Nessus**: A popular vulnerability scanner used to find and report on vulnerabilities across different platforms.
- **OpenVAS**: An open-source vulnerability scanning tool that provides detailed scanning reports.
- **Qualys**: A cloud-based vulnerability management tool with continuous monitoring.
- **Nikto**: A web server scanner that identifies security issues in web applications.

> 🛡️ **Goal**: Identify known vulnerabilities and misconfigurations in systems, so they can be patched or mitigated.

---

## 📘 Conclusion

- **Network Scanning**: Identifies active devices and systems in the target network.
- **Port Scanning**: Identifies open ports that could expose services or vulnerabilities.
- **Vulnerability Scanning**: Finds security flaws in software, systems, and configurations.

Scanning is an essential part of the hacking process as it provides valuable data about a target system, allowing the ethical hacker to move to the next phase — exploitation.

> 🔒 *Remember: Always get explicit written permission before performing any form of scanning to ensure you're within legal boundaries.*

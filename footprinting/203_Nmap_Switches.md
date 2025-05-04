
# 203. Nmap Switches

Nmap (Network Mapper) is one of the most widely used open-source tools for network exploration and security auditing. Understanding and using Nmap's various switches is critical for performing effective port scanning and vulnerability assessments.

> 🎯 *“The power of Nmap lies in its versatility — it is the tool of choice for network discovery and vulnerability scanning.”*

---

## 🧩 Overview of Nmap

Nmap helps in:
- **Network mapping**: Discover devices on a network.
- **Port scanning**: Identify open ports on target systems.
- **Service identification**: Find out which services are running on a system.
- **OS detection**: Discover the operating system running on the target machine.

Nmap is used by network administrators, penetration testers, and attackers alike to gather crucial data about target systems.

---

## 🧰 Common Nmap Switches

### 1. **-sT (TCP Connect Scan)**
- **Description**: This is a **full connection scan** using the operating system's networking functions.
- **How it works**: It attempts to establish a full TCP connection with the target system. If the connection is successful, the port is open.
- **Usage**: It is the **most reliable scan** but can be easily detected.
- **Example**: 
  ```bash
  nmap -sT 192.168.1.1
  ```

### 2. **-sS (SYN Scan)**
- **Description**: A stealth scan that only sends SYN packets to the target system.
- **How it works**: Nmap sends a SYN packet to the target and waits for a response. If the target responds with a SYN-ACK, it indicates that the port is open. If it responds with a RST (reset) packet, the port is closed.
- **Advantages**: Stealthier than -sT because it does not complete the TCP handshake.
- **Usage**: Most commonly used for quick and stealthy port scanning.
- **Example**:
  ```bash
  nmap -sS 192.168.1.1
  ```

### 3. **-sU (UDP Scan)**
- **Description**: Scans UDP ports to determine if they are open.
- **How it works**: Similar to TCP scanning but works with UDP packets instead of TCP.
- **Usage**: Used for scanning UDP services, such as DNS, SNMP, and NTP.
- **Example**:
  ```bash
  nmap -sU 192.168.1.1
  ```

### 4. **-p (Port Selection)**
- **Description**: Specifies which ports to scan on the target system.
- **How it works**: You can specify a single port, a range of ports, or a comma-separated list of ports.
- **Usage**: Can be used in combination with other scans (e.g., -sS -p 80,443).
- **Example**:
  ```bash
  nmap -sS -p 22,80,443 192.168.1.1
  ```

### 5. **-sA (ACK Scan)**
- **Description**: Used to determine the firewall rules and filter status.
- **How it works**: Nmap sends an ACK packet to the target system. If a RST packet is returned, the port is open; if no response is received, the port is filtered by a firewall.
- **Usage**: Helps in identifying firewall settings and filtering mechanisms.
- **Example**:
  ```bash
  nmap -sA 192.168.1.1
  ```

### 6. **-sF (FIN Scan)**
- **Description**: A stealth scan that sends FIN packets to the target system.
- **How it works**: A FIN packet is sent to the target port. If the port is closed, the target will send a RST packet back. If the port is open, it will typically not respond.
- **Usage**: Can bypass certain firewalls and packet filters.
- **Example**:
  ```bash
  nmap -sF 192.168.1.1
  ```

### 7. **-sX (Xmas Scan)**
- **Description**: Another stealth scan that sends packets with the FIN, URG, and PUSH flags set.
- **How it works**: Similar to -sF, the target will typically not respond to an open port, but will respond with a RST if the port is closed.
- **Usage**: Works on some firewalls and packet filters but is rare.
- **Example**:
  ```bash
  nmap -sX 192.168.1.1
  ```

### 8. **-O (OS Detection)**
- **Description**: Detects the operating system of the target machine.
- **How it works**: Nmap uses several heuristics, including analyzing TCP/IP stack behavior, to determine the operating system of the target.
- **Usage**: Provides valuable information for penetration testers.
- **Example**:
  ```bash
  nmap -O 192.168.1.1
  ```

### 9. **-v (Verbose Output)**
- **Description**: Increases the verbosity of the output to display more detailed results.
- **How it works**: Adds more information about the scan process and findings.
- **Usage**: Useful for troubleshooting and analyzing scan details.
- **Example**:
  ```bash
  nmap -v 192.168.1.1
  ```

### 10. **-A (Aggressive Scan)**
- **Description**: Performs a comprehensive scan that includes OS detection, version scanning, script scanning, and traceroute.
- **How it works**: This combines several Nmap techniques in one command to give a complete overview of the target machine.
- **Usage**: Useful for deep scans but can be noisy and easily detected.
- **Example**:
  ```bash
  nmap -A 192.168.1.1
  ```

### 11. **-T (Timing Template)**
- **Description**: Adjusts the timing of the scan to control speed and stealthiness.
- **How it works**: The -T option can be set from 0 (slowest) to 5 (fastest). Increasing the speed can make the scan more detectable but reduce scan time.
- **Usage**: Use for stealthier scans (lower values) or faster scans (higher values).
- **Example**:
  ```bash
  nmap -T4 192.168.1.1
  ```

### 12. **-Pn (No Ping)**
- **Description**: Skips the host discovery (ping scan) and assumes the target is up.
- **How it works**: If the target is behind a firewall that blocks ping requests, this option allows you to scan the target without first confirming it is online.
- **Usage**: Useful when performing stealth scans or scanning a host that might not respond to ICMP requests.
- **Example**:
  ```bash
  nmap -Pn 192.168.1.1
  ```

## 🔒 Additional Useful Nmap Switches

### 13. **-sL (List Scan)**
- **Description**: Lists the targets without scanning them.
- **Usage**: Great for verifying that a list of hosts is correctly formatted.
- **Example**:
  ```bash
  nmap -sL 192.168.1.1/24
  ```

### 14. **--script (Nmap Scripting Engine)**
- **Description**: Executes Nmap scripts for specific tasks, like vulnerability scanning.
- **Usage**: Great for discovering more complex vulnerabilities, such as SQL injection or XSS.
- **Example**:
  ```bash
  nmap --script http-sql-injection 192.168.1.1
  ```

📘 **Summary of Key Nmap Switches**

| Switch   | Description                                                      | Example Command                         |
|----------|------------------------------------------------------------------|-----------------------------------------|
| -sT      | TCP Connect Scan                                                 | nmap -sT 192.168.1.1                   |
| -sS      | SYN Scan (Stealth Scan)                                          | nmap -sS 192.168.1.1                   |
| -p       | Specify ports to scan                                            | nmap -p 22,80 192.168.1.1             |
| -O       | OS Detection                                                     | nmap -O 192.168.1.1                    |
| -A       | Aggressive Scan (OS, version, script scan, traceroute)           | nmap -A 192.168.1.1                    |
| -T4      | Timing (faster scan)                                             | nmap -T4 192.168.1.1                   |
| -v       | Verbose output                                                   | nmap -v 192.168.1.1                    |
| --script | Run Nmap scripts for specific tasks                               | nmap --script http-vuln-cve2014-0160 192.168.1.1 |

---
> 🧠 Mastering Nmap switches enables effective scanning and mapping of networks, which is essential for both penetration testers and system defenders

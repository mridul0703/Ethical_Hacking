# A02. TCP Flag Usage in Attacks

The **Transmission Control Protocol (TCP)** is one of the core protocols of the Internet, allowing reliable communication between systems. However, it is also susceptible to various types of attacks due to its inherent features, particularly its **flags**. This document outlines **SYN Flood** and **TCP Reset Attacks**, which exploit the TCP flag mechanism to disrupt and interfere with network services.

---

## 📌 1. Overview of TCP Flags

TCP flags are control bits used in the TCP header to manage the state of a connection. These flags include:
- **SYN**: Synchronize the sequence number.
- **ACK**: Acknowledgment of received data.
- **FIN**: Request to finish the connection.
- **RST**: Reset the connection.
- **PSH**: Push the data to the application.
- **URG**: Urgent data processing.
- **ECE** and **CWR**: ECN (Explicit Congestion Notification) related flags.

These flags are integral to maintaining the state of a TCP connection, and manipulating them can lead to various types of **Denial of Service (DoS)** or **Denial of Service (DDoS)** attacks.

---

## ⚔️ 2. SYN Flood Attack

The **SYN Flood** attack is a type of **DoS attack** that exploits the three-way handshake used in establishing a TCP connection. It aims to **overwhelm** the target server, causing it to exhaust its resources, resulting in service disruption.

### 🔍 Mechanism of SYN Flood
1. The attacker sends **SYN packets** with a **spoofed source IP address** to the target server.
2. The target server responds with **SYN-ACK packets** to the spoofed IP address.
3. The **final ACK** to complete the handshake is never sent, leaving the connection in a **half-open state**.

### 💥 Effects:
- **Exhausted system resources** due to half-open connections.
- The server may run out of memory or processing capacity, making it unable to accept legitimate connections.

### 🛠️ Tools Used:
- **Hping3**: A popular tool for generating SYN Floods.
- **LOIC** (Low Orbit Ion Cannon): A tool used for DoS attacks.

### ⚠️ Countermeasures:
- **Firewall Filters** to block excessive SYN requests.
- **Intrusion Detection Systems (IDS)** to identify abnormal traffic patterns.
- **SYN Cookies**: A mechanism where the server sends a response based on a cookie instead of allocating resources until the handshake is completed.

---

## 🚨 3. TCP Reset Attacks

A **TCP Reset Attack** involves sending **TCP RST (Reset)** packets to **terminate an active connection** between two systems. It exploits the trust established between two communicating systems, often resulting in an unexpected disconnection.

### 🔍 Mechanism of TCP Reset Attack
1. The attacker **eavesdrops** on a legitimate TCP connection.
2. Using the sequence and acknowledgment numbers from the conversation, the attacker sends **RST packets**.
3. The **RST packet** is received by both parties, causing them to close the connection abruptly.

### 💥 Effects:
- **Disruption of ongoing communication** between legitimate users.
- The attacked service may experience unexpected shutdowns, leading to service unavailability.
- Can be used in conjunction with **Man-in-the-Middle (MitM)** attacks to forcibly disconnect sessions.

### 🛠️ Tools Used:
- **Scapy**: A powerful Python-based tool for crafting custom packets, including TCP Reset packets.
- **Ettercap**: A tool for network sniffing and Man-in-the-Middle attacks, which can be used to inject RST packets.

### ⚠️ Countermeasures:
- **Encrypted Sessions** (e.g., using SSL/TLS) prevent attackers from reading session data and injecting RST packets.
- **Sequence Number Randomization**: Randomizing the sequence numbers makes it difficult for attackers to guess the correct values for an RST injection.
- **TCP Interception Techniques**: Implementing methods to detect and prevent unauthorized RST packets.

---

## 💡 4. Summary

Both **SYN Floods** and **TCP Reset Attacks** exploit the fundamental properties of the TCP handshake and its flags to disrupt network communication. While **SYN Floods** attempt to exhaust system resources through uncompleted handshakes, **TCP Reset Attacks** target existing connections to force them to abruptly terminate.

**Preventive Measures**:
- Using **firewall filters** and **IDS/IPS systems**.
- Ensuring proper **sequence number management**.
- **Encrypting communication** to secure connections from being easily hijacked.

These attacks underscore the importance of maintaining secure and properly configured network systems to prevent disruptions caused by malicious traffic.

---

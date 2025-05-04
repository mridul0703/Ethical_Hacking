
# 502. Network Attacks

Understanding various network-based attacks is essential for securing computer systems. In this chapter, we explore two of the most common and dangerous network attacks: **Denial of Service (DoS/DDoS)** and **Man-in-the-Middle (MITM)** attacks.

---

## 🚫 Denial of Service (DoS) and Distributed Denial of Service (DDoS)

### ❓ What is DoS?

A **Denial of Service (DoS)** attack aims to make a system, network, or service **unavailable to its intended users** by overwhelming it with traffic or exploiting system vulnerabilities.

### 🔄 What is DDoS?

A **Distributed Denial of Service (DDoS)** attack uses **multiple compromised systems (botnets)** to flood a target, making it much harder to mitigate than a single-source DoS.

---

### ⚙️ How DoS/DDoS Attacks Work

1. **Attack Planning**:
   - Choose a vulnerable target (e.g., web server, DNS).
2. **Traffic Generation**:
   - Send high volumes of packets or requests.
3. **System Overload**:
   - Resources are exhausted, making services unavailable.

---

### 🚀 Common Types of DoS/DDoS Attacks

| Type                 | Description |
|----------------------|-------------|
| **UDP Flood**        | Sends large numbers of UDP packets to random ports. |
| **SYN Flood**        | Exploits TCP handshake process to consume resources. |
| **HTTP Flood**       | Mimics legitimate traffic with GET/POST requests. |
| **Ping of Death**    | Sends malformed or oversized ICMP packets. |
| **Smurf Attack**     | ICMP requests are sent to a network's broadcast address. |

---

### 🔐 Countermeasures

- Use **rate limiting** and **traffic filtering**
- Employ **firewalls and intrusion detection systems**
- Use **CDNs** and **DDoS protection services** (e.g., Cloudflare, AWS Shield)
- **Update and patch** all systems regularly

---

## 👥 Man-in-the-Middle (MITM) Attack

### ❓ What is MITM?

A **Man-in-the-Middle (MITM)** attack occurs when a malicious actor intercepts and possibly alters communication between two parties **without their knowledge**.

---

### 🧰 Techniques of MITM Attacks

| Technique            | Description |
|----------------------|-------------|
| **Packet Sniffing**  | Captures unencrypted traffic on the network. |
| **Session Hijacking**| Attacker takes over a user’s active session. |
| **SSL Stripping**    | Downgrades HTTPS to HTTP to steal data. |
| **ARP Spoofing**     | Associates attacker’s MAC with a trusted IP. |
| **DNS Spoofing**     | Redirects domain name to malicious IP. |

---

### 🧱 Countermeasures

- Use **HTTPS and strong SSL/TLS certificates**
- Enable **VPNs** on public or untrusted networks
- Employ **Public Key Infrastructure (PKI)**
- Use **HSTS (HTTP Strict Transport Security)**
- Monitor for **abnormal ARP/DNS activity**

---

> 📘 *Both DoS/DDoS and MITM attacks pose major threats to network security. Defending against them requires a combination of monitoring, secure protocols, and timely updates.*

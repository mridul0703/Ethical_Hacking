# 201. Types of Footprinting

Footprinting is the **initial phase of ethical hacking**, focused on collecting information about a potential target to identify vulnerabilities. It can be done either **passively** or **actively**, depending on whether the hacker interacts directly with the target system.

> 🎯 *Goal: Gather comprehensive intelligence about a target to plan further stages of penetration testing or vulnerability analysis.*

---

## 📌 1. What is Footprinting?

Footprinting, also called reconnaissance, is the process of **systematically gathering information** about a target system, individual, or organization, often used to map out the attack surface.

### 🔍 Objectives of Footprinting:
- Identify domain names, IP ranges, and DNS records.
- Gather employee details, email addresses, and organizational structure.
- Discover operating systems, software versions, and exposed services.
- Understand the network topology and security mechanisms.

---

## 🕵️ 2. Types of Footprinting

Footprinting can be broadly categorized into:

### ✅ 2.1 Passive Footprinting

Passive footprinting involves **indirect methods** of collecting data **without interacting with the target** system directly. It is stealthy and generally **undetectable**.

#### 📚 Examples:
- Searching on Google, Bing, or DuckDuckGo
- Reading social media and press releases
- Using third-party services like WHOIS, Netcraft, Shodan

#### 🔧 Common Tools:
- **Google Dorking** – Advanced search queries to uncover sensitive data
- **Netcraft** – Web server information and hosting history
- **Whois Lookup** – Domain owner, registration dates, and IP blocks
- **Maltego** – Relationship mapping via open-source data

#### 📄 Information Gathered:
- Domain and IP info
- Employee names and emails
- OSINT (Open Source Intelligence)
- Job postings (tech stacks, software in use)

---

### ⚙️ 2.2 Active Footprinting

Active footprinting involves **direct interaction** with the target to extract information, making it more **accurate but potentially detectable**.

#### 🔧 Techniques:
- Port Scanning (e.g., with Nmap)
- Network Mapping (using traceroute or pathping)
- Banner Grabbing (identifying services and versions)
- DNS Queries (e.g., zone transfer)

#### 🛠️ Tools:
- **Nmap** – Open port detection and service versioning
- **Traceroute / Tracert** – Network path discovery
- **NSLookup / Dig** – DNS records
- **Netcat** – Banner grabbing and service fingerprinting

#### 🛑 Legal Consideration:
Active methods may trigger IDS or firewall alerts and must only be used with **explicit written permission**.

---

## 🧾 3. Passive vs Active Footprinting: Comparison Table

| Feature                | Passive Footprinting                     | Active Footprinting                         |
|------------------------|------------------------------------------|---------------------------------------------|
| Interaction with Target| No direct interaction                    | Direct interaction with target              |
| Detection Risk         | Very low / undetectable                  | High – may be flagged by security systems   |
| Data Accuracy          | Limited / surface-level                  | High – detailed information                 |
| Legality               | Generally safe (uses public info)        | Must be authorized and scoped               |
| Examples               | Google search, WHOIS, social media       | Nmap scanning, banner grabbing              |

---

## 🧠 4. Real-World Scenarios

### 🏢 Corporate Footprinting
- Gathering employee emails for spear-phishing
- Identifying exposed services on subdomains

### 🎓 Academic Use
- Understanding how much public info is exposed by universities
- Analyzing IT infrastructure as a case study

---

## 🧰 5. Tools Summary

| Tool        | Purpose                                | Type     |
|-------------|----------------------------------------|----------|
| Google Dorking | Search sensitive data on web         | Passive  |
| Whois Lookup | Domain/IP ownership and DNS info      | Passive  |
| Netcraft     | Site tech stack and host details      | Passive  |
| Maltego      | Entity mapping from public sources    | Passive  |
| Nmap         | Port and service scanning             | Active   |
| Netcat       | Service banner grabbing               | Active   |
| Traceroute   | Discover network routing              | Active   |
| NSLookup/Dig | DNS zone info                         | Active   |

---

## ✅ 6. Best Practices in Footprinting

- **Always define the scope** of engagement clearly with the client.
- **Avoid overstepping** into unauthorized access during passive discovery.
- Document all findings with **timestamps, sources, and tool versions**.
- Verify gathered information using multiple sources.

---

> 📘 *Mastering passive and active footprinting enables ethical hackers to anticipate attacker behavior and improve organizational defenses early in the cyber kill chain.*

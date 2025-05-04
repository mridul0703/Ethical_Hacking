# 902. Firewall Architectures

Firewall architectures are essential in network security as they manage and filter incoming and outgoing traffic between different network segments. The goal is to prevent unauthorized access while permitting legitimate communications. Two key components in firewall architecture are **Bastion Hosts** and **Demilitarized Zones (DMZ)**.

> 📌 *Firewall architectures protect critical assets by acting as barriers between secure and untrusted networks.*

---

## 🛡️ Firewall Architecture Overview

Firewalls are typically deployed at the **perimeter** of an organization's network. They control the flow of data between:

- **Internal Network**: Trusted network with authorized users and systems.
- **External Network**: Untrusted environment like the internet.
  
Firewalls may be implemented using **hardware appliances**, **software**, or **cloud-based solutions**.

### 🧭 Core Functions of a Firewall:
- **Packet Filtering**: Examine network packets and allow or deny traffic based on predefined rules.
- **Stateful Inspection**: Keep track of active connections and make decisions based on state and context.
- **Proxying and Network Address Translation (NAT)**: Mask internal IP addresses from external sources.

---

## 🏰 1. Bastion Hosts

A **Bastion Host** is a **special-purpose computer** designed and configured to withstand attacks. It typically sits at the **network perimeter**, serving as the gateway between trusted and untrusted networks.

### 🎯 Purpose of Bastion Hosts:
- Protect sensitive information within a network.
- Allow controlled access to internal resources from external networks.
- Act as a **"hardened" entry point** for both legitimate and hostile traffic.

### 🔒 Key Features:
- **Hardened Security**: Configured to resist attacks, with minimal services running.
- **Direct Access**: Often used to provide access to services such as **FTP**, **SSH**, or **VPN**.
- **Monitored**: Frequently monitored and updated for security vulnerabilities.

### 🧰 Examples:
- **SSH Gateway**: A Bastion Host that allows users to SSH into the internal network via a secure tunnel.
- **Proxy Server**: A Bastion Host can act as a proxy to handle web traffic, filtering and logging requests before forwarding them to the internal network.

---

## 🏰 2. Demilitarized Zone (DMZ)

The **DMZ** (Demilitarized Zone) is a **physical or logical subnetwork** that separates the internal network from untrusted external networks, such as the internet.

### 🎯 Purpose of a DMZ:
- Provide an additional layer of security between the internal network and external threats.
- Allow **public-facing services** to be placed in the DMZ, keeping them isolated from the internal network.
- Facilitate **controlled communication** with external entities (e.g., email servers, web servers) without exposing the entire internal network.

### 🌐 Typical Components in a DMZ:
- **Web Servers**: Publicly accessible websites or web applications.
- **Mail Servers**: Handling external and internal emails.
- **DNS Servers**: Resolving domain names for public services.

### 🔒 Firewall Setup in a DMZ:
- **Two-Firewall Architecture**: The DMZ is protected by **two firewalls** — one firewall between the DMZ and the external network, and another between the DMZ and the internal network.
- **One-Firewall Architecture**: A single firewall with three network interfaces (external, DMZ, internal).

#### 📌 Benefits of DMZ:
- Reduces the attack surface of the internal network.
- Ensures **public services** are accessible while **internal resources** remain protected.
- Provides a layer of security to defend against attacks targeting publicly available services.

---

## 🔥 Types of DMZ Configurations

### 🔐 **Single Firewall DMZ**
- A **single firewall** has **three interfaces**: one for the external network, one for the internal network, and one for the DMZ.
- **Pros**: Simple setup, lower cost.
- **Cons**: Less secure than a two-firewall DMZ, as a breach in the DMZ can potentially affect the internal network.

### 🔐 **Dual Firewall DMZ**
- Two firewalls are used: one firewall between the DMZ and the external network, and another between the DMZ and the internal network.
- **Pros**: Higher security due to separation of the DMZ from both external and internal networks.
- **Cons**: More complex setup, higher cost.

---

## 🛡️ 3. Best Practices for Firewall Architecture

- **Harden Bastion Hosts**: Limit the number of services running and apply regular security patches.
- **Minimize DMZ Exposure**: Only place essential, public-facing servers in the DMZ.
- **Monitoring and Logging**: Continuously monitor the Bastion Hosts and DMZ for unusual activity or signs of intrusion.
- **Segmentation**: Ensure proper network segmentation between the internal network, DMZ, and external networks to minimize the impact of a potential attack.

---

> 📘 *Bastion Hosts and DMZs are critical elements of a robust network security architecture, designed to limit exposure while ensuring controlled access to critical systems.*

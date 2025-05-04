
# 603 Detection and Prevention

Understanding how to detect and prevent SQL injection and other input-based attacks is crucial for maintaining secure web applications. This section covers three main protective mechanisms: **Prepared Statements**, **Input Validation**, and **Web Application Firewalls (WAFs)**.

---

## 🧱 1. Prepared Statements (Parameterized Queries)

Prepared statements are a secure way to interact with databases. They separate SQL code from data, which prevents attackers from injecting malicious SQL.

### ✅ Benefits:
- Automatically escape user inputs
- Ensure SQL logic cannot be altered by input
- Works with many programming languages (Java, PHP, Python, etc.)

### 🧪 Example (PHP with MySQLi):
```php
$stmt = $conn->prepare("SELECT * FROM users WHERE username = ?");
$stmt->bind_param("s", $username);
$stmt->execute();
```

### 🧪 Example (Python with SQLite):
```python
cursor.execute("SELECT * FROM users WHERE username = ?", (username,))
```

> 🔐 **Best Practice:** Always use parameterized queries instead of string concatenation.

---

## 🛡️ 2. Input Validation

Input validation ensures that incoming data matches expected formats, lengths, or types before being processed.

### ✳️ Types:
- **Whitelist Validation** – Only allow specific characters or patterns.
- **Blacklist Validation** – Block known malicious characters (less secure).
- **Type Checking** – Ensure numeric, email, URL, etc., format is respected.

### ✅ Best Practices:
- Use **regular expressions** to validate input.
- Avoid directly trusting client-side validation.
- Apply validation both on **client and server side**.

### 🧪 Example (Regex for Email in JavaScript):
```javascript
const emailRegex = /^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/;
```

> ⚠️ Note: Validation is a complementary control and should not replace prepared statements.

---

## 🌐 3. Web Application Firewall (WAF)

A WAF is a filtering system that monitors, filters, and blocks HTTP traffic to and from a web application.

### 🛡️ Key Functions:
- Detect and block **SQL injection**, **XSS**, and **CSRF** attacks.
- Apply **rulesets** (e.g., OWASP CRS) to detect anomalies.
- Log suspicious activity and generate alerts.

### 🧰 Examples of WAF Solutions:
- **Cloud-based**: Cloudflare WAF, AWS WAF, Imperva
- **Open-source**: ModSecurity (with Apache/Nginx)

> 🔐 **Deployment Tip**: Place the WAF between the user and the web server.

---

## ✅ Summary Table

| Technique            | Strength                          | Usage Level      |
|----------------------|-----------------------------------|------------------|
| Prepared Statements  | Prevents SQL injection completely | Application Code |
| Input Validation     | Stops malformed or harmful input  | Application Code |
| Web App Firewall     | Detects & blocks known patterns   | Network Layer    |

---

> 📘 *Combining secure coding practices (prepared statements), proper validation, and WAFs offers a layered defense against injection attacks and data breaches.*

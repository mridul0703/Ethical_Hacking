
# 601. Basics of SQL Injection (SQLi)

SQL Injection (SQLi) is a type of cyber attack that allows attackers to interfere with the queries that an application makes to its database. It is one of the most dangerous and widely exploited vulnerabilities in web applications.

> 🛑 *“SQLi can compromise the entire database — including usernames, passwords, and sensitive business data.”*

---

## 🧠 What is SQL Injection?

SQL Injection occurs when an attacker **inserts or "injects" malicious SQL statements** into an entry field for execution (e.g., to dump the database contents to the attacker).

### 🔧 Example of Vulnerable Code:
```sql
SELECT * FROM users WHERE username = 'admin' AND password = '1234';
```

If the input is:
```sql
' OR '1'='1
```

Then the query becomes:
```sql
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '';
```

This condition is always **true**, allowing the attacker to **bypass authentication**.

---

## ⚙️ Types of SQL Injection

### 1. Classic (In-band) SQL Injection

This is the **simplest and most common** type, where the attacker uses the same communication channel to both launch the attack and gather the results.

#### 💣 Techniques:
- Tautology-based (e.g., `' OR '1'='1`)
- Piggy-backed queries (multiple SQL commands)

#### 🔧 Example:
```sql
SELECT * FROM products WHERE id = 1; DROP TABLE users;
```

---

### 2. Blind SQL Injection

Occurs when the application is vulnerable to SQLi but does **not show output**, making it harder to exploit.

#### 🧪 Two types:
- **Boolean-based**: Alters query logic and observes response changes.
- **Time-based**: Injects time delays and measures response time.

#### ⏱️ Example (Time-based):
```sql
' OR IF(1=1, SLEEP(5), 0) -- 
```

---

### 3. Error-Based SQL Injection

This technique relies on **database error messages** to gather information about the structure of the database.

#### 🔍 Example:
```sql
' AND 1=CONVERT(int, (SELECT @@version)) -- 
```

> ⚠️ Useful when error messages are not suppressed by the application.

---

### 4. Union-Based SQL Injection

Uses the SQL `UNION` operator to combine the results of two or more SELECT statements into a single response — allowing attackers to **extract data from other tables**.

#### 🧾 Example:
```sql
' UNION SELECT username, password FROM users -- 
```

This merges attacker’s query with legitimate results.

---

## 🔒 Prevention Techniques

- Use **parameterized queries** (e.g., with prepared statements)
- Employ **stored procedures** carefully
- Implement **input validation** and sanitization
- Use **ORM frameworks** that abstract SQL logic
- Configure **web application firewalls (WAF)**

---

## 📘 Summary

| Type         | Description                              | Detectability | Risk |
|--------------|------------------------------------------|---------------|------|
| Classic      | Uses same channel for attack + result    | High          | High |
| Blind        | No visible output, relies on behavior    | Low           | High |
| Error-Based  | Exploits error messages for extraction   | Medium        | Medium |
| Union-Based  | Combines data sets to exfiltrate data    | High          | High |

---

> ✅ *Understanding SQLi is critical to securing web applications and databases against unauthorized access and data theft.*

# 🎣 Phishing Attack Detection & Investigation using Splunk

A simulated SOC investigation project that demonstrates how phishing attacks can be detected, analyzed, and correlated using Splunk SIEM.

---

# 📌 Overview

This project simulates a real-world phishing attack investigation workflow inside a Security Operations Center (SOC).

The simulation demonstrates how attackers may:

- Send phishing emails
- Trick users into clicking malicious links
- Gain unauthorized account access
- Enable mailbox forwarding for persistence

Using Splunk, the project identifies suspicious activity and correlates attack events across multiple users.

---

# ⚠️ Attack Scenario

The simulated attack flow:

1. User receives phishing email
2. User clicks malicious login link
3. Attacker gains account access
4. Suspicious login occurs from foreign location
5. Mailbox forwarding is enabled for persistence

This follows common phishing attack behavior seen in real-world environments.

---

# 🧰 Tools Used

- Splunk Enterprise
- SPL (Search Processing Language)
- Simulated phishing log dataset
- SOC investigation workflow

---

# 🧪 Detection Queries Used

## 🔗 Detect Phishing Link Clicks

```spl
index=main ACTION=LINK_CLICKED
```

## 🌍 Detect Suspicious Logins

```spl
index=main ACTION=LOGIN_SUCCESS
```

## 📬 Detect Mailbox Forwarding Persistence

```spl
index=main ACTION=MAILBOX_FORWARDING_ENABLED
```

## 🧠 Correlation Search

```spl
index=main
(ACTION=LINK_CLICKED OR ACTION=LOGIN_SUCCESS OR ACTION=MAILBOX_FORWARDING_ENABLED)
| table _time USER ACTION IP LOCATION URL
```

---

# 📸 Investigation Screenshots

## 🔗 Phishing Link Click Detection

<img width="1932" height="1145" alt="image" src="https://github.com/user-attachments/assets/e9f690ea-90a0-4057-88a9-371ae57a3b57" />

---

## 🌍 Suspicious Login Detection

<img width="2048" height="888" alt="image" src="https://github.com/user-attachments/assets/6ccd1b4b-c895-41a2-8363-e50504e9f2bf" />

---

## 📬 Mailbox Forwarding Detection

<img width="2048" height="806" alt="image" src="https://github.com/user-attachments/assets/aa7471c0-5fee-4e2d-8e49-18ba2ef77c67" />

---

## 🧠 Correlated Investigation View

<img width="2048" height="681" alt="image" src="https://github.com/user-attachments/assets/dbb3ee61-f036-4e7e-9c7b-e8ba83f50c2e" />

---

# 🧾 Sample Log Events

```text
2026-05-10 09:01:22 USER=dipan ACTION=EMAIL_RECEIVED SUBJECT="Urgent Password Reset"

2026-05-10 09:02:10 USER=dipan ACTION=LINK_CLICKED URL="http://fake-microsoft-login.com"

2026-05-10 09:04:15 USER=dipan ACTION=LOGIN_SUCCESS IP=185.22.44.10 LOCATION=Russia

2026-05-10 09:06:55 USER=dipan ACTION=MAILBOX_FORWARDING_ENABLED
```

---

# 🚨 Indicators of Compromise (IOCs)

- Suspicious phishing URLs
- Foreign login locations
- Mailbox forwarding enabled
- Multiple compromised users
- Unusual login behavior

---

# 🧯 SOC Response Actions

If this were a real-world environment, the SOC team would:

- Disable compromised accounts
- Reset affected passwords
- Remove mailbox forwarding rules
- Block malicious IP addresses
- Investigate affected users
- Monitor for additional suspicious activity

---

# 🧠 Skills Demonstrated

- SOC investigation workflow
- SIEM log analysis
- Splunk SPL queries
- Event correlation
- Phishing attack detection
- Threat hunting mindset
- Incident response analysis

  ---

# 📚 MITRE ATT&CK Mapping

| Technique | Description |
|---|---|
| T1566 | Phishing |
| T1078 | Valid Accounts |
| T1114 | Email Collection |
| T1098 | Account Manipulation |

---

# 🌍 Real-World Relevance

This project reflects how SOC analysts investigate phishing attacks in enterprise environments using SIEM tools like Splunk.

It demonstrates the transition from:

👉 Raw logs → Detection → Correlation → Investigation → Response

---

# 👨‍💻 Author

## Dipan Khatri

Cybersecurity Enthusiast | Aspiring SOC Analyst

GitHub: https://github.com/Dipan-Khatri

LinkedIn: https://www.linkedin.com/in/dipan-khatri/

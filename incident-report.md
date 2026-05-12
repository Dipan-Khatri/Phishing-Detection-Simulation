
# 🚨 Incident Report – Phishing Attack Investigation

---

# 📅 Incident Summary

- **Incident Type:** Phishing Attack
- **Severity:** High
- **Detection Platform:** Splunk Enterprise
- **Date Detected:** May 10, 2026
- **Affected Users:** dipan

---

# 🔍 Executive Summary

A simulated phishing attack was identified through suspicious email activity and unauthorized login behavior detected in Splunk logs.

The investigation revealed that a user received a phishing email, clicked a malicious login link, experienced multiple failed login attempts, and later had a successful login from a suspicious foreign IP address.

The attacker also enabled mailbox forwarding persistence, which is commonly used to maintain unauthorized access and monitor victim communications.

---

# ⚠️ Indicators of Compromise (IOCs)

| Indicator | Value |
|---|---|
| Suspicious URL | fake-microsoft-login.com |
| Suspicious IP | 185.22.44.10 |
| Login Location | Russia |
| Malicious Activity | Mailbox forwarding enabled |

---

# 🧾 Timeline of Events

| Time | Event |
|---|---|
| 09:01:22 | User received phishing email |
| 09:02:10 | User clicked suspicious login link |
| 09:03:45 | Failed login detected |
| 09:04:01 | Additional failed login attempt |
| 09:04:15 | Successful login from Russia |
| 09:05:10 | Password changed |
| 09:06:55 | Mailbox forwarding enabled |

---

# 🧪 Investigation Steps

1. Reviewed phishing-related events in Splunk
2. Identified malicious link click activity
3. Investigated failed authentication attempts
4. Confirmed successful login from suspicious location
5. Detected mailbox forwarding persistence activity
6. Correlated attack events into a single incident timeline

---

# 🧠 Detection Queries Used

## Detect Link Click Activity

```spl
index=main ACTION=LINK_CLICKED
```

## Detect Successful Logins

```spl
index=main ACTION=LOGIN_SUCCESS
```

## Detect Mailbox Forwarding Persistence

```spl
index=main ACTION=MAILBOX_FORWARDING_ENABLED
```

## Correlation Search

```spl
index=main
(ACTION=LINK_CLICKED OR ACTION=LOGIN_SUCCESS OR ACTION=MAILBOX_FORWARDING_ENABLED)
| table _time USER ACTION IP LOCATION URL
```

---

# 📸 Evidence

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

# 🧯 Recommended Response Actions

If this were a real SOC environment, the following actions would be recommended:

- Disable affected user account
- Reset compromised credentials
- Remove mailbox forwarding rules
- Block suspicious IP addresses
- Investigate additional affected users
- Monitor for persistence activity
- Educate users about phishing awareness

---

# 🧠 Analyst Assessment

The sequence of events strongly indicates a successful phishing attack leading to account compromise.

The attacker demonstrated:

- Credential harvesting behavior
- Unauthorized access attempts
- Successful authentication
- Persistence establishment through mailbox forwarding

This activity matches common phishing attack techniques observed in enterprise environments.

---

# 🎯 Conclusion

The investigation successfully identified and correlated phishing-related events using Splunk SIEM.

This project demonstrates how SOC analysts detect, investigate, and respond to phishing attacks using log analysis, event correlation, and threat investigation workflows.

---

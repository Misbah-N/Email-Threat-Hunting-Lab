# Phishing

## 📌 Overview

Phishing is a social engineering attack in which an attacker attempts to trick a victim into revealing sensitive information or executing malicious content by impersonating a trusted source.

It remains one of the most common initial access techniques used by cybercriminals and Advanced Persistent Threat (APT) groups.

---

## 🎯 Objectives of a Phishing Attack

Attackers typically aim to:

- Steal user credentials
- Deliver malware
- Gain initial access
- Bypass security controls
- Conduct Business Email Compromise (BEC)
- Steal sensitive information

---

## 🛠️ Common Phishing Techniques

- Credential Harvesting
- Business Email Compromise (BEC)
- QR Phishing (Quishing)
- Spear Phishing
- Clone Phishing
- Attachment-based Phishing
- Link-based Phishing

---

## 🚩 Common Indicators

- Suspicious sender address
- Domain impersonation
- Unexpected attachments
- URL shorteners
- Urgent language
- Password reset requests
- MFA verification requests
- Fake invoices
- Gift card scams

---

## 🔍 Investigation Checklist

When investigating a phishing email, verify:

- Sender domain
- Reply-To address
- Email headers
- Authentication results (SPF, DKIM, DMARC)
- Embedded URLs
- Attachments
- Indicators of Compromise (IOCs)
- Similar emails delivered to other users

---

## 🛡️ MITRE ATT&CK

| Technique | ID |
|-----------|------|
| Phishing | T1566 |
| Spearphishing Attachment | T1566.001 |
| Spearphishing Link | T1566.002 |
| Spearphishing via Service | T1566.003 |

---

## 📚 References

- Microsoft Learn
- Microsoft Security Blog
- MITRE ATT&CK
- CISA
- OWASP

---

> This document is part of my Email Threat Hunting learning repository.

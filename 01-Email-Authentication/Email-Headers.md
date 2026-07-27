# Email Headers

## Overview

Email headers contain metadata that records how an email traveled from the sender to the recipient. They provide critical information for identifying spoofing, phishing, Business Email Compromise (BEC), and other email-based attacks.

For a Security Analyst, email headers are one of the most valuable sources of evidence during an investigation.

---

## Why It Matters

While the email body tells you **what the sender wants you to see**, the headers tell you **what actually happened**.

A thorough header analysis can help identify:

- Spoofed senders
- Sending infrastructure
- Authentication results
- Email routing
- Suspicious Reply-To addresses
- Indicators of compromise

---

## Common Email Headers

| Header | Purpose |
|---------|----------|
| From | Visible sender shown to the recipient |
| Return-Path | Envelope sender used during SMTP |
| Reply-To | Address that receives replies |
| Received | Shows the route the email took |
| Message-ID | Unique identifier for the email |
| Authentication-Results | SPF, DKIM and DMARC results |
| DKIM-Signature | Digital signature used for DKIM |
| Received-SPF | SPF validation result |

---

## Microsoft Defender Perspective

Microsoft Defender for Office 365 exposes many of these header fields during email investigations.

The most useful fields include:

- Authentication Results
- Sender IP
- Return-Path
- CompAuth
- Message ID
- Network Message ID
- Recipient
- Delivery Action

These fields help determine whether the email is legitimate, spoofed, or part of a phishing campaign.

---

## My Investigation Workflow

When investigating a suspicious email, I typically review:

1. From address
2. Reply-To address
3. Return-Path
4. Authentication Results (SPF, DKIM, DMARC)
5. Sender IP
6. Received headers
7. Message-ID
8. URLs and attachments
9. Similar emails in the environment

The order may change depending on the nature of the investigation, but authentication results and routing information are always among the first items reviewed.

---

## Common Pitfalls

- Trusting the visible From address.
- Ignoring the Reply-To address.
- Looking only at SPF results.
- Skipping the Received headers.
- Assuming a familiar domain guarantees legitimacy.

---

## Analyst Tips

- Always compare the From and Return-Path domains.
- Review the complete email route using the Received headers.
- Treat authentication results as one part of the investigation, not the final answer.
- Validate suspicious sender IPs using threat intelligence sources.
- Correlate email findings with other Defender telemetry whenever possible.

---

## Key Takeaways

- Email headers reveal how an email was delivered.
- Header analysis is essential for phishing investigations.
- Authentication results should always be interpreted in context.
- Never rely on a single indicator when determining legitimacy.

---

## References

- Microsoft Learn
- Microsoft Defender for Office 365 Documentation
- RFC 5322
- RFC 7208 (SPF)
- RFC 6376 (DKIM)
- RFC 7489 (DMARC)

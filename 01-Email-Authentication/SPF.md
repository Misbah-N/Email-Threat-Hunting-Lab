# Sender Policy Framework (SPF)

## Overview

Sender Policy Framework (SPF) is an email authentication mechanism that helps prevent email spoofing by verifying whether the sending mail server is authorized to send emails on behalf of a domain.

SPF uses DNS TXT records to publish a list of authorized sending servers. When an email is received, the recipient's mail server compares the sending IP address against the sender domain's SPF record and returns an authentication result.

---

## Why It Matters

Email spoofing is one of the most common techniques used in phishing and Business Email Compromise (BEC) attacks.

SPF helps reduce spoofing by allowing domain owners to specify which mail servers are permitted to send emails for their domain.

However, SPF alone does **not** prove that an email is legitimate. It should always be evaluated together with DKIM and DMARC.

---

## How SPF Works

1. A sender sends an email.
2. The receiving mail server extracts the **Return-Path (Envelope From)** domain.
3. The receiver queries DNS for the domain's SPF TXT record.
4. The sender's IP address is compared against the authorized IP addresses.
5. An SPF result is generated.

Possible results include:

- Pass
- Fail
- SoftFail
- Neutral
- None
- PermError
- TempError

---

## Microsoft Defender Perspective

During an email investigation in Microsoft Defender for Office 365, SPF results can be viewed within the email authentication details.

Key fields to review include:

- SPF Result
- Return-Path
- Sender IP
- Authentication Results
- Composite Authentication (CompAuth)

SPF should never be interpreted in isolation. Always review DKIM and DMARC results before determining email legitimacy.

---

## Investigation Workflow

When reviewing a suspicious email:

1. Verify the SPF result.
2. Review the Return-Path domain.
3. Compare the sender's IP with the expected sending infrastructure.
4. Check whether the sender uses third-party email services.
5. Review DKIM and DMARC results.
6. Continue investigating URLs, attachments, and sender reputation.

---

## Common Pitfalls

- Assuming **SPF Pass** means the email is safe.
- Ignoring the Return-Path domain.
- Forgetting that forwarding can break SPF.
- Overlooking legitimate third-party email providers.

---

## Edge Cases

### Email Forwarding

Forwarded emails often fail SPF because the forwarding server is not listed in the original sender's SPF record.

### Third-Party Email Services

Services such as marketing platforms may legitimately send emails on behalf of an organization if properly included in the SPF record.

---

## Key Takeaways

- SPF validates the sending server, not the sender's identity.
- SPF helps reduce email spoofing.
- SPF should always be evaluated together with DKIM and DMARC.
- SPF Pass does not guarantee that an email is legitimate.

---

## References

- RFC 7208 – Sender Policy Framework (SPF)
- Microsoft Learn
- Microsoft Defender for Office 365 Documentation
- CISA Email Security Guidance

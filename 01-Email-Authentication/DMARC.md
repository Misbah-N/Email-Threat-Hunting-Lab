# Domain-based Message Authentication, Reporting & Conformance (DMARC)

## Overview

Domain-based Message Authentication, Reporting & Conformance (DMARC) is an email authentication protocol that builds upon SPF and DKIM to help domain owners protect their domains from email spoofing and phishing attacks.

DMARC enables domain owners to define how receiving mail servers should handle emails that fail authentication and provides reporting mechanisms to monitor unauthorized email activity.

---

## Why It Matters

SPF and DKIM individually validate different aspects of an email but do not specify what should happen when authentication fails.

DMARC solves this by:

- Requiring domain alignment.
- Defining enforcement policies.
- Providing visibility through aggregate and forensic reports.

It is one of the most effective controls against domain spoofing.

---

## How DMARC Works

DMARC evaluates:

1. SPF authentication
2. DKIM authentication
3. Domain alignment

For DMARC to pass:

- SPF or DKIM must pass.
- The authenticated domain must align with the visible From domain.

---

## DMARC Policies

### None

- Monitor authentication results.
- Do not take enforcement action.

### Quarantine

- Treat suspicious emails as spam or junk.

### Reject

- Reject emails that fail DMARC during SMTP delivery.

---

## Microsoft Defender Perspective

During investigations in Microsoft Defender for Office 365, review:

- DMARC Result
- Authentication Results
- Composite Authentication (CompAuth)
- From Domain
- Return-Path
- DKIM Signing Domain

DMARC should always be interpreted together with SPF and DKIM.

---

## Investigation Workflow

When reviewing a suspicious email:

1. Verify the DMARC result.
2. Check SPF authentication.
3. Check DKIM authentication.
4. Confirm domain alignment.
5. Review authentication headers.
6. Continue investigating URLs, attachments, sender reputation, and message intent.

---

## Common Pitfalls

- Assuming DMARC Pass guarantees a safe email.
- Ignoring domain alignment.
- Forgetting that legitimate third-party services require proper DMARC configuration.
- Overlooking authentication details when only reviewing the final verdict.

---

## Edge Cases

### Third-Party Email Providers

Organizations often use services such as marketing platforms or ticketing systems that send emails on their behalf. These services must be properly configured to align with the organization's DMARC policy.

### Compromised Accounts

Emails sent from compromised corporate accounts usually pass SPF, DKIM, and DMARC because they originate from legitimate infrastructure.

Authentication confirms the sender's infrastructure—not the sender's intent.

---

## Key Takeaways

- DMARC combines SPF and DKIM with domain alignment.
- DMARC helps prevent domain spoofing.
- DMARC policies determine how failed authentication is handled.
- A DMARC Pass does not automatically mean an email is legitimate.

---

## References

- RFC 7489 – DMARC
- Microsoft Learn
- Microsoft Defender for Office 365 Documentation
- CISA Email Security Guidance

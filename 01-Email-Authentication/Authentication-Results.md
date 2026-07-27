# Authentication Results

## Overview

Authentication Results summarize how an email performed against the three primary email authentication mechanisms:

- Sender Policy Framework (SPF)
- DomainKeys Identified Mail (DKIM)
- Domain-based Message Authentication, Reporting & Conformance (DMARC)

These results help analysts determine whether an email originated from authorized infrastructure and whether the message integrity was preserved during transit.

Authentication results are one of the first artifacts I review during an email investigation, but they are never used as the sole indicator of legitimacy.

---

## Why It Matters

Authentication results help answer important questions such as:

- Was the sending server authorized?
- Was the message altered after it was sent?
- Does the sender align with the claimed domain?
- Is the email potentially spoofed?

Although valuable, authentication results only validate technical aspects of email delivery—they do not determine whether an email is malicious.

---

## Common Authentication Results

### SPF

- Pass
- Fail
- SoftFail
- Neutral
- None
- TempError
- PermError

### DKIM

- Pass
- Fail
- None

### DMARC

- Pass
- Fail
- Best Guess Pass (in some environments)

---

## Microsoft Defender Perspective

Microsoft Defender for Office 365 exposes authentication information within the email details.

During an investigation, I commonly review:

- SPF Result
- DKIM Result
- DMARC Result
- Composite Authentication (CompAuth)
- Authentication-Results header
- Sender IP
- Return-Path
- From Domain

These values help establish whether the sender's infrastructure is trusted before moving on to analyze URLs, attachments, and message content.

---

## Investigation Workflow

When reviewing authentication results:

1. Check SPF.
2. Check DKIM.
3. Check DMARC.
4. Verify domain alignment.
5. Review CompAuth.
6. Compare the From and Return-Path domains.
7. Continue investigating the rest of the email.

Authentication is one part of the investigation—not the final verdict.

---

## Common Scenarios

| SPF | DKIM | DMARC | Possible Interpretation |
|------|------|--------|-------------------------|
| Pass | Pass | Pass | Legitimate infrastructure, continue investigation |
| Fail | Pass | Pass | Forwarding or third-party service may be involved |
| Pass | Fail | Fail | Possible message modification or DKIM issue |
| Fail | Fail | Fail | Strong indicator of spoofing, but verify before concluding |

---

## Common Pitfalls

- Assuming all authentication passes mean the email is safe.
- Ignoring domain alignment.
- Not reviewing the Authentication-Results header.
- Focusing only on a single authentication mechanism.

---

## Key Takeaways

- Authentication validates infrastructure—not intent.
- SPF, DKIM, and DMARC should always be evaluated together.
- Authentication results are valuable indicators, not proof of legitimacy.
- Always correlate authentication with message content and other telemetry.

---

## References

- Microsoft Learn
- Microsoft Defender for Office 365 Documentation
- RFC 7208
- RFC 6376
- RFC 7489

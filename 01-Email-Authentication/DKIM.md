# DomainKeys Identified Mail (DKIM)

## Overview

DomainKeys Identified Mail (DKIM) is an email authentication standard that uses cryptographic signatures to verify that an email has not been altered during transit and that it was authorized by the sending domain.

Unlike SPF, which validates the sending server, DKIM validates the integrity of the email message.

---

## Why It Matters

Attackers frequently spoof trusted domains to deliver phishing emails. DKIM helps receiving mail servers determine whether an email was genuinely sent by the claimed domain and whether its contents have remained unchanged after being signed.

A valid DKIM signature increases confidence in the authenticity of an email, but it does not guarantee that the email is safe. A compromised legitimate account can still send malicious emails with a valid DKIM signature.

---

## How DKIM Works

1. The sending mail server generates a cryptographic hash of selected email headers and the message body.
2. The hash is encrypted using the sender's private key.
3. The encrypted hash is added to the email as a DKIM-Signature header.
4. The sender publishes the corresponding public key in DNS.
5. The receiving mail server retrieves the public key and verifies the signature.
6. If the calculated hash matches the decrypted hash, DKIM passes.

---

## Microsoft Defender Perspective

During email investigations in Microsoft Defender for Office 365, review:

- DKIM Result
- Signing Domain (`d=` value)
- Selector (`s=` value)
- Authentication Results
- Composite Authentication (CompAuth)

Always compare the signing domain with the visible sender domain to understand whether the message is properly aligned.

---

## Investigation Workflow

When analyzing a suspicious email:

1. Verify the DKIM result.
2. Review the signing domain (`d=`).
3. Compare it with the From domain.
4. Check whether DMARC alignment is satisfied.
5. Review SPF results.
6. Continue investigating message content, URLs, attachments, and sender reputation.

---

## Common Pitfalls

- Assuming a DKIM Pass means the email is trustworthy.
- Ignoring the signing domain.
- Forgetting that compromised legitimate accounts produce valid DKIM signatures.
- Looking only at DKIM without reviewing SPF and DMARC.

---

## Edge Cases

### Mailing Lists

Some mailing lists modify email content, which can invalidate DKIM signatures if the signed portions of the message are changed.

### Compromised Accounts

Emails sent from compromised Microsoft 365 or Google Workspace accounts often pass DKIM because the sender legitimately controls the private signing key.

---

## Key Takeaways

- DKIM verifies message integrity.
- DKIM does not validate sender intent.
- A valid DKIM signature does not mean an email is safe.
- Always evaluate DKIM together with SPF and DMARC.

---

## References

- RFC 6376 – DomainKeys Identified Mail
- Microsoft Learn
- Microsoft Defender for Office 365 Documentation
- CISA Email Security Guidance

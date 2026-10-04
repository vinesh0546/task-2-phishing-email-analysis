# Task 2: Phishing Email Analysis

## 1. Objective

The objective of this task is to analyze a phishing email sample
and identify indicators such as sender spoofing, header
authentication failures, suspicious URLs, urgency, and social
engineering techniques.

## 2. Sample Information

Sample file: `sample2.eml`

The sample presents itself as a Microsoft account security alert
claiming that unusual sign-in activity was detected.

Subject:

`[Action Required] Unusual sign-in activity on your account`

Sender:

`"Microsoft Account Team" <noreply@microsoftonline-verify.com>`

---

## 3. Sender Analysis

The sender claims to be the Microsoft Account Team.

However, the sender uses the domain:

`microsoftonline-verify.com`

This is suspicious because the message is presenting itself as an
official Microsoft security notification while using a
non-Microsoft domain.

The Return-Path also uses the same suspicious domain:

`noreply@microsoftonline-verify.com`

### Finding

The sender domain is a strong phishing indicator.

---

## 4. Email Header Analysis

### Return-Path

`noreply@microsoftonline-verify.com`

### Sending Server

`mail.microsoftonline-verify.com`

### Sending IP

`178.238.225.91`

The header also identifies the sending server as:

`vps-291847.contabo.net`

### SPF

`SPF: FAIL`

The header states that the sending IP was not authorized to send
email for the sender domain.

### DKIM

`DKIM: FAIL`

The DKIM authentication check failed.

### DMARC

`DMARC: FAIL`

The DMARC authentication check failed.

### Header Assessment

The failure of SPF, DKIM, and DMARC provides strong evidence that
the message should not be trusted as an authenticated message from
the claimed domain.

---

## 5. Email Content Analysis

The email claims:

> "We detected something unusual about a recent sign-in to your
> Microsoft account."

It provides details including:

- Country/region: Russia
- IP address: 91.234.99.42
- Date: February 6, 2026
- Platform: Windows 10
- Browser: Chrome 120.0

The message then tells the recipient to secure the account
immediately if the activity was not theirs.

### Finding

The message uses an unexpected-login scenario to create concern
and encourage the recipient to take immediate action.

---

## 6. Suspicious URL Analysis

The email contains a button labelled:

`Review recent activity`

The actual hyperlink in the HTML is:

`https://bit.ly/3vF9xKz`

This is a shortened URL.

The shortened URL hides the final destination from the recipient,
making it difficult to determine where the link will lead without
additional investigation.

The link was not opened during this analysis.

### Finding

The use of a shortened URL in an account-security email is a
suspicious characteristic and should be investigated before any
interaction.

---

## 7. Brand Impersonation

The email attempts to appear as an official Microsoft security
notification.

Indicators include:

- "Microsoft Account Team" sender name
- Microsoft logo
- Microsoft-style security-alert design
- Microsoft Corporation address in the footer
- Microsoft account security terminology

However, the sender domain does not match the claimed organization.

### Finding

This is consistent with brand impersonation.

---

## 8. Urgency and Social Engineering

The email uses several social-engineering techniques.

### Urgency

The subject begins with:

`[Action Required]`

The email also states:

`secure your account immediately`

and describes the message as:

`a mandatory service notification`

### Fear

The email claims that unusual sign-in activity was detected,
including a login from Russia.

This can make the recipient worry that their account has been
compromised.

### Trust

The attacker uses Microsoft's name, branding, and security
terminology to make the message appear legitimate.

### Finding

The combination of fear, urgency, and brand impersonation is a
strong social-engineering indicator.

---

## 9. Phishing Indicators Summary

| Indicator | Evidence | Assessment |
|---|---|---|
| Suspicious sender domain | microsoftonline-verify.com | High |
| Brand impersonation | Claims to be Microsoft | High |
| SPF authentication | FAIL | High |
| DKIM authentication | FAIL | High |
| DMARC authentication | FAIL | High |
| Suspicious sending infrastructure | vps-291847.contabo.net | High |
| Shortened URL | bit.ly/3vF9xKz | High |
| Urgency | [Action Required] | Medium/High |
| Fear-based message | Unusual sign-in from Russia | High |
| Social engineering | Fear + urgency + trust | High |

---

## 10. Risk Assessment

### Risk Level: HIGH

The email contains multiple independent phishing indicators,
including:

- Suspicious sender domain
- SPF failure
- DKIM failure
- DMARC failure
- Suspicious sending infrastructure
- Brand impersonation
- Shortened URL
- Urgent language
- Fear-based messaging
- Social engineering

Taken together, these indicators strongly suggest that the email
is a phishing attempt.

---

## 11. Recommended Actions

If a user receives a message like this:

1. Do not click the suspicious link.
2. Do not enter passwords or other credentials.
3. Verify the account through the organization's official website
   or another trusted channel.
4. Report the message as phishing.
5. Delete or quarantine the suspicious email.
6. If credentials were already entered, change the password through
   the legitimate service and follow the organization's incident
   response procedure.

---

## 12. Conclusion

The analyzed email demonstrates several common phishing techniques.

The attacker attempts to impersonate Microsoft and uses a
suspicious sender domain, failed email authentication checks,
a shortened URL, urgency, fear, and social engineering.

Header analysis and examination of the email content provide
multiple indicators that the message should not be trusted.

This task demonstrates the importance of checking sender
information, email headers, links, message content, and
social-engineering techniques before interacting with a
suspicious email.

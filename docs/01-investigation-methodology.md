# 01 — Investigation Methodology

## Purpose

The purpose of this investigation is to determine whether a reported email is legitimate, spam, reconnaissance, credential phishing, malware delivery, or another form of social engineering.

## Phase 1 — Initial Triage

Begin with the visible message. Review the sender, display name, subject, greeting, branding, grammar, urgency, requested action, hyperlinks, and attachments.

Do not click links or open attachments during initial triage.

Questions to answer:

- What organization is the email claiming to represent?
- What action does it want the recipient to perform?
- Is the message creating urgency, fear, curiosity, or financial pressure?
- Does the sender domain match the organization?
- Does the visible link text match the real destination?
- Is an attachment present?

## Phase 2 — Artifact Collection

Collect the following where available:

### Email artifacts

- Sender address
- Recipient
- Subject
- Date/time
- Return-Path
- Reply-To
- Originating/sending IP
- Relevant `Received` headers
- Message-ID

### Web artifacts

- Full URL, sanitized for public reporting
- Root domain
- Redirect domains if safely obtained through an analysis platform

### File artifacts

- Filename
- File extension
- File size
- MD5
- SHA1
- SHA256

## Phase 3 — Artifact Analysis

Analyze collected indicators using reputation and contextual sources.

For a domain or URL, review:

- Reputation detections
- Registration/domain age
- Whether the domain matches the impersonated brand
- Safe webpage capture results
- HTTP status if obtained through a passive/safe service

For a file, review:

- Hash reputation
- File type
- Submission history
- Sandbox results when available and authorized

## Phase 4 — Correlation

One suspicious indicator alone may not prove maliciousness. Correlate the evidence.

Example correlation:

A non-brand sender address + mismatched destination domain + phishing detections + a newly registered domain provides significantly stronger evidence than any one indicator by itself.

## Phase 5 — Verdict

Choose a clear classification such as:

- Legitimate
- Spam
- Reconnaissance
- Suspicious
- Credential phishing
- Malware delivery
- Business email compromise

State the confidence level and summarize the evidence supporting the decision.

## Phase 6 — Defensive Actions

Recommend actions proportionate to the evidence and business risk. Possible actions include sender/domain blocking, message removal, IOC searches, authentication review, credential reset, endpoint review, and user notification.

## Phase 7 — Documentation

Record the case in a structured report containing:

- Executive summary
- Scope
- Artifacts
- Analysis
- Findings
- Verdict
- Defensive recommendations
- Evidence references

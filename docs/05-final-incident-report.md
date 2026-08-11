# 05 — Final Incident Report

## Report Scope

This report documents the sanitized credential-phishing example used throughout the core investigation workflow. It is separate from the hands-on email samples and HTML credential-harvester investigation documented elsewhere in this repository.

## Incident Title

Credential-Phishing Email Investigation

## Severity

Medium — Example portfolio classification

## Status

Closed — Malicious email confirmed and recommended controls documented

## Executive Summary

A suspicious email was reviewed after it attempted to impersonate a trusted account-security service and direct the recipient to an external login page. Analysis identified multiple indicators consistent with credential phishing, including a sender/domain mismatch, a non-brand hyperlink destination, phishing reputation detections, and a login-oriented landing page. The message is classified as malicious with high confidence.

## Scope

This portfolio case covers one reported email and its associated sender and URL indicators. The example contains sanitized data and does not represent a live company incident.

## Artifacts

| Type | Value |
|---|---|
| Sender | security-alert@example-mail[.]test |
| Subject | Action Required: Verify Your Account |
| Originating IP | 192.0.2.44 |
| URL | hxxps://account-review[.]example/login |
| Root Domain | account-review[.]example |
| Attachment | None |

## Analysis

The email used urgency and account-verification language to influence the recipient. The sender infrastructure did not align with the organization being impersonated.

The destination URL used a different domain than the claimed organization. Reputation and safe-capture results were consistent with phishing activity and credential harvesting.

No attachment was present in this example, so file analysis was not required.

## Findings

The available evidence demonstrates intentional credential-phishing behavior. The malicious conclusion is based on correlated indicators rather than a single reputation result.

## Verdict

**Malicious — Credential Phishing**

**Confidence:** High

## Recommended Actions

- Block the confirmed malicious sender and URL/domain as appropriate.
- Search for additional delivered copies of the message.
- Search web/DNS/security telemetry for user interaction with the IOC.
- Remove matching messages when authorized.
- If credentials were entered, reset credentials, revoke active sessions, and review authentication activity.
- Preserve the original email and investigation evidence according to policy.

## Lessons Learned

The investigation demonstrates why analysts should correlate email content, header artifacts, web indicators, domain context, and reputation data before making a final determination.

It also demonstrates the importance of safe handling: suspicious links do not need to be opened directly, and suspicious attachments should not be executed simply to determine whether they are malicious.

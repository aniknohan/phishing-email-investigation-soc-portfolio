# 07 — MITRE ATT&CK Mapping

MITRE ATT&CK mapping should be based on behavior that is actually supported by evidence. It is not necessary to force a technique onto every artifact.

## Primary Technique

### T1566.002 — Phishing: Spearphishing Link

The email attempts to persuade the recipient to follow an external hyperlink. This is consistent with **Spearphishing Link** when the link is used as the delivery mechanism for the social-engineering attempt.

**Evidence that supports the mapping:**

- The message contains a call-to-action link.
- The visible brand/context does not match the destination domain.
- The landing page is designed to continue the phishing interaction.

## Conditional Technique

### T1056.003 — Input Capture: Web Portal Capture

This technique may be relevant **only if evidence shows that the landing page is designed to collect credentials or other authentication data through a web form**.

**Evidence that could support the mapping:**

- Safe webpage capture shows a fake login form.
- The page imitates a trusted authentication portal.
- Sandbox or web-capture evidence shows credential-entry fields or form submission behavior.

Do not map T1056.003 merely because a URL looks suspicious. The credential-capture behavior should be observed or otherwise supported.

## Analyst Note

ATT&CK is used here to describe adversary behavior, not to determine maliciousness by itself. The phishing verdict should come from the complete evidence set: message content, sender identity, headers, destination infrastructure, reputation, safe capture results, and user/telemetry context.

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


## Confirmed HTML Credential-Harvester Mapping

The separate HTML credential-harvester investigation documented in this repository provides direct behavioral evidence supporting additional ATT&CK mapping.

### T1566.001 — Phishing: Spearphishing Attachment

The phishing activity used a malicious HTML attachment as the mechanism for presenting credential-harvesting content to the recipient.

Supporting evidence includes:

- The suspicious file was delivered as an HTML attachment.
- The attachment rendered a fake Microsoft / Office 365 login interface.
- The attachment was analyzed separately through static and controlled behavioral analysis.

### T1056.003 — Input Capture: Web Portal Capture

Controlled analysis of the HTML attachment confirmed credential-collection behavior. Test credentials entered into the fake login interface were included in an outbound HTTP request to external infrastructure.

Supporting evidence includes:

- A fake Microsoft / Office 365 login interface was presented.
- Credential-entry fields were available to the user.
- Controlled submission generated an outbound request containing the submitted test values.
- The credential-collection domain and endpoint were identified during network analysis.

This mapping is based on observed behavior from the controlled lab analysis rather than inference from the appearance of the phishing page alone.

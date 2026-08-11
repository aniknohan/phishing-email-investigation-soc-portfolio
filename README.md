
# Phishing Email Investigation — SOC Analyst Portfolio

A hands-on SOC phishing investigation portfolio demonstrating email triage, raw `.eml` and header analysis, manual artifact collection, sender-infrastructure investigation, URL and domain analysis, attachment hashing, HTML credential-harvester analysis, IOC extraction, MITRE ATT&CK mapping, and incident-response planning.

The repository documents multiple phishing-analysis scenarios and shows how evidence can be collected, correlated, and converted into defensible analyst findings. The project progresses from initial email review through deeper artifact analysis, malicious-behavior confirmation, incident scoping, containment recommendations, remediation, and post-incident monitoring.

> **Portfolio safety:** The example indicators in this repository are sanitized and non-live. Do not publish real company emails, credentials, internal IP addresses, customer information, authentication tokens, or active malicious files/URLs.

## Scenario

This project simulates the investigation of suspicious emails reported to a Security Operations Center (SOC). The analyst is responsible for determining whether the messages are benign, suspicious, or malicious by examining the available email and related artifacts.

The investigation begins with manual analysis of raw `.eml` files to collect key evidence such as sender and recipient addresses, subject lines, timestamps, sending IP addresses, reverse DNS information, URLs, domains, attachment filenames, and cryptographic hashes.

The project then progresses into deeper analysis of suspicious content. This includes examining an HTML attachment that impersonates a Microsoft / Office 365 login page, reviewing its source code, and observing its network behavior in a controlled lab environment. The analysis demonstrates credential-harvesting behavior and identifies associated indicators of compromise.

Finally, the collected evidence is used to document incident classification, IOC-based scoping, containment recommendations, remediation, recovery, post-incident monitoring, and lessons learned.

The goal is to demonstrate an evidence-driven SOC investigation workflow while clearly distinguishing between actions performed in the lab and response actions that would be recommended in a production environment.


## Tools & Technologies

The investigation used a combination of email-analysis, operating-system, browser, and threat-analysis tools to collect and examine phishing artifacts.

- **Sublime Text** — Reviewed raw `.eml` files, email headers, URLs, attachment metadata, and HTML source code.
- **Mozilla Thunderbird** — Opened email samples and reviewed message content and attachment information.
- **Windows PowerShell** — Calculated cryptographic file hashes using `Get-FileHash`.
- **DomainTools** — Investigated sending IP addresses and reviewed reverse DNS / hostname information.
- **CyberChef** — Decoded and transformed encoded URL and web artifacts during analysis.
- **Google Chrome Developer Tools** — Inspected HTML credential-harvester network activity and captured the credential-submission request.
- **Windows File Properties** — Reviewed attachment file type, extension, and file-size metadata.
- **MITRE ATT&CK** — Mapped observed phishing behavior to relevant adversary tactics and techniques.
- **GitHub** — Documented investigation methodology, evidence, findings, IOCs, and incident-response recommendations.

## Objectives

- Triage the message without directly interacting with suspicious content.
- Extract sender, header, URL/domain, IP, and file artifacts.
- Review sender identity and mail-routing evidence.
- Investigate URLs/domains with passive reputation and safe-capture services.
- Calculate file hashes without executing an attachment.
- Correlate multiple indicators before reaching a verdict.
- Document findings with evidence and analyst reasoning.
- Recommend containment, scoping, recovery, and prevention actions.
- Map relevant observed behavior to MITRE ATT&CK.

## Investigation Workflow

The project follows a structured SOC investigation workflow that moves from initial email triage to deeper technical analysis and incident-response planning.

1. **Email Triage** — Review the suspicious message and determine what artifacts require further investigation.
2. **Header Analysis** — Examine raw `.eml` content to identify sender and recipient addresses, subject lines, timestamps, sending IP addresses, and other message metadata.
3. **Infrastructure Analysis** — Investigate sending IP addresses, reverse DNS information, domains, and related infrastructure.
4. **URL Analysis** — Extract suspicious URLs safely, identify root domains, and preserve relevant indicators for further investigation.
5. **Attachment Analysis** — Identify attachment filenames, extensions, file sizes, and cryptographic hashes while avoiding unsafe execution.
6. **HTML Source Analysis** — Review suspicious HTML attachments for forms, embedded resources, redirects, scripts, and credential-collection behavior.
7. **Behavioral Analysis** — Use browser Developer Tools in a controlled lab environment to observe network requests generated by the suspicious HTML content.
8. **IOC Extraction** — Record relevant filenames, hashes, domains, URLs, endpoints, email addresses, and infrastructure indicators.
9. **Incident Assessment** — Correlate the collected evidence to classify the activity and determine whether malicious behavior has been confirmed.
10. **Response Planning** — Document recommended scoping, containment, eradication, recovery, monitoring, and security-improvement actions.

This workflow emphasizes evidence-based analysis. Findings are based on artifacts observed during the lab, while production containment and remediation activities are documented separately as recommended SOC actions.

## Repository Structure

```text
phishing-email-investigation-soc-portfolio/
│
├── README.md
├── LICENSE
│
├── data/
│   ├── artifact-worksheet.md
│   └── iocs.csv
│
├── docs/
│   ├── 01-investigation-methodology.md
│   ├── 02-artifact-collection.md
│   ├── 03-analysis-and-findings.md
│   ├── 04-defensive-actions.md
│   ├── 05-final-incident-report.md
│   ├── 06-email-analysis-demo.md
│   ├── 07-mitre-attack-mapping.md
│   ├── 08-html-credential-harvester-analysis.md
│   ├── 09-incident-response-and-remediation.md
│   └── screenshot-guide.md
│
└── evidence/
    ├── email-samples/
    └── screenshots/
        ├── manual-artifact-collection/
        └── html-credential-harvester/
```

## Project Documentation

The investigation is documented across the following sections:

1. [Investigation Methodology](docs/01-investigation-methodology.md) — Investigation approach, evidence handling, and analysis methodology.
2. [Artifact Collection](docs/02-artifact-collection.md) — Manual extraction of email headers, sender infrastructure, URLs, domains, attachments, and file hashes.
3. [Analysis and Findings](docs/03-analysis-and-findings.md) — Correlation of collected artifacts and documentation of analyst findings.
4. [Defensive Actions](docs/04-defensive-actions.md) — Recommended defensive actions based on the investigation findings.
5. [Final Incident Report](docs/05-final-incident-report.md) — Consolidated incident findings and final assessment.
6. [Email Analysis Demo](docs/06-email-analysis-demo.md) — Practical walkthrough of phishing email analysis.
7. [MITRE ATT&CK Mapping](docs/07-mitre-attack-mapping.md) — Mapping of observed phishing behavior to relevant MITRE ATT&CK techniques.
8. [HTML Credential Harvester Analysis](docs/08-html-credential-harvester-analysis.md) — Static and behavioral analysis of an HTML attachment designed to harvest credentials.
9. [Incident Response and Remediation](docs/09-incident-response-and-remediation.md) — Incident classification, scoping, containment, remediation, recovery, monitoring, and lessons learned.

### Featured Investigation

For the most technical hands-on analysis, see:

**[HTML Credential Harvester Analysis →](docs/08-html-credential-harvester-analysis.md)**

This investigation demonstrates HTML attachment identification, SHA256 hashing, metadata review, source-code analysis, URL decoding, browser Developer Tools analysis, credential-submission observation, and IOC extraction.

For the response workflow that follows the technical investigation, see:

**[Incident Response and Remediation →](docs/09-incident-response-and-remediation.md)**


## Example Case Verdict

**Classification:** Malicious — Credential Phishing / Credential Harvester

**Severity:** High

**Confidence:** High

**Disposition:** Confirmed Malicious

The final assessment is based on correlation of multiple artifacts rather than a single indicator. The investigation identified phishing characteristics across email metadata, sender infrastructure, URLs, attachments, and web content.

The strongest technical evidence came from analysis of the HTML attachment. The attachment presented a fraudulent Microsoft / Office 365 login interface, and controlled behavioral analysis showed that information entered into the form was transmitted through an HTTP request to external infrastructure.

Additional analysis identified and documented relevant indicators, including the attachment filename, SHA256 hash, credential-collection domain, endpoint, and defanged request URL.

Together, the static and behavioral evidence supports a **high-confidence malicious verdict** and demonstrates credential-harvesting functionality.

**Production compromise:** Not established by the available lab evidence. The analysis confirms malicious functionality but does not establish that real production credentials were submitted or successfully used by an attacker.

## Defensive Response Summary

Following confirmation of the phishing activity, the investigation findings can be used to guide incident-response actions in a production SOC environment.

Recommended response actions include:

- Search the email environment for additional messages containing matching senders, subjects, URLs, domains, attachment filenames, or hashes.
- Remove confirmed malicious messages from affected mailboxes.
- Block confirmed malicious domains, URLs, and other infrastructure using the most appropriate security controls.
- Search network and endpoint telemetry for communication with identified malicious infrastructure.
- Identify users who opened the attachment, visited the phishing page, or potentially submitted credentials.
- Reset passwords and revoke active sessions when credential compromise is suspected or confirmed.
- Review affected accounts for suspicious authentication activity, MFA changes, mailbox rules, forwarding rules, or other unauthorized modifications.
- Quarantine or remove identified malicious attachments where appropriate.
- Continue monitoring affected users and systems for related suspicious activity.
- Retain confirmed indicators for future detection, correlation, and threat hunting.

These actions represent **recommended production response procedures**. The lab demonstrates phishing investigation and malicious-artifact analysis but does not provide access to production email gateways, identity platforms, endpoint-security systems, or network controls required to perform these actions directly.

For the complete response workflow, see **[Incident Response and Remediation →](docs/09-incident-response-and-remediation.md)**.


## Evidence and Screenshots

Investigation evidence is organized by analysis type so that the documented findings can be traced back to supporting screenshots and artifacts.

### Manual Email Artifact Collection

Evidence from the manual `.eml` investigation includes:

- Sender and recipient addresses
- Subject lines and timestamps
- Sending-server IP addresses
- Reverse DNS / hostname information
- Extracted URLs and root domains
- Attachment filenames
- MD5 and SHA256 hashes

**[View Manual Artifact Collection Evidence →](evidence/screenshots/manual-artifact-collection/)**

### HTML Credential Harvester Analysis

Evidence from the HTML attachment investigation includes:

- HTML attachment identification
- SHA256 hash collection
- File-size and metadata review
- HTML source-code analysis
- Embedded resource inspection
- URL decoding
- Browser Developer Tools network analysis
- Credential-submission request analysis
- Credential-collection domain and endpoint identification

**[View HTML Credential Harvester Evidence →](evidence/screenshots/html-credential-harvester/)**

### Evidence Handling

Potentially malicious URLs are defanged in the written documentation where appropriate. Screenshots are used to demonstrate the investigation process without publishing active malicious content for execution.

The evidence in this repository is intended to support the documented analyst findings and demonstrate the investigative process performed within the lab environment.

## Project Documents

- [Investigation Methodology](docs/01-investigation-methodology.md)
- [Artifact Collection](docs/02-artifact-collection.md)
- [Analysis and Findings](docs/03-analysis-and-findings.md)
- [Defensive Actions](docs/04-defensive-actions.md)
- [Final Incident Report](docs/05-final-incident-report.md)
- [Hands-On Email Analysis Demo](docs/06-email-analysis-demo.md)
- [MITRE ATT&CK Mapping](docs/07-mitre-attack-mapping.md)
- [Screenshot Guide](docs/screenshot-guide.md)
- [Artifact Worksheet](data/artifact-worksheet.md)
- [IOC Register](data/iocs.csv)

## Skills Demonstrated

Phishing triage, raw email/header analysis, IOC extraction, URL/domain investigation, file hashing, threat-intelligence correlation, safe evidence handling, MITRE ATT&CK mapping, incident scoping, defensive recommendations, and SOC-style reporting.

## Disclaimer

This repository is for defensive cybersecurity education and portfolio demonstration only. Do not execute suspicious attachments or directly browse suspicious links from a production workstation. Follow your organization’s policies and use isolated, authorized analysis environments.

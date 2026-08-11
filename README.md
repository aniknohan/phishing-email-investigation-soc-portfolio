
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

## Tools Demonstrated

This workflow can be performed with a safe text editor such as **Visual Studio Code**, **Notepad++**, or **Sublime Text** for raw `.eml` review; **PowerShell `Get-FileHash`** for MD5/SHA1/SHA256 calculation; and approved passive or sandbox services such as **VirusTotal**, **WHOIS/RDAP**, **URL2PNG or another remote web-capture service**, **WannaBrowser**, **Hybrid Analysis**, **URLhaus**, and **PhishTool**.

The goal is not to use every tool in every case. A SOC analyst should select the minimum set of sources needed to answer the investigation questions and should avoid unnecessary direct interaction with suspicious infrastructure.

## Example Case Verdict

**Classification:** Malicious — Credential Phishing  
**Confidence:** High

The example verdict is based on the combination of brand impersonation, urgency, sender/domain mismatch, a non-brand destination, phishing reputation evidence, and a login-oriented landing page. Each individual signal is useful, but the final assessment is based on correlation rather than a single detection.

## Defensive Response Summary

For a confirmed credential-phishing message, appropriate actions may include blocking the specific malicious sender/URL/domain where business impact is acceptable, searching the mail environment for additional recipients, removing matching messages, reviewing web/DNS/endpoint telemetry for clicks, and reviewing authentication activity when credential submission is possible. If credentials were entered, response should include credential reset, session revocation, MFA review, and follow-on compromise checks according to organizational procedure.

Do not broadly block a legitimate shared provider simply because one account, subdomain, or path was abused. Use the most specific effective control supported by the evidence.

## Evidence and Screenshots

The project is fully readable without screenshots. When screenshots are added later, store sanitized PNG images under `evidence/screenshots/` and follow [`docs/screenshot-guide.md`](docs/screenshot-guide.md). The guide provides filenames and suggested evidence for VS Code/raw headers, VirusTotal, WHOIS/RDAP, safe webpage capture, PhishTool, Hybrid Analysis, URLhaus, and file-hash output.

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

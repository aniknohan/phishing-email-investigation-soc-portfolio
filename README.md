
# Phishing Email Investigation — SOC Analyst Portfolio

A hands-on SOC phishing investigation portfolio demonstrating email triage, raw `.eml` and header analysis, manual artifact collection, sender-infrastructure investigation, URL and domain analysis, attachment hashing, HTML credential-harvester analysis, IOC extraction, MITRE ATT&CK mapping, and incident-response planning.

The repository documents multiple phishing-analysis scenarios and shows how evidence can be collected, correlated, and converted into defensible analyst findings. The project progresses from initial email review through deeper artifact analysis, malicious-behavior confirmation, incident scoping, containment recommendations, remediation, and post-incident monitoring.

> **Portfolio safety:** The example indicators in this repository are sanitized and non-live. Do not publish real company emails, credentials, internal IP addresses, customer information, authentication tokens, or active malicious files/URLs.

## Scenario

A user reports a suspicious account-security email that attempts to create urgency and directs the recipient to an external login page. The analyst must determine whether the message is legitimate or malicious, identify the relevant indicators of compromise (IOCs), assess potential user exposure, and recommend proportionate response actions.

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

```text
Report received
      ↓
Initial email triage
      ↓
Raw header / source review
      ↓
Artifact extraction
      ↓
URL / domain / IP / file analysis
      ↓
Evidence correlation
      ↓
Classification + confidence
      ↓
Containment and scope checks
      ↓
Final incident report
```

## Repository Structure

```text
.
├── README.md
├── .gitignore
├── LICENSE
├── data/
│   ├── artifact-worksheet.md
│   └── iocs.csv
├── docs/
│   ├── 01-investigation-methodology.md
│   ├── 02-artifact-collection.md
│   ├── 03-analysis-and-findings.md
│   ├── 04-defensive-actions.md
│   ├── 05-final-incident-report.md
│   ├── 06-email-analysis-demo.md
│   ├── 07-mitre-attack-mapping.md
│   └── screenshot-guide.md
└── evidence/
    ├── email-samples/
    │   └── README.md
    └── screenshots/
        └── README.md
```

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

# Screenshot Guide

Screenshots are optional for the initial upload, but adding them later will make the portfolio easier to verify visually. Save sanitized screenshots under `evidence/screenshots/`.

## Recommended Screenshots

### 01 — Email Overview

**Filename:** `01-email-overview.png`

Show the sender/display name, subject, main message body, call-to-action text, and attachment name if present. Redact real names, addresses, internal domains, and active malicious links.

### 02 — Raw Email / Header Analysis

**Filename:** `02-email-header.png`

Show useful fields such as `From`, `To`, `Subject`, `Date`, `Return-Path`, `Reply-To`, and the relevant `Received` header used to identify sending infrastructure. Avoid exposing sensitive internal mail-routing details.

### 03 — URL Reputation

**Filename:** `03-url-reputation.png`

Show a sanitized/defanged URL or domain and the relevant reputation verdict or detection summary from an approved source such as VirusTotal.

### 04 — WHOIS / RDAP Context

**Filename:** `04-domain-whois.png`

Show the domain, creation/registration date, registrar or registry context, and other relevant ownership/registration information. Treat IP geolocation as approximate and do not equate hosting location with attacker location.

### 05 — Safe Web Capture

**Filename:** `05-safe-web-capture.png`

Show a remote capture of the suspicious page from an approved web-capture or sandbox service. Highlight evidence of impersonation, credential fields, or suspicious redirects without directly browsing the live page from the analyst workstation.

### 06 — PhishTool Analysis

**Filename:** `06-phishtool-analysis.png`

Show the overall message analysis, extracted URLs, or relevant Web Capture/WHOIS information. Redact any live sensitive data.

### 07 — Hybrid Analysis / URLhaus (If Applicable)

**Filename:** `07-threat-intel-analysis.png`

Show relevant sandbox, reputation, tags, or MITRE ATT&CK information. Only include sources that provide meaningful evidence for the case.

### 08 — Attachment Hashes (If Attachment Exists)

**Filename:** `08-file-hashes.png`

Show PowerShell output for SHA256 and, when needed, SHA1/MD5:

```powershell
Get-FileHash .\filename.ext -Algorithm SHA256
Get-FileHash .\filename.ext -Algorithm SHA1
Get-FileHash .\filename.ext -Algorithm MD5
```

### 09 — Final IOC Register

**Filename:** `09-ioc-register.png`

Show the completed sanitized IOC table or worksheet with indicator type, value, assessment, evidence source, and recommended action.

## Adding Screenshots to the README

After saving an image, reference it with Markdown such as:

```markdown
![Raw email header analysis](evidence/screenshots/02-email-header.png)
```

Use short captions that explain **what the screenshot proves**, not merely which tool is shown.

## Minimum Recommendation

For a clean portfolio, screenshots 01–05 plus the final IOC register are sufficient. Add file-hash or sandbox screenshots only when the case actually contains an attachment or when those sources add meaningful evidence.

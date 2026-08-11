# HTML Credential Harvester Analysis

## Lab Overview

This investigation examined a phishing technique that delivered an HTML credential-harvesting page as an email attachment rather than placing a phishing URL directly in the email body.

The analysis focused on identifying the attachment, collecting file metadata, calculating a cryptographic hash, examining the rendered phishing page, identifying the targeted email address, decoding the HTML source, and observing how submitted credentials were transmitted through the web request.

## Tools Used

- Windows File Properties
- PowerShell
- Google Chrome
- Chrome Developer Tools
- CyberChef

## Investigation Scope

The investigation focused on the following questions:

- What file was attached to the phishing email?
- What is the SHA256 hash of the attachment?
- What is the file size?
- What service or company is the phishing page impersonating?
- What email address was pre-populated in the phishing page?
- What Microsoft logo file was referenced in the decoded source?
- Where were submitted credentials being transmitted?


---

## Investigation Findings

### 1. HTML Attachment Identification

![HTML attachment filename](../evidence/screenshots/html-credential-harvester/01-html-attachment-filename.png)

The suspicious attachment was located in the lab environment and its file properties were reviewed to identify the complete filename and file type.

**Observed attachment:** `MICRO.html`

The `.html` extension identifies the attachment as an HTML document capable of rendering web content locally in a browser. In the context of a phishing investigation, HTML attachments require careful examination because they can contain forms, scripts, redirects, or other content designed to imitate legitimate websites and collect user information.

At this stage, the file type alone does not establish malicious intent. The attachment was therefore treated as a suspicious artifact and examined further through hashing, metadata review, source-code analysis, and controlled behavioral observation.


### 2. SHA256 Hash Collection

![HTML attachment SHA256](../evidence/screenshots/html-credential-harvester/02-html-attachment-sha256.png)

PowerShell was used to calculate the SHA256 hash of the suspicious `MICRO.html` attachment. The `Get-FileHash` cmdlet was executed against the file, using its default SHA256 hashing algorithm.

**SHA256:**

`0FC57290189ADECFE17F6BACBC515ED080CD63C54B282FDEF4EF3DFC598CDD1E`

The SHA256 hash provides a unique identifier for the attachment and allows the file to be referenced without relying solely on its filename. In a SOC investigation, this value can be used for threat-intelligence searches, reputation checks, file correlation, and comparison against artifacts observed on other systems.

The hash itself does not determine whether the attachment is malicious. It serves as an investigation artifact that can be correlated with additional evidence collected during the analysis.


### 3. Attachment File Size

![HTML attachment file size](../evidence/screenshots/html-credential-harvester/03-html-attachment-file-size.png)

The file properties of `MICRO.html` were reviewed to collect additional metadata about the suspicious attachment.

**Observed file size:** `14.6 KB`

Recording the file size provides another identifying characteristic of the attachment and can assist with artifact comparison during an investigation.

File size alone does not indicate whether a file is malicious. It should be considered together with the filename, SHA256 hash, file contents, and observed behavior.

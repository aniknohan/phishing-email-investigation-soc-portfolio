# 02 — Artifact Collection

## Example Case

This public example uses sanitized indicators.

| Artifact | Example |
|---|---|
| Display Name | Account Security |
| Sender | security-alert@example-mail[.]test |
| Recipient | analyst-lab@example[.]test |
| Subject | Action Required: Verify Your Account |
| Date | 2026-08-09 10:14 UTC |
| Originating IP | 192.0.2.44 |
| URL | hxxps://account-review[.]example/login |
| Root Domain | account-review[.]example |
| Attachment | None |

## Manual Collection Procedure

### 1. Record visible email information

Capture the sender, recipient, subject, date, visible message content, hyperlink text, and attachment names.

### 2. Review the raw email or `.eml`

Open the message source in an appropriate text editor or email-analysis tool. Search for fields such as:

```text
From:
To:
Subject:
Date:
Return-Path:
Reply-To:
Received:
Message-ID:
```

### 3. Identify the originating infrastructure

Review the `Received` chain and any platform-specific originating IP field. Do not automatically assume the first visible IP is attacker-controlled; identify which server actually introduced the message into the mail flow.

### 4. Extract URLs safely

Prefer copying the hyperlink destination through message-source inspection or an analysis platform. Do not browse the suspicious URL directly.

For public documentation, defang it:

```text
https://evil.example/login
```

becomes:

```text
hxxps://evil[.]example/login
```

### 5. Hash attachments without executing them

On Windows PowerShell:

```powershell
Get-FileHash .\suspicious-file.pdf -Algorithm SHA256
Get-FileHash .\suspicious-file.pdf -Algorithm SHA1
Get-FileHash .\suspicious-file.pdf -Algorithm MD5
```

Record the filename, file size, and hashes.

## Evidence to Save

Save screenshots according to `screenshot-guide.md`. Do not save or publish the real malicious attachment in a public repository.

---

## Hands-On Manual Artifact Collection

The following section documents the manual collection of artifacts from email samples. Raw `.eml` content was reviewed to identify message metadata, sending infrastructure, URLs, domains, attachments, and file hashes.

### Email 1 — Header and Message Artifacts

#### Sender Address

![Email 1 sender address](../evidence/screenshots/manual-artifact-collection/01-email1-sender-addres.png)

The raw `.eml` file was opened in a text editor and the `From` field was located to identify the sender.

**Observed sender:** `security@netflixxuk.com`

The sender address was recorded as an email artifact for further investigation. The domain resembles the Netflix brand but should not be considered legitimate based on appearance alone. Additional infrastructure and URL analysis is required before reaching a final determination.

#### Recipient Address

![Email 1 recipient address](../evidence/screenshots/manual-artifact-collection/02-email1-recipient-address.png)

The raw `.eml` file was reviewed and the `To` field was located to identify the intended recipient.

**Observed recipient:** `jake.wood@dicksonunited.co.uk`

The recipient address was recorded as part of the message metadata. Identifying the intended recipient helps establish who was targeted by the message and provides context for determining the scope of the phishing investigation.

#### Subject

![Email 1 subject](../evidence/screenshots/manual-artifact-collection/03-email1-subject.png)

The raw `.eml` file was reviewed and the `Subject` field was located to identify the message subject.

**Observed subject:** `Netflix: Suspicious Account Activity`

The subject attempts to create concern by warning the recipient about suspicious activity involving a Netflix account. Security-related subject lines can be used to create urgency and encourage the recipient to interact with the message. This indicator should be evaluated together with the sender, URLs, sending infrastructure, and other email artifacts before reaching a final determination.


#### Date and Time

![Email 1 date and time](../evidence/screenshots/manual-artifact-collection/04-email1-date-time.png)

The raw `.eml` file was reviewed and the `Date` field was located to identify when the message was sent.

**Observed date/time:** `Sun, 3 May 2020 19:20:54 +0100`

The timestamp was recorded as part of the email metadata. Recording the message date and time helps establish the investigation timeline and can be correlated with other email, authentication, network, or endpoint activity.


#### Sender IP

![Email 1 sender IP](../evidence/screenshots/manual-artifact-collection/05-email1-sender-ip.png)

The raw `.eml` file was reviewed to identify the IP address associated with the message's sending infrastructure.

**Observed sender IP:** `54.240.5.4`

The sender IP was recorded as an infrastructure artifact for further investigation. An IP address can be used for additional enrichment, including WHOIS/RDAP ownership checks, reverse DNS lookups, reputation analysis, and correlation with other security telemetry. The IP should not be considered malicious based on the email header alone.


#### Reverse DNS Lookup

![Email 1 reverse DNS](../evidence/screenshots/manual-artifact-collection/06-email1-reverse-dns.png)

A reverse DNS lookup was performed on the identified sender IP address `54.240.5.4` to determine whether a hostname was associated with the sending infrastructure.

**Observed IP:** `54.240.5.4`

**Reverse DNS result:** `a5-4[.]smtp-out.eu-west-1[.]amazonses[.]com`

The reverse DNS result was recorded as an infrastructure artifact. This information can help identify the network or service associated with the sending IP and provide additional context during the investigation. A reverse DNS result alone does not establish whether the message is legitimate or malicious.


#### URL Extraction

![Email 1 URL extraction](../evidence/screenshots/manual-artifact-collection/07-email1-url-extraction.png)

The email was reviewed to identify the destination of the embedded hyperlink. The URL was extracted without directly navigating to the destination, reducing the risk of interacting with potentially malicious content.

**Observed URL (defanged):**

`hxxps://www[.]thiswouldbeamalicioussite[.]com/index/2020/j411/NetflixLogin[.]php`

The URL was recorded as an investigation artifact for further analysis. The path contains `NetflixLogin.php`, which is consistent with a page designed to imitate a Netflix login workflow. This observation should be correlated with the sender information, domain analysis, and other indicators before reaching a final verdict.

For safe documentation, the URL has been defanged by replacing `https` with `hxxps` and periods in the domain with `[.]`.


#### Root Domain Identification

![Email 1 root domain](../evidence/screenshots/manual-artifact-collection/08-email1-root-domain.png)

After extracting the URL from the email, the URL structure was reviewed to identify the root domain.

**Observed URL (defanged):**  
`hxxps://www[.]thiswouldbeamalicioussite[.]com/index/2020/j411/NetflixLogin[.]php`

**Root domain:** `thiswouldbeamalicioussite[.]com`

The root domain was separated from the remaining URL path so it could be used as an individual investigation artifact. Identifying the root domain allows the analyst to perform additional enrichment such as WHOIS/RDAP, DNS, reputation, and threat-intelligence checks without relying only on the complete URL.

The domain has been defanged in this documentation to prevent accidental navigation.


### Email 2 — Header, Message, and Attachment Artifacts

#### Sender Address

![Email 2 sender address](../evidence/screenshots/manual-artifact-collection/09-email2-sender-address.png)

The raw `.eml` file was opened in Sublime Text and the `From` field was located using the Find feature (`Ctrl + F`) to identify the sender's email address.

**Observed sender:** `elli0taaa@outlook.com`

The sender address was recorded as part of the email metadata for further investigation. Identifying the sender provides an artifact that can be correlated with the sending IP address, email headers, message content, and attachment information.

At this stage, the sender address alone does not establish whether the message is malicious. Additional analysis of the email infrastructure and attachment is required.


#### Recipient Address

![Email 2 recipient address](../evidence/screenshots/manual-artifact-collection/10-email2-recipient-address.png)

The raw `.eml` file was reviewed in Sublime Text and the `To` field was located to identify the intended recipient of the message.

**Observed recipient:** `andrewadams112@hotmail.co.uk`

The recipient address was recorded as part of the email metadata. Identifying the intended recipient helps establish who was targeted by the message and provides context for determining the scope of the investigation.

In a production SOC environment, this artifact could also be used to search for related messages, determine whether additional users received the same email, and assess the potential impact of the campaign.

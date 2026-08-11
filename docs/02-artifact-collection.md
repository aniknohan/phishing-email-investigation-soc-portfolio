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

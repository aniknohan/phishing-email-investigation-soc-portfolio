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

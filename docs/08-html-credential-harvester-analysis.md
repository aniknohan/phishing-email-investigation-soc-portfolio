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

# 04 — Defensive Actions

## Recommended Containment

1. Block the confirmed malicious sender address if appropriate to the organization's email-security design.
2. Block the confirmed malicious URL/domain at the email, proxy, DNS, secure web gateway, or other relevant controls.
3. Search the mail environment for additional copies of the message.
4. Remove matching malicious messages from user mailboxes when authorized.

## Scope Investigation

Search available telemetry for:

- Additional recipients of the same message
- Click activity related to the URL
- DNS requests for the domain
- Proxy/web requests
- Endpoint browser activity
- Authentication activity after the suspected click
- Similar messages from related senders

## If a User Clicked but Entered No Credentials

Review endpoint and web telemetry. Determine whether the site attempted downloads, redirects, or other follow-on activity.

## If Credentials Were Submitted

Follow organizational procedures for:

- Password reset
- Session/token revocation
- MFA review or reset when required
- Authentication-log review
- Impossible-travel or unusual-login review
- Mailbox rule/forwarding-rule review where relevant
- Escalation according to incident severity

## Recovery and Prevention

- Confirm IOC blocks are active.
- Confirm malicious messages were removed.
- Notify impacted users according to policy.
- Preserve evidence.
- Update detections if the investigation revealed reusable indicators or behaviors.

## Important Analyst Note

Do not block a large shared provider or legitimate root domain solely because one sender or compromised path was abused. Defensive actions should minimize business impact and be based on the specific evidence observed.

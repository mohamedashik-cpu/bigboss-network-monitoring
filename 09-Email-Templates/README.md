# NOC and ISP Email Templates

This section provides reusable, generic email wording for common ISP and network-incident communications, including new link incidents, status follow-ups, escalations, and restoration updates.

> **Confidentiality:** These are public learning templates only. Add real site details, circuit IDs, bandwidth, contact information, and provider references only in approved company communication systems. Never commit real customer or production details to this repository.

## Guides in This Section

1. [ISP Link Down and Flapping Emails](01-ISP-Link-Down-and-Flapping-Emails.md) — starting templates for reporting a verified link-down or link-flapping issue to an ISP.
2. [ISP Follow-up and Escalation Emails](02-ISP-Follow-up-Escalation-and-Restoration.md) — templates for requesting updates, following up on an ETR, and escalating an unresolved issue.

## Choosing the Right Template

| Situation | Template to use |
|---|---|
| Newly detected link-down issue | Link Down email |
| Link repeatedly changes between Up and Down | Link Flapping email |
| Waiting for an ISP status update | Follow-up email |
| Previously advised ETR has passed | ETR-exceeded follow-up |
| Issue needs higher-level attention | Escalation email |
| ISP reports the service is restored | Restoration update or verification response |

Select wording that matches the verified condition. Do not label a link as flapping unless repeated Up/Down transitions have been observed.

## Before Sending

- [ ] Confirm the alert and current status.
- [ ] Verify the affected link type and bandwidth.
- [ ] Confirm the approved site/circuit identifiers in the internal system.
- [ ] Include the incident start time and impact when known.
- [ ] State only verified facts; do not guess the root cause.
- [ ] Request a ticket/reference number and ETR when appropriate.
- [ ] Check recipients, subject, spelling, and tone.
- [ ] Use the company's approved signature and communication channel.
- [ ] Keep production details out of this public GitHub repository.

## Professional Email Structure

1. **Subject:** Short and specific, such as the link type and observed symptom.
2. **Greeting:** Address the provider/team professionally.
3. **Issue summary:** Explain what has been observed and since when, if verified.
4. **Reference details:** Add approved link/site/circuit information in the actual company email.
5. **Request:** Ask the ISP to investigate and provide a status update or ETR.
6. **Closing:** Use a polite, concise sign-off.

## Writing Tips

- Keep the email concise and easy to scan.
- Use “Please investigate and share an update” instead of vague or overly forceful wording.
- Ask for a revised ETR when the previous estimate has passed.
- Do not promise an ETR on behalf of the provider.
- After a restoration notification, verify the service internally before confirming it is fully restored.
- Keep follow-up messages factual and include the relevant provider reference in approved systems.

## Related Sections

- [Network Monitoring](../01-Network-Monitoring/README.md)
- [Troubleshooting](../02-Troubleshooting/README.md)
- [ILL](../04-ILL/README.md)
- [P2P](../05-P2P/README.md)
- [ISP Coordination](../06-ISP-Coordination/README.md)
- [Ticketing](../07-Ticketing/README.md)
- [Glossary](../10-Glossary/README.md)

## Learning Outcome

After reviewing these templates, you should be able to write clear and professional ISP emails for common link incidents, follow-ups, escalations, and restoration updates while keeping production details confidential.

## Author

**Mohamed Ashik**

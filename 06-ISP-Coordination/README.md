# ISP Coordination

This section covers professional, evidence-based communication with Internet Service Providers (ISPs) during network incidents. It focuses on preparing verified information, raising and tracking tickets, following up on status and ETR, escalating unresolved issues, and confirming restoration.

> **Confidentiality:** This public repository uses generic examples only. Never publish real circuit IDs, customer/site details, internal IP addresses, provider ticket numbers, contact details, monitoring screenshots, or other confidential operational information.

## Guides in This Section

1. [ISP Coordination Workflow](01-ISP-Coordination-Workflow.md) — when to contact an ISP, what information to prepare, ticket tracking, follow-up, escalation, and restoration verification.
2. [ISP Call and Email Communication](02-ISP-Call-and-Email-Communication.md) — practical call scripts and email wording for common incident scenarios.

## Before Contacting the ISP

- [ ] Verify the alert and current link status.
- [ ] Confirm the affected link type and scope.
- [ ] Perform authorized first-line checks.
- [ ] Record relevant timestamps and observed results.
- [ ] Check whether an ISP ticket already exists.
- [ ] Prepare the approved circuit/site reference and confirmed impact.
- [ ] Keep assumptions separate from verified facts.

Use real operational identifiers only in approved company email, ticketing, and monitoring systems.

## ISP Coordination Workflow

**Verify Incident → Gather Evidence → Contact ISP → Raise/Confirm Ticket → Record Reference → Request Status and ETR → Follow Up → Escalate When Required → Verify Restoration → Document Outcome**

## Common Communication Scenarios

| Scenario | Information or request |
|---|---|
| New Link Down/Flapping issue | State the verified symptom, link type, impact, and relevant time; request investigation |
| Ticket/reference tracking | Ask for the provider's ticket/reference number |
| Status follow-up | Request the latest investigation status and next update |
| ETR request | Ask for the estimated restoration time when appropriate |
| ETR exceeded | Mention the previous advised ETR accurately and request a revised estimate |
| Escalation | Explain the ongoing issue and verified impact; request escalation through the provider's process |
| ISP reports restoration | Acknowledge the update and perform internal verification |
| No fault found | Share observed test results and request the next recommended investigation step |

## ETR and ETA

- **ETR (Estimated Time to Restore):** The expected time for the affected service to be restored.
- **ETA (Estimated Time of Arrival):** Often refers to a person's or resource's expected arrival; clarify the intended meaning in your team's process.
- Record the time exactly as communicated and include the relevant date/time zone where needed.
- If no estimate has been provided, record it as pending rather than inventing one.
- If an estimate is exceeded, request a status update and revised estimate.

Follow the definitions and escalation timelines used by your organization.

## Communication Best Practices

- Keep messages short, polite, and specific.
- Ask one clear question at a time during calls.
- Repeat important reference numbers and time estimates to confirm them.
- Record who provided an update, when it was received, and what was said.
- Do not promise a restoration time on behalf of the ISP.
- Do not state that the service is restored until internal checks confirm it.
- Follow approved escalation paths and communication rules.

## Generic Follow-up Record

| Field | Record |
|---|---|
| Incident symptom | Verified Down / Flapping / other symptom |
| ISP reference | Stored in approved internal system |
| Last provider update | Factual summary and timestamp |
| ETR | Advised value or Pending |
| Next follow-up | As required by the approved process |
| Escalation status | Not required / Raised / Pending |
| Restoration status | Pending verification / Verified |
| Next action | Follow-up, escalation, monitoring, or closure |

## Related Sections

- [Network Monitoring](../01-Network-Monitoring/README.md)
- [Troubleshooting](../02-Troubleshooting/README.md)
- [ILL](../04-ILL/README.md)
- [P2P](../05-P2P/README.md)
- [Ticketing](../07-Ticketing/README.md)
- [Email Templates](../09-Email-Templates/README.md)
- [Glossary](../10-Glossary/README.md)

## Learning Outcome

After reviewing these guides, you should be able to communicate clearly with an ISP, share verified incident evidence, track provider tickets and ETR updates, escalate according to the approved process, and verify service restoration before closure.

## Author

**Mohamed Ashik**

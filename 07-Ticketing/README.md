# NOC Ticketing

This section documents the ticket lifecycle used to record, track, update, escalate, hand over, and close network incidents. The guides are designed as a practical reference for NOC operations and ISP coordination.

> **Confidentiality:** This public learning repository contains generic examples only. Never publish real customer details, internal IP addresses, circuit IDs, production ticket IDs, credentials, screenshots, or other confidential company information.

## Guides in This Section

1. [NOC Ticketing Workflow](01-NOC-Ticketing-Workflow.md) — the ticket lifecycle from incident reporting through verification and closure.
2. [Ticket Update and Closure Examples](02-Ticket-Update-and-Closure-Examples.md) — practical examples for incident updates, ISP follow-up, restoration, handover, and closure.
3. [Ticket Priority and Severity](03-Ticket-Priority-and-Severity.md) — how impact, urgency, severity, and priority are considered.
4. [Ticket SLA and Escalation Tracking](04-Ticket-SLA-and-Escalation-Tracking.md) — tracking milestones, due times, escalation, and SLA risk.
5. [NOC Ticket Shift Handover](05-NOC-Ticket-Shift-Handover.md) — transferring open incidents and pending actions between shifts.
6. [Ticket RCA Requirement and Tracking](06-Ticket-RCA-Requirement-and-Tracking.md) — identifying when an RCA is required and tracking its status.
7. [Ticket Reopen and Recurring Incident Handling](07-Ticket-Reopen-and-Recurring-Incident-Handling.md) — handling repeat symptoms, reopened tickets, and recurring incidents.
8. [Ticket Maintenance and Planned Change Handling](08-Ticket-Maintenance-and-Planned-Change-Handling.md) — tracking planned maintenance, approved changes, and post-change verification.

## Ticket Lifecycle

**Detect/Receive → Verify → Create or Update Ticket → Set Priority According to Policy → Record Actions and Evidence → Coordinate with Internal Team/ISP → Track SLA and ETR → Escalate When Required → Verify Restoration → Monitor if Required → Document Resolution → Close According to SOP**

Follow the organization's ticketing policy. Priority labels, SLA targets, mandatory fields, and closure rules may vary by organization.

## Essential Ticket Information

A clear ticket generally records:

- **Summary:** Short, specific description of the symptom
- **Detection/report time:** Verified date and time
- **Scope and impact:** Affected service or users, based on available evidence
- **Current status:** What is known at the time of the update
- **Checks performed:** Actions taken and their results
- **Evidence:** Relevant timestamps and sanitized outputs
- **Owner/team:** Responsible team or provider, according to process
- **Reference:** Related ISP or internal ticket reference, stored in approved systems
- **Next action:** Follow-up, investigation, escalation, or verification
- **Restoration and closure:** Verified outcome and closure notes

## Ticket Quality Checklist

- [ ] Use a concise, factual title.
- [ ] Verify the issue before describing it as confirmed.
- [ ] Separate observed symptoms from suspected causes.
- [ ] Add timestamps and action updates in chronological order.
- [ ] Record provider updates and ETR accurately when applicable.
- [ ] Reassess priority using approved impact and urgency rules.
- [ ] Escalate according to policy when required.
- [ ] Include useful handover notes for unresolved incidents.
- [ ] Verify restoration before marking the service recovered.
- [ ] Close only after the required checks and documentation are complete.
- [ ] Keep confidential production details out of this public repository.

## Common Ticket Status Language

| Status wording | Intended meaning |
|---|---|
| Investigating | Checks are in progress |
| Awaiting ISP | Provider action or update is pending |
| ETR Pending | A restoration estimate has not been provided or confirmed |
| Escalated | Raised through the designated escalation process |
| Restored — Verification Pending | Restoration was reported, but internal verification is incomplete |
| Monitoring for Stability | Service is available and being observed for recurrence |
| RCA Pending | Root cause analysis or its required evidence/report is outstanding |
| Resolved / Closed | Use according to the organization's formal status definitions |

Use the exact statuses defined in your ticketing platform and SOP.

## Related Sections

- [Network Monitoring](../01-Network-Monitoring/README.md)
- [Troubleshooting](../02-Troubleshooting/README.md)
- [ILL](../04-ILL/README.md)
- [P2P](../05-P2P/README.md)
- [ISP Coordination](../06-ISP-Coordination/README.md)
- [RCA](../08-RCA/README.md)
- [Email Templates](../09-Email-Templates/README.md)
- [Glossary](../10-Glossary/README.md)

## Learning Outcome

After reviewing these guides, you should be able to write useful incident updates, track priority and SLA risk, coordinate ISP actions, maintain shift handover, manage recurring incidents, and document verified restoration and closure.

## Author

**Mohamed Ashik**

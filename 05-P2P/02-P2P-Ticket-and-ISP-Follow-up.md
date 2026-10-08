# P2P Ticket and ISP Follow-up Workflow

## Overview

When a Point-to-Point (P2P) link requires ISP assistance, the NOC team should follow a structured process from incident verification through ticket creation, ISP follow-up, escalation, restoration verification, and closure.

This document focuses specifically on **P2P ticket handling and ISP coordination**.

> Important: All examples are generic and sanitized. Do not publish customer details, real circuit IDs, production IP addresses, ticket numbers, contact details, or company-confidential information.

## Objectives

- Raise clear P2P ISP tickets
- Provide useful technical information
- Track ISP ticket references
- Follow up on investigation progress
- Track ETR
- Escalate delayed incidents
- Verify restoration from the NOC side
- Maintain a complete incident timeline
- Support proper shift handover and closure

## P2P Ticket Workflow

~~~text
P2P Issue Detected
        |
        v
Verify Issue
        |
        v
Collect Technical Details
        |
        v
Raise ISP Ticket
        |
        v
Record ISP Reference
        |
        v
Follow Up / Get Status
        |
        v
Track ETR
        |
        +---- Still Down ----> Continue Follow-up / Escalate
        |
        +---- Restored -----> Verify from NOC
                                  |
                                  v
                             Monitor Stability
                                  |
                                  v
                             Update / Close
~~~

## 1. Verify Before Raising the Ticket

Before contacting the ISP:

- Confirm the monitoring alert.
- Identify the affected P2P service.
- Record the detection time.
- Check endpoint reachability.
- Check local interface status.
- Check relevant interface counters.
- Check device logs when applicable.
- Check whether related alerts exist.
- Record the checks already completed.

The objective is to provide evidence rather than assumptions.

## 2. Information Required for a P2P Ticket

A generic P2P ticket can contain:

| Information | Example |
|---|---|
| Service Type | P2P |
| Issue | Link Down |
| Detection Time | YYYY-MM-DD HH:MM |
| Current Status | Down |
| Endpoint | Endpoint-A / Endpoint-B |
| Interface | Interface-X |
| Verification | Reachability/interface checks completed |
| Observation | Link remains down |
| Request | Please investigate and restore |
| ISP Reference | To be provided |
| ETR | To be provided |

Use actual service identifiers only through authorized company/ISP channels.

## 3. Raising the ISP Ticket

Use the approved ISP support channel, such as:

- ISP support portal
- Official support email
- Approved support number
- Existing escalation channel

When creating the ticket:

1. Clearly identify the service type as P2P.
2. State the issue.
3. Include the detection time.
4. Provide relevant technical observations.
5. Mention completed checks.
6. Request investigation.
7. Request the ISP ticket/reference number.
8. Request ETR when applicable.

## 4. Generic P2P Ticket Message

~~~text
Subject: P2P Link Down - Investigation Required

Hello Team,

We are observing a P2P link-down issue for the affected service.

Issue Start Time: YYYY-MM-DD HH:MM
Service Type: P2P
Current Status: Link Down
Basic Verification: Endpoint and interface checks completed.

Please investigate the issue and provide the ISP ticket/reference number along with the current status and ETR.

Regards,
NOC Team
~~~

This is a generic learning template. Use the organization's approved communication format for real incidents.

## 5. ISP Ticket Reference Tracking

After the ISP creates the ticket, record the reference in the approved internal system.

Generic example:

~~~text
Internal Incident: Ticket-XXXX
ISP Reference: ISP-Ticket-XXXX
Service: P2P-Service-XXXX
Status: ISP Investigation
ETR: Pending
~~~

Do not store real ticket references in this public repository.

## 6. Initial ISP Follow-up

After raising the ticket, confirm:

- Ticket was received
- ISP reference is valid
- Current investigation status
- Whether an engineer/team has been assigned
- Whether additional information is required
- Current or expected ETR

Generic internal note:

~~~text
Time: HH:MM
Action: Initial ISP follow-up completed
ISP Status: Investigation in progress
ETR: Pending
Next Action: Follow up as per escalation process
~~~

## 7. Regular Follow-up

Each follow-up should record:

- Date and time
- Contact/channel used
- ISP ticket reference
- Current status
- Latest technical update
- ETR
- Next follow-up requirement
- Escalation status if applicable

Example:

| Time | Action | ISP Status | ETR | Next Action |
|---|---|---|---|---|
| HH:MM | Ticket raised | Open | Pending | Await update |
| HH:MM | Follow-up | Investigating | HH:MM | Monitor |
| HH:MM | Follow-up | Work in progress | HH:MM | Follow up |
| HH:MM | Follow-up | Restored | N/A | Verify |

## 8. ETR Tracking

**ETR = Estimated Time of Restoration.**

When the ISP provides an ETR:

~~~text
ISP Status: Work in progress
ETR: YYYY-MM-DD HH:MM
~~~

ETR should be treated as an estimate.

If the ETR is missed:

1. Recheck the P2P monitoring status.
2. Contact the ISP.
3. Request the latest status.
4. Request a revised ETR.
5. Escalate according to the approved process if required.

## 9. ISP Escalation

Escalation may be required when:

- P2P link remains down beyond the expected timeline.
- ISP ETR is missed.
- Updates are delayed.
- The issue has significant operational impact.
- Repeated follow-ups do not provide progress.
- The approved escalation threshold is reached.

Use only approved escalation contacts and procedures.

Do not publish real escalation contacts in this repository.

## 10. Useful Follow-up Questions

Professional questions that can be used during ISP follow-up:

- “Could you please confirm the current status of the P2P ticket?”
- “Could you please provide the latest ETR?”
- “Has the fault been identified?”
- “Has the issue been assigned to the concerned technical team?”
- “Could you please confirm the next update time?”
- “The link is still showing down on our monitoring. Could you please investigate further?”
- “The previous ETR has passed. Could you please provide a revised ETR?”

## 11. Restoration Notification

If the ISP reports that the P2P link has been restored:

**Do not close the ticket immediately.**

First verify:

- Monitoring alert cleared
- Endpoint reachable
- Interface is operational
- Packet loss is normal
- Latency is within expected observation
- No repeated flapping
- Service remains stable

## 12. Restoration Verification Example

~~~text
ISP Status: Restored
Monitoring: Alert cleared
Endpoint Reachability: Successful
Interface: Up / Up
Packet Loss: No abnormal loss observed
Latency: Within expected observation
Flapping: Not observed
Stability: Monitoring continued
~~~

Record the actual restoration time based on monitoring or the approved internal procedure.

## 13. Post-Restoration Follow-up

After technical verification:

- Update the internal incident.
- Confirm the service is stable.
- Record the restoration time.
- Capture the final ISP update.
- Check whether an RCA is required.
- Start the approved closure process.

If the service goes down again, treat it as an ongoing or recurring incident according to the organization's procedure.

## 14. P2P Incident Timeline

**Example only:**

~~~text
14:00 - P2P link-down alert detected
14:05 - Alert verified
14:10 - Endpoint and interface checks completed
14:15 - ISP ticket raised
14:20 - ISP reference received
15:00 - Initial ISP follow-up
15:05 - ETR received
16:00 - Follow-up completed
16:30 - Previous ETR missed
16:35 - ISP escalation performed
17:10 - ISP reports restoration
17:15 - NOC verifies connectivity
17:30 - Stability monitoring completed
17:45 - Incident updated for closure
~~~

Times are illustrative only.

## 15. Shift Handover for an Open P2P Ticket

If the incident remains open during shift change, hand over:

- P2P service reference
- Issue
- Detection time
- Current monitoring status
- ISP ticket reference
- Latest ISP update
- Current ETR
- Last follow-up time
- Next follow-up time
- Escalation status
- Checks already completed

Generic handover:

~~~text
P2P Service: P2P-Service-XXXX
Issue: Link Down
Status: ISP Investigation
ISP Ref: ISP-Ticket-XXXX
ETR: YYYY-MM-DD HH:MM
Last Follow-up: YYYY-MM-DD HH:MM
Next Action: Follow up at agreed time
Monitoring: Link still down
Escalation: Not yet required
~~~

## 16. Closure Checklist

Before closing a P2P incident:

- [ ] ISP reports restoration
- [ ] Monitoring alert cleared
- [ ] Endpoint reachable
- [ ] Interface verified
- [ ] Packet loss checked
- [ ] Latency checked where applicable
- [ ] No repeated flapping observed
- [ ] Stability monitored
- [ ] Restoration time recorded
- [ ] ISP final update recorded
- [ ] Internal ticket updated
- [ ] RCA requirement checked
- [ ] Closure completed according to procedure

## 17. Communication Best Practices

When coordinating with the ISP:

- Be concise.
- Use exact timestamps.
- State the observed issue clearly.
- Mention completed checks.
- Ask direct questions.
- Record every important response.
- Avoid assumptions.
- Maintain professional communication.
- Use approved escalation channels.

## 18. Common Mistakes to Avoid

### Closing Immediately After ISP Restoration

**Problem:** The ISP says the service is restored, but NOC verification is skipped.

**Better approach:** Verify monitoring, reachability, interface state, and stability before closure.

### Not Recording ETR

**Problem:** Follow-up becomes difficult because there is no expected restoration time.

**Better approach:** Request and record ETR whenever available.

### Missing Follow-up

**Problem:** An open P2P incident remains unattended.

**Better approach:** Record the next follow-up time and include it in shift handover.

### Providing Too Little Technical Information

**Problem:** ISP needs additional information before starting investigation.

**Better approach:** Include issue type, timestamp, service reference, observations, and checks already completed.

### Sharing Confidential Data Publicly

**Problem:** Production information can be exposed.

**Better approach:** Use sanitized placeholders in documentation and keep real information inside approved systems.

## Confidentiality

Never publish:

- Customer names
- Real P2P circuit IDs
- Production IP addresses
- ISP ticket numbers
- Internal ticket numbers
- Phone numbers
- Email addresses
- Credentials
- Monitoring screenshots containing real data
- Internal escalation contacts
- Proprietary ISP information
- Company-confidential information

Use placeholders:

~~~text
Customer-Site-A
P2P-Service-XXXX
Ticket-XXXX
ISP-Ticket-XXXX
Generic-ISP
Endpoint-A
Endpoint-B
Interface-X
X.X.X.X
~~~

## Key Takeaways

- Verify the P2P issue before raising the ISP ticket.
- Provide concise and useful technical evidence.
- Always record the ISP reference.
- Track follow-ups and ETR.
- Escalate missed ETRs according to the approved process.
- Never close only because the ISP says “restored.”
- Verify recovery from the NOC side.
- Maintain complete records for shift handover and closure.

## Related Topics

- P2P Monitoring and Troubleshooting
- ILL Ticket and ISP Follow-up Workflow
- ISP Coordination
- Ticketing
- Monitoring Logs and Documentation
- RCA
- Shift Handover

## Author

Mohamed Ashik

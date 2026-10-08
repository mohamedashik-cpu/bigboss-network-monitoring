# Ticket RCA Requirement and Tracking

## Overview

RCA = **Root Cause Analysis**.

RCA is used to understand why an incident occurred, not just what symptom was observed or how the service was restored.

In NOC operations, RCA tracking helps identify recurring problems, document confirmed causes, and record corrective and preventive actions.

> Important: This is a generic learning guide. Never publish customer information, production IP addresses, circuit IDs, internal ticket IDs, credentials, screenshots, or confidential company information.

## Objectives

- Understand when RCA may be required
- Differentiate symptom, cause, and resolution
- Build an incident timeline
- Track RCA status
- Record confirmed root cause
- Document corrective and preventive actions
- Track RCA pending actions
- Link recurring incidents to historical records

## 1. What Is RCA?

RCA means identifying the underlying reason that caused an incident.

Simple example:

~~~text
Symptom:
Network link is down.

Immediate action:
ISP contacted and service restored.

Root Cause:
<Confirmed technical cause>

Corrective Action:
<Action taken to restore/fix the issue>

Preventive Action:
<Action intended to reduce recurrence>
~~~

A restoration action alone is not necessarily the root cause.

## 2. Symptom vs Root Cause

### Symptom

What was observed.

Examples:

- Link Down
- Packet Loss
- High Latency
- Interface Flapping
- Device Unreachable

### Root Cause

Why the symptom occurred.

Examples:

- Confirmed fiber cut
- Hardware failure
- Power failure
- Configuration issue
- Interface fault
- ISP-side equipment failure

Only record a root cause when it has been confirmed by a reliable source.

## 3. Resolution vs Root Cause

These terms are different.

**Resolution** = What restored the service.

**Root Cause** = Why the incident happened.

Example:

~~~text
Issue:
P2P link unavailable

Resolution:
ISP restored the circuit.

Root Cause:
ISP confirmed an upstream fiber issue.

Corrective Action:
Service path repaired.

Preventive Action:
ISP review / redundancy improvement as applicable.
~~~

## 4. When May RCA Be Required?

RCA requirements vary by organization.

Common triggers can include:

- Major incident
- Critical service outage
- Repeated incident
- Prolonged outage
- SLA-impacting incident
- Significant business impact
- Security-related incident
- Infrastructure failure
- Management-requested RCA
- Customer-requested RCA
- Recurring link flapping or packet loss

Always follow the organization's official RCA policy.

## 5. RCA Tracking Workflow

~~~text
Incident Occurs
      ↓
Incident Verified
      ↓
Service Restored
      ↓
RCA Requirement Identified
      ↓
Evidence / Timeline Collected
      ↓
Root Cause Confirmed
      ↓
Corrective Action Recorded
      ↓
Preventive Action Recorded
      ↓
RCA Reviewed
      ↓
RCA Closed
~~~

## 6. RCA Status

A generic RCA status model:

| Status | Meaning |
|---|---|
| Not Required | RCA is not applicable |
| Pending | RCA is required but not started/completed |
| Investigation | Cause is being investigated |
| Awaiting ISP | Waiting for external RCA |
| Awaiting Internal Team | Waiting for internal technical information |
| Draft | RCA information prepared but not finalized |
| Review | RCA submitted for review |
| Closed | RCA completed and accepted according to process |

Use the organization's actual status names where applicable.

## 7. Incident Timeline

A clear timeline is one of the most useful RCA inputs.

Example:

~~~text
09:10 - Monitoring alert received
09:15 - Alert verified
09:20 - Link status checked
09:25 - ISP contacted
09:30 - ISP ticket created
10:00 - ISP investigation update received
11:00 - Service restored
11:05 - NOC verification completed
11:30 - Stability monitoring completed
12:00 - Root cause information received
~~~

Use actual confirmed timestamps in real tickets.

## 8. Evidence Collection

Depending on the incident, useful evidence may include:

- Monitoring alerts
- Interface status
- Interface counters
- Device logs
- Ping results
- Traceroute results
- ISP updates
- Ticket updates
- Incident timestamps
- Maintenance information
- Change records
- Approved screenshots
- ISP RCA document

Only collect information permitted by company policy.

## 9. Cisco Evidence Examples

For a network incident, commonly useful commands include:

~~~text
show ip interface brief
show interfaces <interface>
show interfaces description
show interfaces counters errors
show logging
~~~

These commands can help establish the operational condition of the device or interface.

Do not paste real production output into a public repository.

## 10. ISP RCA

For ISP-managed incidents, the final root cause may need to come from the ISP.

Example:

~~~text
Incident:
P2P service unavailable

ISP Status:
Service restored

ISP RCA:
<Confirmed ISP explanation>

Corrective Action:
<Confirmed action>

Preventive Action:
<Confirmed preventive measure, if provided>
~~~

Do not assume an ISP root cause based only on symptoms.

## 11. RCA Evidence vs Assumption

### Evidence-Based

~~~text
ISP confirmed a fiber-related issue.
~~~

### Assumption

~~~text
The fiber must have been cut.
~~~

Unless the cause is confirmed, use wording such as:

~~~text
Suspected Cause:
<Description>

Confirmation:
Pending ISP / Internal Team confirmation.
~~~

This prevents inaccurate RCA documentation.

## 12. Corrective Action

Corrective action addresses the incident or restores the affected service.

Examples:

- Replace failed hardware
- Repair damaged cable
- Correct configuration
- Restore a failed interface
- Replace faulty power equipment
- Repair ISP infrastructure

Only document actions that were actually performed or officially confirmed.

## 13. Preventive Action

Preventive action aims to reduce the chance of recurrence.

Examples:

- Improve redundancy
- Replace aging equipment
- Review configuration
- Improve monitoring
- Add alerting
- Schedule preventive maintenance
- Review ISP escalation process
- Update operational documentation

Preventive actions should be practical and trackable.

## 14. RCA Action Tracking

A simple action tracker:

| Action | Type | Owner | Due Date | Status |
|---|---|---|---|---|
| <Action> | Corrective | <Team> | <Date> | Open |
| <Action> | Preventive | <Team> | <Date> | In Progress |
| <Action> | Preventive | <Team> | <Date> | Closed |

Use approved team names and dates in internal systems.

## 15. RCA Pending Follow-up

If RCA is not yet received:

~~~text
Ticket: Ticket-XXXX
RCA Status: Awaiting ISP

Incident: <Issue>
Service Restored: YYYY-MM-DD HH:MM

Last ISP Update:
<RCA pending>

Next Follow-up:
YYYY-MM-DD HH:MM

Pending Action:
Follow up with ISP for final RCA.
~~~

RCA should not be forgotten after service restoration.

## 16. RCA and Ticket Closure

If the process requires RCA before closure:

~~~text
Service Restored
      ↓
RCA Requested
      ↓
RCA Received
      ↓
RCA Reviewed
      ↓
Corrective / Preventive Actions Tracked
      ↓
Ticket Closed
~~~

If the ticket can be closed before RCA completion, keep the RCA as a separate tracked action according to the organization's process.

## 17. Recurring Incident Tracking

Recurring incidents should be compared with historical incidents.

Track:

- Previous ticket reference
- Incident type
- Start time
- Duration
- Affected service
- Confirmed root cause
- Previous corrective action
- Recurrence count
- Current preventive action

Example:

~~~text
Incident Type: Link Flapping
Current Ticket: Ticket-XXXX
Previous Ticket: Ticket-XXXX
Recurrence: Yes

Previous Root Cause:
<Confirmed cause>

Current Status:
Investigation

Pending:
Determine whether the current incident has the same root cause.
~~~

## 18. RCA Quality Check

Before finalizing an RCA:

~~~text
[ ] Incident description is clear
[ ] Timeline is complete
[ ] Symptoms are documented
[ ] Evidence is available
[ ] Root cause is confirmed
[ ] Resolution is documented
[ ] Corrective action is documented
[ ] Preventive action is documented where required
[ ] Owner is identified
[ ] Due dates are recorded
[ ] Supporting teams have reviewed the information
[ ] Confidential information is handled correctly
~~~

## 19. Generic RCA Template

~~~text
RCA - Ticket-XXXX

Incident:
<Short incident description>

Service:
<Service>

Priority:
P1 / P2 / P3 / P4

Incident Start:
YYYY-MM-DD HH:MM

Restoration Time:
YYYY-MM-DD HH:MM

Duration:
<Duration>

Impact:
<Generic business/service impact>

### Timeline

YYYY-MM-DD HH:MM - <Event>
YYYY-MM-DD HH:MM - <Event>
YYYY-MM-DD HH:MM - <Event>
YYYY-MM-DD HH:MM - <Event>

### Symptoms

- <Observed symptom>
- <Observed alert>
- <Observed behavior>

### Investigation

- <Check performed>
- <Result>
- <Check performed>
- <Result>

### Root Cause

<Confirmed root cause>

### Resolution

<Action that restored the service>

### Corrective Action

<Action taken to correct the issue>

### Preventive Action

<Action intended to reduce recurrence>

### Action Tracking

Owner: <Team>
Due Date: YYYY-MM-DD
Status: Open / In Progress / Closed

### RCA Status

Pending / Investigation / Review / Closed

### Remarks

<Additional confirmed information>
~~~

## 20. Example - Link Down RCA

~~~text
Incident:
P2P link unavailable.

Symptom:
Monitoring reported the link as down.

Investigation:
NOC verified the alert and checked device/interface status.
ISP ticket was raised.

Restoration:
ISP restored service.

Root Cause:
ISP confirmed an upstream connectivity issue.

Corrective Action:
ISP repaired the affected infrastructure.

Preventive Action:
ISP preventive action to be reviewed if provided.

RCA Status:
Closed after confirmation and review.
~~~

This example demonstrates the structure only. Real RCA details must come from confirmed evidence.

## 21. Example - Unknown Root Cause

Sometimes service is restored but the exact cause is not immediately known.

~~~text
Incident:
Intermittent connectivity issue.

Current Status:
Service restored.

Root Cause:
Not confirmed.

Suspected Cause:
<Available technical observation>

Pending:
Further investigation / ISP RCA.

RCA Status:
Investigation
~~~

It is better to document "not confirmed" than to invent a root cause.

## 22. RCA and SLA

RCA and SLA measure different things.

### SLA

Focuses on service-management commitments and timelines.

### RCA

Focuses on why the incident occurred and how recurrence can be reduced.

An incident can therefore have:

~~~text
SLA Status: Within SLA
RCA: Required

or

SLA Status: Breached
RCA: Not Required
~~~

Whether RCA is required depends on the organization's process.

## 23. Shift Handover for RCA-Pending Tickets

Example:

~~~text
Ticket: Ticket-XXXX
Issue: Link Down
Service: <Service>

Service Status:
Restored

RCA Status:
Awaiting ISP

Last Follow-up:
YYYY-MM-DD HH:MM

Next Follow-up:
YYYY-MM-DD HH:MM

Pending Action:
Obtain final RCA from ISP.

Remarks:
Do not close RCA tracking until the required documentation is completed.
~~~

## 24. Common RCA Mistakes

### Confusing Symptom With Root Cause

"Link down" describes the symptom, not necessarily the cause.

### Guessing the Root Cause

Use only confirmed information.

### Missing Timeline

Without timestamps, incident reconstruction becomes difficult.

### Ignoring Preventive Action

Repeated incidents may continue if recurrence reduction is not considered.

### Closing RCA Without Evidence

The root cause should be supported by reliable information.

### Forgetting External RCA

ISP-related incidents may require follow-up after service restoration.

### Publishing Production Data

Never upload confidential incident information to a public repository.

## 25. RCA Tracking Checklist

~~~text
[ ] RCA requirement checked
[ ] Incident timeline prepared
[ ] Evidence collected
[ ] Symptoms documented
[ ] Root cause confirmed
[ ] Resolution documented
[ ] Corrective action recorded
[ ] Preventive action recorded where required
[ ] Owner identified
[ ] Due date recorded
[ ] ISP RCA followed up where applicable
[ ] RCA status updated
[ ] Shift handover updated if still pending
[ ] RCA closed according to process
~~~

## Key Takeaways

- RCA explains why an incident occurred.
- A symptom is not automatically the root cause.
- Resolution and root cause are different.
- Use evidence and confirmed information.
- Record a clear incident timeline.
- Track corrective and preventive actions.
- Follow up on pending ISP RCA after restoration.
- Recurring incidents should be linked to historical information where appropriate.
- SLA tracking and RCA tracking serve different purposes.
- Never guess or publicly expose production incident information.

## Related Topics

- NOC Ticketing Workflow
- Ticket Update and Closure Examples
- Ticket Priority and Severity
- Ticket SLA and Escalation Tracking
- NOC Ticket Shift Handover
- ISP Coordination Workflow
- Monitoring Logs and Documentation
- RCA
- NOC Glossary

## Author

Mohamed Ashik

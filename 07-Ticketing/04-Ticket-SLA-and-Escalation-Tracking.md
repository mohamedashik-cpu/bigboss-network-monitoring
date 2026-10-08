# Ticket SLA and Escalation Tracking

## Overview

SLA and escalation tracking help the NOC ensure that incidents receive the required attention within the organization's defined timelines.

This document explains how to track SLA-related milestones, ETR, follow-ups, overdue incidents, and escalation actions using generic examples.

> Important: SLA values and escalation thresholds are organization-specific. Never invent or publish internal SLA values, escalation contacts, customer details, production identifiers, or confidential information.

## Objectives

- Understand SLA tracking
- Track response and restoration milestones
- Monitor ETR against incident progress
- Identify overdue actions
- Perform timely escalation
- Document escalation history
- Maintain accurate ticket timelines

## 1. What Is an SLA?

SLA = **Service Level Agreement**.

An SLA is an agreed service commitment between a service provider and a customer or organization.

Depending on the environment, an SLA may define:

- Response time
- Acknowledgement time
- Update frequency
- Restoration target
- Resolution target
- Escalation requirements
- Availability commitments

Always use the approved SLA for the relevant service.

## 2. SLA Is Not the Same as ETR

### SLA

Defines the agreed service-management target or commitment.

### ETR

**ETR = Estimated Time of Restoration.**

ETR is the expected time at which the current incident is expected to be restored.

Example:

~~~text
SLA Target: <Approved organizational value>
Incident Start: YYYY-MM-DD HH:MM
Current ETR: YYYY-MM-DD HH:MM
~~~

An ETR can change during an incident. An SLA should be tracked according to the applicable agreement and process.

## 3. Common SLA Milestones

A ticket may have several important milestones:

~~~text
Incident Detected
      ↓
Ticket Created
      ↓
Acknowledgement
      ↓
Initial Response
      ↓
Investigation
      ↓
Updates / Follow-ups
      ↓
Restoration
      ↓
Resolution
      ↓
Closure
~~~

The exact milestones depend on the organization's process.

## 4. SLA Tracking Fields

A useful tracking record can contain:

~~~text
Ticket ID:
Priority:
Incident Start:
Ticket Created:
Acknowledgement:
Initial Response:
ISP Ticket:
Initial ETR:
Latest ETR:
Last Follow-up:
Next Follow-up:
Restoration Time:
Resolution Time:
Closure Time:
SLA Status:
Escalation Status:
~~~

Do not record fields that are not applicable.

## 5. SLA Status

A generic tracking model:

| Status | Meaning |
|---|---|
| Within SLA | Current activity is within the applicable target |
| At Risk | Target may be missed without action |
| Breached | Applicable SLA target has been exceeded |
| Not Applicable | SLA does not apply or is not being measured for this ticket |

Use the organization's official SLA calculation and status definitions where available.

## 6. Incident Timeline

Example:

~~~text
10:00 - Incident detected
10:05 - Ticket created
10:10 - Initial verification completed
10:15 - ISP contacted
10:18 - ISP ticket received
10:20 - ETR provided
11:00 - Follow-up completed
12:00 - ETR revised
13:15 - Escalation performed
14:00 - Restoration reported
14:05 - Restoration verified
14:30 - Stability monitoring completed
14:45 - Ticket resolved
~~~

A timestamped timeline makes SLA review easier.

## 7. ETR Tracking

When an ETR is received:

~~~text
Initial ETR: YYYY-MM-DD HH:MM
Source: ISP / Internal Team
Received Time: YYYY-MM-DD HH:MM
Status: Pending
~~~

If the ETR changes:

~~~text
Previous ETR: YYYY-MM-DD HH:MM
Revised ETR: YYYY-MM-DD HH:MM
Update Time: YYYY-MM-DD HH:MM
Reason: <Confirmed reason>
~~~

Never replace the history completely. Keep the previous ETR when the ticketing system supports history tracking.

## 8. Next Follow-up

Every open incident should have a clear next action.

Example:

~~~text
Current Status: ISP investigation
Latest ETR: HH:MM
Last Follow-up: HH:MM
Next Follow-up: HH:MM
Owner: NOC
~~~

A ticket without a next action can easily be missed during a busy shift.

## 9. SLA At Risk

An incident can be considered "at risk" when the available time is becoming limited and the required action has not yet been completed.

Generic action:

~~~text
Review current ticket status.
Confirm the remaining SLA time.
Contact the responsible team if required.
Request an updated ETR.
Escalate according to the approved process.
Document the action.
~~~

Do not wait until the SLA has already breached if the process requires proactive escalation.

## 10. SLA Breach

If an applicable SLA target is exceeded:

~~~text
YYYY-MM-DD HH:MM - Applicable SLA target has been exceeded.

Current Status: <Status>
Incident Start: YYYY-MM-DD HH:MM
Latest ETR: YYYY-MM-DD HH:MM

Responsible team / ISP contacted.
Escalation initiated according to the applicable process.
Revised ETR requested.
~~~

Record the actual confirmed times.

## 11. ETR Exceeded vs SLA Breached

These are not automatically the same.

### ETR Exceeded

The expected restoration time provided during the incident has passed.

### SLA Breached

The contractual or organizational SLA target has been exceeded.

Example:

~~~text
ETR: 15:00
SLA target: <Approved target>

15:00 passes
    ↓
ETR exceeded
    ↓
Request revised ETR / escalate
~~~

Whether the SLA is also breached depends on the approved SLA calculation.

## 12. Escalation Tracking

For every escalation, record:

~~~text
Escalation Time:
Ticket:
Priority:
Reason:
Escalated To:
Method:
Current Status:
Previous ETR:
Revised ETR:
Next Update:
Action Required:
~~~

Example:

~~~text
Escalation Time: YYYY-MM-DD HH:MM
Ticket: Ticket-XXXX
Priority: P2
Reason: Previous ETR exceeded
Escalated To: ISP Technical Team
Method: Approved escalation channel
Current Status: Service unavailable
Previous ETR: HH:MM
Revised ETR: HH:MM
Next Update: HH:MM
Action Required: Continue follow-up
~~~

## 13. Escalation Levels

A generic escalation structure may look like:

~~~text
Level 1
ISP / First-Line Support
      ↓
Level 2
ISP Technical Team
      ↓
Level 3
ISP Senior / Specialist Team
      ↓
Management Escalation
~~~

Actual levels and contacts depend on the organization's escalation matrix.

Do not bypass defined escalation levels unless the incident-management process allows it.

## 14. Functional Escalation

Functional escalation means moving an issue to a team with the required technical expertise.

Examples:

~~~text
NOC
 ↓
Network Team
 ↓
Firewall Team
 ↓
Infrastructure Team
~~~

The path depends on the incident.

## 15. Hierarchical Escalation

Hierarchical escalation involves notifying the appropriate management or escalation level.

Possible triggers:

- Critical business impact
- Major outage
- SLA risk
- SLA breach
- Extended service outage
- Repeated missed ETR
- Major operational risk

Follow the organization's approved communication hierarchy.

## 16. Repeated Missed ETR

If the ISP repeatedly provides ETRs that are not met:

~~~text
1. Record each ETR.
2. Record each missed ETR.
3. Request the latest technical status.
4. Request a revised ETR.
5. Escalate according to the escalation matrix.
6. Inform the relevant internal team when required.
7. Continue monitoring until restoration.
~~~

Example:

~~~text
Initial ETR: HH:MM
Missed
Revised ETR: HH:MM
Missed
Escalation: Completed
Current Status: Investigation ongoing
Next Update: HH:MM
~~~

Avoid emotional or blaming language.

## 17. SLA Tracking During Shift Handover

Open tickets with SLA risk should be clearly highlighted.

Example:

~~~text
Ticket: Ticket-XXXX
Priority: P2
Issue: Link Down
SLA Status: At Risk
Current Status: ISP Investigation
ISP Ticket: ISP-Ticket-XXXX
Latest ETR: HH:MM
Last Follow-up: HH:MM
Next Follow-up: HH:MM
Escalation: Yes
Pending Action: Follow up before the next SLA milestone
~~~

The next engineer should immediately understand the urgency.

## 18. SLA Dashboard / Spreadsheet Fields

For a simple internal tracking sheet, useful columns may include:

| Field | Purpose |
|---|---|
| Ticket ID | Internal ticket reference |
| Priority | P1/P2/P3/P4 |
| Service | Affected service |
| Issue | Incident type |
| Start Time | Incident start |
| Ticket Time | Ticket creation |
| ISP Ticket | External reference |
| Initial ETR | First ETR |
| Latest ETR | Current ETR |
| Last Follow-up | Latest communication |
| Next Follow-up | Next action time |
| Restoration Time | Service restoration |
| SLA Status | Current SLA state |
| Escalation | Escalation state |
| Closure Time | Ticket completion |

Only use fields permitted by the organization's data-handling policy.

## 19. Overdue Ticket Review

During periodic ticket review, identify:

~~~text
[ ] Tickets with no recent update
[ ] Tickets with overdue follow-up
[ ] Tickets with expired ETR
[ ] Tickets approaching SLA risk
[ ] Tickets requiring escalation
[ ] Restored tickets awaiting verification
[ ] Resolved tickets awaiting closure
~~~

This helps prevent open incidents from being forgotten.

## 20. Generic SLA Review Workflow

~~~text
Review Open Tickets
        ↓
Check Priority
        ↓
Check Incident Start Time
        ↓
Check SLA Milestone
        ↓
Check Latest ETR
        ↓
Check Last Follow-up
        ↓
Identify At-Risk / Overdue Tickets
        ↓
Take Required Action
        ↓
Escalate if Necessary
        ↓
Update Ticket
~~~

## 21. Example - P2 Incident

~~~text
Ticket: Ticket-XXXX
Priority: P2
Issue: P2P Link Down
Start Time: YYYY-MM-DD HH:MM

Current Status: ISP Investigation
ISP Ticket: ISP-Ticket-XXXX

Initial ETR: HH:MM
Latest ETR: HH:MM

Last Follow-up: HH:MM
Next Follow-up: HH:MM

SLA Status: At Risk
Escalation: In Progress
Pending Action: Obtain revised ETR and continue monitoring
~~~

This is an example format only. Actual SLA status must be calculated using the approved process.

## 22. Example - Restored but Under Monitoring

~~~text
Ticket: Ticket-XXXX
Priority: P2
Issue: Link Down

ISP Restoration: YYYY-MM-DD HH:MM
NOC Verification: YYYY-MM-DD HH:MM

Current Status: Monitoring
SLA Status: <According to approved process>

Monitoring Result:
Service reachable and relevant alerts cleared.

Next Action:
Continue stability monitoring and close according to process.
~~~

## 23. Common SLA Tracking Mistakes

### Ignoring the SLA Clock

Open tickets should be reviewed according to the defined process.

### Tracking Only ETR

ETR does not replace SLA tracking.

### Missing Next Follow-up

Every active incident should have a clear next action.

### Overwriting ETR History

Keep previous ETR information where the system/process supports it.

### Escalating Too Late

Use proactive escalation when an incident is approaching an SLA threshold.

### Inventing SLA Values

Never guess internal SLA targets.

### Incorrect Timestamps

Use actual confirmed times.

### Closing Before Verification

Restoration and SLA completion should be properly documented before closure.

## 24. SLA Tracking Checklist

~~~text
[ ] Priority confirmed
[ ] Incident start time recorded
[ ] Ticket creation time recorded
[ ] Applicable SLA identified
[ ] Current SLA status checked
[ ] Initial ETR recorded
[ ] Latest ETR recorded
[ ] Last follow-up recorded
[ ] Next follow-up scheduled
[ ] At-risk tickets identified
[ ] Overdue tickets identified
[ ] Escalation completed when required
[ ] Restoration verified
[ ] Final timeline documented
~~~

## 25. Generic SLA and Escalation Template

~~~text
Ticket: Ticket-XXXX
Priority: P1 / P2 / P3 / P4
Service: <Service>
Issue: <Issue>

Incident Start:
YYYY-MM-DD HH:MM

Ticket Created:
YYYY-MM-DD HH:MM

Applicable SLA:
<Approved SLA reference>

SLA Status:
Within SLA / At Risk / Breached / N/A

ISP Ticket:
ISP-Ticket-XXXX

Initial ETR:
YYYY-MM-DD HH:MM

Latest ETR:
YYYY-MM-DD HH:MM

Last Follow-up:
YYYY-MM-DD HH:MM

Next Follow-up:
YYYY-MM-DD HH:MM

Escalation:
Yes / No

Escalation Time:
YYYY-MM-DD HH:MM

Escalated To:
<Approved team/level>

Restoration Time:
YYYY-MM-DD HH:MM

Verification Time:
YYYY-MM-DD HH:MM

Final Status:
Resolved / Closed

Remarks:
<Confirmed final information>
~~~

## Key Takeaways

- SLA tracking is different from ETR tracking.
- Record important timestamps accurately.
- Every active incident should have a clear next follow-up.
- Identify SLA risk before the target is missed.
- Track every ETR change and escalation.
- Use the approved escalation matrix.
- ETR exceeded does not automatically mean SLA breached.
- Never invent SLA targets or escalation contacts.
- Keep handover notes clear for at-risk and overdue tickets.
- Verify restoration before final closure.

## Related Topics

- NOC Ticketing Workflow
- Ticket Update and Closure Examples
- Ticket Priority and Severity
- ISP Coordination Workflow
- ISP Call and Email Communication
- Monitoring Logs and Documentation
- RCA
- NOC Glossary

## Author

Mohamed Ashik

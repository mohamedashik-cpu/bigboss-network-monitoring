# NOC Ticketing Workflow

## Overview

Ticketing is used to record, track, communicate, and close network incidents in a structured way.

A good NOC ticket should allow another engineer to understand:

- What happened
- When it happened
- What was verified
- What action was taken
- Who was contacted
- Current status
- Expected next action
- How and when the service was restored

> Important: This is a generic learning guide. Never publish real customer data, internal ticket IDs, circuit IDs, production IP addresses, credentials, or confidential company information.

## Objectives

- Understand the NOC ticket lifecycle
- Create clear incident descriptions
- Record troubleshooting actions
- Track ISP references and ETR
- Maintain accurate ticket status
- Escalate overdue incidents
- Document restoration and closure
- Prepare useful shift handover information

## Ticket Lifecycle

A typical NOC ticket follows:

~~~text
Incident Detected
      ↓
Verify Incident
      ↓
Create Ticket
      ↓
Initial Investigation
      ↓
Internal / ISP Coordination
      ↓
Follow-up
      ↓
Escalation if Required
      ↓
Service Restored
      ↓
Verify Stability
      ↓
Update Ticket
      ↓
Close Ticket
~~~

## 1. When to Create a Ticket

Create a ticket according to the organization's incident-management process when an issue requires tracking or action.

Common examples:

- Link Down
- Link Flapping
- Packet Loss
- High Latency
- Device Unreachable
- Interface Down
- ISP Service Issue
- Recurring Connectivity Issue
- Other monitored network incidents

Before creating a ticket, verify that the alert represents a real or actionable incident.

## 2. Information to Collect Before Ticket Creation

Collect the information available from authorized monitoring and troubleshooting sources.

### Basic Information

~~~text
Date:
Detection Time:
Service Type:
Issue:
Current Status:
Affected Device/Service:
Monitoring Alert:
Initial Verification:
~~~

### If ISP Coordination Is Required

~~~text
ISP:
ISP Ticket/Reference:
Time Reported:
Current ISP Status:
ETR:
Next Follow-up:
~~~

Do not delay a critical incident unnecessarily just because every optional field is not available.

## 3. Ticket Title

A ticket title should be short and descriptive.

Examples:

~~~text
P2P Link Down - Service XXXX
ILL Link Down - Service XXXX
Network Link Flapping - Service XXXX
High Packet Loss - Service XXXX
High Latency - Service XXXX
Device Unreachable - Device XXXX
~~~

Avoid vague titles such as:

~~~text
Network Issue
Problem
Check This
Internet Not Working
~~~

The title should help the next engineer understand the incident immediately.

## 4. Ticket Description

A useful description contains:

~~~text
Issue:
Detection Time:
Current Status:
Verification:
Action Taken:
External Coordination:
Next Action:
~~~

Generic example:

~~~text
Issue: P2P link down
Detection Time: YYYY-MM-DD HH:MM
Current Status: Service unavailable
Verification: Monitoring alert verified and basic interface/reachability checks completed
Action Taken: ISP contacted and incident reported
External Coordination: ISP ticket ISP-Ticket-XXXX
Next Action: Follow up with ISP at HH:MM
~~~

## 5. Ticket Priority and Severity

Priority and severity should follow the organization's defined process.

A generic approach:

| Priority | Typical Meaning | Example |
|---|---|---|
| P1 | Critical / major impact | Major service outage |
| P2 | High impact | Important service unavailable |
| P3 | Moderate impact | Limited service degradation |
| P4 | Low impact / request | Minor or informational issue |

Do not assign priority based only on personal judgment.

Consider:

- Business impact
- Number of affected services/users
- Service criticality
- Duration
- Redundancy availability
- Organization's SLA/process

## 6. Ticket Status

Common ticket statuses include:

| Status | Meaning |
|---|---|
| New | Ticket created and awaiting action |
| Assigned | Engineer/team assigned |
| In Progress | Investigation is ongoing |
| Waiting for ISP | Awaiting ISP action/update |
| Waiting for User | Awaiting required user-side information |
| Monitoring | Service restored but stability is being observed |
| Resolved | Technical issue resolved |
| Closed | Ticket closure completed |

The exact names can differ between organizations.

## 7. Initial Ticket Update

The first update should explain what was detected and what has been done.

Example:

~~~text
YYYY-MM-DD HH:MM - Monitoring alert received for the affected service.

YYYY-MM-DD HH:MM - Alert verified. Basic reachability and interface checks completed.

YYYY-MM-DD HH:MM - ISP contacted and incident reported.

ISP Ticket: ISP-Ticket-XXXX
ETR: HH:MM
Next Follow-up: HH:MM
~~~

Use timestamps consistently.

## 8. Action Log

Every important action should be recorded chronologically.

Example:

~~~text
10:05 - Link-down alert detected.
10:08 - Alert verified.
10:12 - Basic interface checks completed.
10:15 - ISP contacted.
10:17 - ISP ticket received.
10:20 - Initial ETR received.
11:00 - Follow-up completed.
11:30 - ETR revised.
12:10 - ISP reported restoration.
12:15 - Service verified from monitoring.
12:45 - Stability monitoring completed.
~~~

This creates a clear incident timeline.

## 9. ISP Ticket Tracking

When an external ISP ticket is created, record:

~~~text
ISP:
ISP Ticket:
Reported Time:
Issue:
Current Status:
ETR:
Last Follow-up:
Next Follow-up:
Escalation:
~~~

Do not confuse:

- Internal NOC ticket
- ISP ticket
- Customer/service reference

Each identifier should be recorded in the correct field.

## 10. ETR Tracking

ETR = Estimated Time of Restoration.

When an ISP provides an ETR:

1. Record the ETR.
2. Continue monitoring the incident.
3. Follow up before or around the expected time according to the process.
4. If the ETR is exceeded, request a revised ETR.
5. Escalate according to the escalation process when required.

Example:

~~~text
Initial ETR: HH:MM
ETR Status: Pending
Revised ETR: HH:MM
Reason/Update: ISP investigation ongoing
~~~

Never mark an incident resolved only because the ETR has passed.

## 11. ETA vs ETR

### ETA

**ETA = Estimated Time of Arrival**

Usually refers to when a person, engineer, team, or resource is expected to arrive.

### ETR

**ETR = Estimated Time of Restoration**

Refers to the expected time when the affected service will be restored.

Example:

~~~text
Engineer ETA: 14:00
Service ETR: 15:30
~~~

These terms should not be treated as interchangeable.

## 12. Follow-up Update

Example:

~~~text
YYYY-MM-DD HH:MM - Follow-up completed with ISP.

Current Status: Investigation ongoing
ISP Update: Technical team working on the issue
ETR: HH:MM
Next Follow-up: HH:MM
~~~

Keep updates factual.

Avoid writing:

~~~text
ISP is very slow.
They are not responding properly.
They don't know the issue.
~~~

Instead record objective information:

~~~text
No technical update received during the follow-up.
Revised ETR requested.
Escalation requested as per process.
~~~

## 13. ETR Exceeded Update

Example:

~~~text
YYYY-MM-DD HH:MM - Previous ETR has been exceeded.

Service is still showing the reported issue on monitoring.

ISP contacted for the latest status and revised ETR.
Escalation requested according to the applicable process.
~~~

## 14. Escalation Update

Record:

~~~text
Escalation Time:
Escalated To:
Reason:
Current Status:
Revised ETR:
Next Follow-up:
~~~

Example:

~~~text
Escalation Time: HH:MM
Escalated To: ISP Technical Team
Reason: Previous ETR exceeded
Current Status: Service unavailable
Revised ETR: HH:MM
Next Follow-up: HH:MM
~~~

## 15. Restoration Update

Do not close the ticket immediately when the ISP reports restoration.

First record:

~~~text
YYYY-MM-DD HH:MM - ISP reported service restoration.

NOC verification initiated.
~~~

After verification:

~~~text
YYYY-MM-DD HH:MM - Service verified as reachable.

Monitoring alert cleared and service status returned to normal.
Stability monitoring initiated.
~~~

## 16. Monitoring After Restoration

Depending on the organization's process, continue monitoring for stability.

Check relevant indicators such as:

- Service reachability
- Interface status
- Packet loss
- Latency
- Repeated flapping
- Monitoring alerts
- Interface errors where applicable

If the issue returns, reopen or continue the incident according to the organization's process.

## 17. Ticket Resolution

Before marking a ticket resolved, confirm:

- Service is restored
- Monitoring status is normal
- Relevant alerts are cleared
- Required verification is completed
- ISP update is recorded
- Incident timeline is complete
- Any required RCA information is captured
- No further action is pending

Generic resolution note:

~~~text
Service restored and verified from monitoring.

Relevant alerts have cleared and the service is currently stable.

Incident timeline and ISP updates have been documented.
~~~

## 18. Ticket Closure

Closure should follow the organization's process.

Generic closure checklist:

~~~text
[ ] Issue verified
[ ] Troubleshooting documented
[ ] ISP ticket/reference recorded
[ ] ETR updates recorded
[ ] Restoration verified
[ ] Stability checked
[ ] Final remarks added
[ ] Required RCA linked/recorded
[ ] No pending action
[ ] Ticket closed according to process
~~~

## 19. Reopened Incident

If the same issue returns after closure:

~~~text
YYYY-MM-DD HH:MM - Service issue recurred after previous restoration.

Current status: <Status>
Previous ticket: Ticket-XXXX
New verification: <Verification>
Action taken: <Action>
~~~

Determine whether the organization requires reopening the previous ticket or creating a new incident.

## 20. Shift Handover Information

For an open ticket, handover should contain:

~~~text
Ticket:
Service:
Issue:
Start Time:
Current Status:
Actions Completed:
ISP Ticket:
Latest ISP Update:
ETR:
Last Follow-up:
Next Follow-up:
Escalation:
Pending Action:
~~~

Example:

~~~text
Ticket: Ticket-XXXX
Service: P2P-Service-XXXX
Issue: Link Down
Start Time: YYYY-MM-DD HH:MM
Current Status: ISP Investigation
Actions Completed: Basic checks and ISP coordination
ISP Ticket: ISP-Ticket-XXXX
Latest ISP Update: Technical team investigating
ETR: HH:MM
Last Follow-up: HH:MM
Next Follow-up: HH:MM
Escalation: Yes
Pending Action: Follow up with ISP
~~~

## 21. Good vs Poor Ticket Updates

### Poor

~~~text
Link down. ISP informed. Waiting.
~~~

Problem:

- No timestamp
- No verification
- No ticket reference
- No ETR
- No next action

### Better

~~~text
YYYY-MM-DD HH:MM - Link-down alert verified.

Basic interface and reachability checks completed.

ISP contacted and ticket ISP-Ticket-XXXX received.

Current Status: ISP investigation
ETR: HH:MM
Next Follow-up: HH:MM
~~~

## 22. Common Ticketing Mistakes

### Missing Timestamps

Always record important actions with time.

### No Clear Next Action

Every open ticket should have a known next step.

### Incorrect ETR

Record the latest confirmed ETR rather than an assumption.

### Missing ISP Reference

Record the ISP ticket/reference when available.

### Closing Too Early

Verify restoration before closure.

### Copying the Same Update Repeatedly

Each update should add meaningful information.

### Mixing Facts and Assumptions

Record what was observed or confirmed.

### Sharing Confidential Information

Use approved systems for real production information.

## 23. Generic Ticket Template

~~~text
Ticket ID: Ticket-XXXX
Date: YYYY-MM-DD

Service Type: P2P / ILL / Network Device
Issue: Link Down / Flapping / Packet Loss / High Latency / Unreachable

Detection Time: YYYY-MM-DD HH:MM
Current Status: <Status>

Initial Verification:
<Action / checks completed>

Action Taken:
<Action>

ISP:
<Generic ISP>

ISP Ticket:
ISP-Ticket-XXXX

Latest ISP Update:
<Update>

ETR:
HH:MM

Last Follow-up:
HH:MM

Next Follow-up:
HH:MM

Escalation:
<Yes / No>

Restoration Time:
YYYY-MM-DD HH:MM

Restoration Verification:
<Verification>

Final Remarks:
<Closure information>
~~~

## 24. Ticket Quality Checklist

Before updating or closing a ticket, ask:

- Is the issue clearly described?
- Is the detection time recorded?
- Is the current status accurate?
- Are troubleshooting actions documented?
- Is the ISP ticket recorded if applicable?
- Is the latest ETR recorded?
- Is the next follow-up clear?
- Is escalation documented?
- Is restoration verified?
- Is the final update understandable to another engineer?
- Has confidential information been kept out of public documentation?

## Key Takeaways

- A ticket is the incident's operational history.
- Record facts chronologically.
- Use timestamps for important actions.
- Track internal and ISP references separately.
- Track ETR and next follow-up carefully.
- Escalate overdue incidents according to process.
- Verify restoration before resolution or closure.
- Make shift handover information actionable.
- Clear documentation helps the next engineer continue the incident without repeating work.

## Related Topics

- ISP Coordination Workflow
- ISP Call and Email Communication
- P2P Monitoring and Troubleshooting
- ILL Monitoring and Troubleshooting
- Monitoring Logs and Documentation
- RCA
- Shift Handover
- NOC Glossary

## Author

Mohamed Ashik

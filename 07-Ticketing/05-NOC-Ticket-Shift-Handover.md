# NOC Ticket Shift Handover

## Overview

Shift handover ensures that open incidents and pending actions continue smoothly when one NOC engineer or shift team hands work over to another.

A good handover should allow the incoming engineer to understand the current situation without repeating completed checks unnecessarily.

> Important: This is a generic learning guide. Never publish real customer information, production IP addresses, circuit IDs, internal ticket IDs, credentials, contact details, or confidential company information.

## Objectives

- Understand the purpose of shift handover
- Identify tickets that require handover
- Record pending actions clearly
- Track ISP follow-ups and ETR
- Highlight SLA-risk incidents
- Communicate restoration and monitoring status
- Prevent missed follow-ups

## 1. Why Shift Handover Matters

NOC operations may run continuously across multiple shifts.

Without a proper handover:

- Follow-ups may be missed
- ETR may be forgotten
- The same troubleshooting may be repeated
- Tickets may remain without updates
- SLA risk may increase
- Restored services may not be verified
- Important escalations may be overlooked

A good handover provides continuity.

## 2. What Should Be Handed Over?

Not every completed ticket needs a detailed handover.

Focus on:

- Open incidents
- Tickets waiting for ISP
- Tickets waiting for internal teams
- SLA-risk tickets
- Missed ETR tickets
- Escalated incidents
- Recurring issues
- Recently restored services under observation
- Scheduled follow-ups
- Any other pending action

## 3. Basic Handover Flow

~~~text
Review Open Tickets
       ↓
Check Current Status
       ↓
Check Last Update
       ↓
Check ETR / SLA
       ↓
Identify Pending Actions
       ↓
Update Handover Notes
       ↓
Brief Incoming Shift
       ↓
Confirm Critical Items
~~~

## 4. Open Ticket Handover Template

~~~text
Ticket: Ticket-XXXX
Priority: P1 / P2 / P3 / P4
Service: <Service>
Issue: <Issue>
Start Time: YYYY-MM-DD HH:MM

Current Status:
<Current status>

Actions Completed:
- <Action>
- <Action>

ISP / Internal Reference:
<Reference>

Latest Update:
<Confirmed update>

ETR:
YYYY-MM-DD HH:MM

Last Follow-up:
YYYY-MM-DD HH:MM

Next Follow-up:
YYYY-MM-DD HH:MM

SLA Status:
Within SLA / At Risk / Breached / N/A

Escalation:
Yes / No

Pending Action:
<Next action>

Remarks:
<Important information>
~~~

## 5. ISP-Pending Ticket

Example:

~~~text
Ticket: Ticket-XXXX
Issue: P2P Link Down
Current Status: Waiting for ISP

ISP Ticket: ISP-Ticket-XXXX
Latest ISP Update: Technical team investigating
ETR: HH:MM
Last Follow-up: HH:MM
Next Follow-up: HH:MM

Pending Action:
Follow up with ISP at the scheduled time and update the ticket.

Escalation:
No / Yes
~~~

## 6. ETR Exceeded Ticket

~~~text
Ticket: Ticket-XXXX
Priority: P2
Issue: ILL Link Down
Current Status: Service unavailable

Previous ETR: HH:MM
ETR Status: Exceeded

Latest Action:
ISP contacted for revised ETR.

Escalation:
Initiated according to process

Next Follow-up:
HH:MM

Pending Action:
Obtain revised ETR and continue escalation if required.
~~~

Tickets with an exceeded ETR should be clearly visible to the incoming shift.

## 7. SLA-Risk Ticket

~~~text
Ticket: Ticket-XXXX
Priority: P2
Issue: <Issue>
SLA Status: At Risk

Current Status:
<Status>

Last Action:
<Action>

Next Follow-up:
HH:MM

Pending Action:
<Required action>

Escalation:
<Status>
~~~

Do not hide SLA-risk tickets inside a large general handover list.

## 8. Escalated Ticket

~~~text
Ticket: Ticket-XXXX
Priority: P1 / P2
Issue: <Issue>

Current Status:
<Status>

Escalation Time:
YYYY-MM-DD HH:MM

Escalated To:
<Approved team / escalation level>

Reason:
<Confirmed reason>

Latest Update:
<Update>

Revised ETR:
YYYY-MM-DD HH:MM

Next Follow-up:
YYYY-MM-DD HH:MM

Pending Action:
<Action>
~~~

Use the approved escalation matrix.

## 9. Recently Restored Ticket

A recently restored service may require continued observation.

~~~text
Ticket: Ticket-XXXX
Issue: Link Flapping

Restoration Time:
YYYY-MM-DD HH:MM

NOC Verification:
YYYY-MM-DD HH:MM

Current Status:
Monitoring

Latest Monitoring Result:
Service reachable and no new flapping alert observed.

Pending Action:
Continue stability monitoring according to process.
~~~

Do not mark a service permanently stable based on a very short observation period unless the organization's process says so.

## 10. Recurring Incident Handover

~~~text
Ticket: Ticket-XXXX
Issue: Recurring Link Flapping

Current Status:
Intermittent / recurring

Previous Occurrences:
<Reference available in approved system>

Actions Completed:
<Actions>

Latest Update:
<Confirmed update>

Pending Action:
Continue monitoring and coordinate with the responsible team.

Remarks:
Track recurrence and provide history if escalation or RCA is required.
~~~

## 11. Handover for Multiple Open Tickets

A quick summary can be useful:

| Ticket | Priority | Issue | Status | ETR | Next Action |
|---|---|---|---|---|---|
| Ticket-XXXX | P1 | Major outage | Escalated | HH:MM | Follow up |
| Ticket-XXXX | P2 | Link Down | ISP investigation | HH:MM | ISP follow-up |
| Ticket-XXXX | P3 | High Latency | Monitoring | N/A | Observe |

Use the organization's approved system for actual ticket data.

## 12. Handover Priority Order

When briefing the incoming shift, discuss in roughly this order:

1. Critical / P1 incidents
2. SLA-risk incidents
3. P2 incidents
4. Missed ETR incidents
5. Escalated tickets
6. Tickets requiring immediate follow-up
7. Recently restored services
8. Lower-priority pending items

The exact order may differ according to the organization's process.

## 13. What the Incoming Shift Should Confirm

For each important ticket, confirm:

~~~text
What is the issue?
When did it start?
What has already been checked?
Who is currently working on it?
What is the latest status?
What is the ETR?
When is the next follow-up?
Has it been escalated?
What action is pending?
~~~

If these questions can be answered, the handover is usually actionable.

## 14. Handover Communication

A simple verbal handover:

~~~text
There are three open tickets.

The first is a P1 incident and has been escalated. The next follow-up is at HH:MM.

The second is a P2 P2P link-down issue. The ISP is investigating and the current ETR is HH:MM.

The third is a restored link-flapping incident. The service is under stability monitoring.

The pending actions are documented in the ticket notes.
~~~

Keep verbal handover short and refer to the approved ticketing system for full details.

## 15. Handover Email / Message Structure

A generic internal handover can follow:

~~~text
Subject: NOC Shift Handover - YYYY-MM-DD

Hello Team,

Please find the current open and pending incidents for shift handover.

1. Ticket: Ticket-XXXX
Priority: P2
Issue: <Issue>
Status: <Status>
ETR: <ETR>
Next Follow-up: <Time>
Pending Action: <Action>

2. Ticket: Ticket-XXXX
Priority: P3
Issue: <Issue>
Status: <Status>
Next Follow-up: <Time>
Pending Action: <Action>

Please continue monitoring and follow up on the pending actions.

Regards,
NOC Team
~~~

Use the organization's approved communication channel.

## 16. Start-of-Shift Checklist for Incoming Engineer

~~~text
[ ] Review handover notes
[ ] Review all open tickets
[ ] Identify P1/P2 incidents
[ ] Check SLA-risk tickets
[ ] Check missed ETRs
[ ] Check scheduled ISP follow-ups
[ ] Check escalated incidents
[ ] Check recently restored services
[ ] Review monitoring alerts
[ ] Confirm pending actions
~~~

## 17. End-of-Shift Checklist for Outgoing Engineer

~~~text
[ ] Review all tickets worked during the shift
[ ] Update current status
[ ] Record latest ISP/internal updates
[ ] Record latest ETR
[ ] Record last and next follow-up
[ ] Record escalation status
[ ] Verify restoration where applicable
[ ] Highlight SLA-risk tickets
[ ] Highlight missed ETRs
[ ] Update handover notes
[ ] Brief incoming shift on critical incidents
~~~

## 18. Do Not Hand Over Like This

Poor handover:

~~~text
Several tickets are open. Check them.
~~~

Problems:

- No ticket references
- No priorities
- No status
- No ETR
- No pending actions
- No ownership information

Better:

~~~text
Ticket-XXXX - P2 - P2P Link Down
Current Status: ISP investigation
Latest ETR: HH:MM
Next Follow-up: HH:MM
Pending Action: Follow up with ISP and update ticket
Escalation: No
~~~

## 19. Avoid Repeating Completed Troubleshooting

A handover should tell the incoming engineer what has already been done.

Example:

~~~text
Completed:
- Alert verified
- Reachability checked
- Interface status checked
- ISP contacted
- ISP ticket created

Pending:
- ISP follow-up at HH:MM
- Obtain revised ETR if required
~~~

This prevents unnecessary repetition.

## 20. Handover for Monitoring-Only Items

Not every observation requires an incident ticket.

Example:

~~~text
Observation: Intermittent latency alert
Current Status: Normal
Action: Continued monitoring
Pending: Observe for recurrence
~~~

Only create or maintain a ticket according to the applicable process.

## 21. Handover and Confidentiality

Handover information should be shared only through approved company channels.

Do not place confidential production information into:

- Public GitHub repositories
- Personal notes shared publicly
- Unapproved messaging platforms
- Screenshots posted online
- Personal cloud storage

For this learning repository, use sanitized placeholders such as:

~~~text
Ticket-XXXX
ISP-Ticket-XXXX
P2P-Service-XXXX
ILL-Service-XXXX
Device-XXXX
X.X.X.X
~~~

## 22. Handover Quality Checklist

A good handover should answer:

~~~text
[ ] What happened?
[ ] When did it happen?
[ ] What was verified?
[ ] What action was taken?
[ ] Who is handling it?
[ ] What is the current status?
[ ] What is the latest ETR?
[ ] When is the next follow-up?
[ ] Is escalation required?
[ ] What remains pending?
~~~

## 23. Complete Handover Template

~~~text
NOC SHIFT HANDOVER
Date: YYYY-MM-DD
Outgoing Shift: <Shift>
Incoming Shift: <Shift>

CRITICAL INCIDENTS
------------------
Ticket: Ticket-XXXX
Priority: P1
Issue: <Issue>
Status: <Status>
Start Time: YYYY-MM-DD HH:MM
Actions Completed: <Actions>
Latest Update: <Update>
ETR: YYYY-MM-DD HH:MM
SLA Status: <Status>
Escalation: <Status>
Next Follow-up: YYYY-MM-DD HH:MM
Pending Action: <Action>

HIGH PRIORITY INCIDENTS
-----------------------
Ticket: Ticket-XXXX
Priority: P2
Issue: <Issue>
Status: <Status>
ISP Ticket: ISP-Ticket-XXXX
Latest ETR: YYYY-MM-DD HH:MM
Next Follow-up: YYYY-MM-DD HH:MM
Pending Action: <Action>

MONITORING ITEMS
----------------
Service: <Service>
Issue/Observation: <Observation>
Current Status: <Status>
Action: <Action>
Pending: <Action>

RECENTLY RESTORED
-----------------
Ticket: Ticket-XXXX
Issue: <Issue>
Restoration Time: YYYY-MM-DD HH:MM
Verification Time: YYYY-MM-DD HH:MM
Monitoring Status: <Status>
Pending Action: <Action>

GENERAL NOTES
-------------
<Important non-confidential information>
~~~

## Key Takeaways

- Shift handover is a continuity process, not just a list of tickets.
- Highlight P1/P2, SLA-risk, missed ETR, escalated, and pending incidents.
- Record the latest status and the next action.
- Always record the latest ETR and follow-up time.
- Mention completed troubleshooting so the next engineer does not repeat it unnecessarily.
- Recently restored services may need continued monitoring.
- Keep handover information factual and actionable.
- Use approved company systems and communication channels.
- Never share confidential production information publicly.

## Related Topics

- NOC Ticketing Workflow
- Ticket Update and Closure Examples
- Ticket Priority and Severity
- Ticket SLA and Escalation Tracking
- ISP Coordination Workflow
- Monitoring Logs and Documentation
- RCA
- NOC Glossary

## Author

Mohamed Ashik

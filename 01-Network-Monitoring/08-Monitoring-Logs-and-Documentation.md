# Monitoring Logs and Documentation

## Overview

Monitoring logs and documentation help NOC teams maintain a clear record of alerts, incidents, actions, follow-ups, and restoration status. Good documentation makes troubleshooting easier, supports shift handover, and provides a reliable history for recurring issues.

> **Important:** This document contains only generic and sanitized learning material. Do not store customer information, real production IP addresses, circuit IDs, ticket numbers, credentials, screenshots, or company-confidential information in this repository.

## Objectives

- Understand the purpose of NOC monitoring logs
- Record alerts and incidents consistently
- Maintain accurate timestamps
- Document troubleshooting actions
- Track ISP/team follow-ups
- Record restoration and closure details
- Support clear shift handovers
- Identify recurring incidents from historical records

## 1. What Is a Monitoring Log?

A monitoring log is a structured record of events observed during network monitoring.

A log may contain:

- Date
- Time
- Device or service
- Alert/event
- Status
- Verification
- Action taken
- Ticket/reference
- External update
- Current status
- Next action

A monitoring log should contain factual information rather than assumptions.

## 2. Why Documentation Matters

Proper documentation helps to:

- Maintain incident history
- Avoid repeated troubleshooting
- Prevent missed follow-ups
- Improve shift handover
- Track ISP responses
- Identify recurring problems
- Support RCA preparation
- Improve operational consistency

## 3. Basic Monitoring Log Format

A simple monitoring log can use the following structure:

| Time | Device/Service | Alert | Status | Verification | Action | Reference | Next Action |
|---|---|---|---|---|---|---|---|
| HH:MM | Device-A | Link Down | Active | Interface checked | Escalated | Ticket-XXXX | Follow up |
| HH:MM | Device-B | Packet Loss | Monitoring | Reachability checked | Observed | Ticket-YYYY | Continue monitoring |

Use generic placeholders when documenting examples for learning.

## 4. Alert Log

An alert log focuses on monitoring events.

### Recommended Fields

- Alert time
- Device/service
- Interface
- Alert type
- Severity
- Current status
- Cleared time
- Duration
- Action taken

### Generic Example

~~~text
Alert Time: HH:MM
Device: Device-A
Interface: Interface-X
Alert: Link Down
Severity: High
Status: Active
Action: Verification performed
Reference: Ticket-XXXX
~~~

## 5. Incident Log

An incident log provides more detail than a basic alert log.

### Recommended Fields

~~~text
Incident:
Generic-ISP Link Issue

Detected:
HH:MM

Initial Status:
Down

Verification:
Device and interface checked

Action:
Ticket raised and escalated

Current Status:
Under Investigation

Latest Update:
Awaiting responsible team update

Next Action:
Follow up and continue monitoring
~~~

## 6. Timestamp Discipline

Accurate timestamps are important in NOC documentation.

Record important events such as:

- Alert received
- Verification completed
- Ticket raised
- ISP/team contacted
- Update received
- ETA/ETR provided
- Service restored
- Restoration verified
- Ticket closed

### Generic Timeline

~~~text
10:05  Alert received
10:08  Initial verification completed
10:12  Ticket raised
10:20  ISP/team contacted
10:35  Update received
11:10  Service restored
11:15  Restoration verified
11:30  Monitoring stable
11:35  Incident closed
~~~

This timeline can later help during RCA or incident review.

## 7. Status Tracking

Use clear status descriptions.

Common examples:

- New
- Under Investigation
- Escalated
- Awaiting Update
- Monitoring
- Restored
- Resolved
- Closed
- Handed Over

Avoid unclear notes such as:

~~~text
Checking
Something wrong
Maybe ISP
Issue fixed
~~~

Prefer specific factual statements.

Example:

~~~text
Interface-X is currently Down.
Device reachability check failed.
Issue escalated to responsible ISP/team.
Awaiting restoration update.
~~~

## 8. Action Documentation

Record what was actually done.

Good documentation:

~~~text
Device reachability checked.
Interface status checked.
Monitoring history reviewed.
Ticket-XXXX raised.
Responsible ISP/team notified.
~~~

Avoid writing actions that were not performed.

## 9. ISP Follow-up Log

When an issue is escalated to an ISP or external team, maintain the follow-up history.

### Generic Format

| Time | Reference | Update | Current Status | Next Action |
|---|---|---|---|---|
| HH:MM | ISP-Ticket-XXXX | Issue reported | Open | Await response |
| HH:MM | ISP-Ticket-XXXX | Team acknowledged | Investigating | Await update |
| HH:MM | ISP-Ticket-XXXX | Restoration reported | Restored | Verify |
| HH:MM | ISP-Ticket-XXXX | Monitoring stable | Resolved | Close |

This prevents repeated calls or messages without knowing the previous status.

## 10. ETA and ETR Documentation

When a responsible team provides an expected update or restoration time, record it clearly.

### Example

~~~text
ETA: HH:MM
Purpose: Next status update expected

ETR: HH:MM
Purpose: Expected restoration time
~~~

ETA and ETR should be recorded as provided by the responsible team. Do not create or guess an ETA/ETR.

## 11. Restoration Log

After service restoration, record the verification details.

### Generic Format

~~~text
Restoration Reported: HH:MM
Device Status: Up
Interface Status: Up
Reachability: Successful
Packet Loss: Normal/Checked
Latency: Normal/Checked
Monitoring: Stable
Final Status: Resolved
~~~

The exact checks depend on the incident type and approved procedure.

## 12. Recurring Incident Tracking

Historical logs can help identify repeated problems.

Example:

~~~text
Date 1 → Link Down
Date 2 → Link Flapping
Date 3 → Link Down
Date 4 → Link Flapping
~~~

Repeated events may justify additional investigation or escalation.

Useful fields:

- Number of occurrences
- Date/time pattern
- Duration
- Affected interface
- Related ticket references
- ISP/team responses
- Previous troubleshooting
- RCA availability

## 13. Shift Handover Documentation

A good handover should allow the next engineer to continue work without repeating the entire investigation.

### Handover Format

~~~text
Incident:
Generic-ISP Link Issue

Detected:
HH:MM

Current Status:
Under Investigation

Reference:
Ticket-XXXX

Actions Completed:
Device and interface checks completed.

Latest Update:
Responsible team acknowledged the issue.

Pending Action:
Await next update.

Next Shift:
Continue monitoring and follow up.
~~~

## 14. Daily Monitoring Summary

At the end of a shift, a short summary can capture important activities.

### Generic Format

~~~text
Daily Monitoring Summary

Date:
YYYY-MM-DD

Alerts Handled:
- Device Down
- Link Down
- Link Flapping

Tickets Updated:
- Ticket-XXXX
- Ticket-YYYY

ISP Follow-ups:
- Generic-ISP-A
- Generic-ISP-B

Restored Services:
- Generic-Service-A

Pending Incidents:
- Ticket-ZZZZ

Handover:
Pending incidents handed over to next shift.
~~~

## 15. Documentation Quality Checklist

Before saving or sending an incident update, check:

- [ ] Date/time is clear
- [ ] Device/service is identified
- [ ] Alert type is mentioned
- [ ] Current status is clear
- [ ] Verification steps are documented
- [ ] Actions taken are factual
- [ ] Ticket/reference is recorded
- [ ] Latest external update is included
- [ ] Next action is clear
- [ ] Sensitive information is removed

## 16. Good vs Poor Documentation

### Poor

~~~text
Link problem.
Called ISP.
Waiting.
~~~

### Better

~~~text
Generic-ISP link-down alert verified at HH:MM.
Device and interface status checked.
Ticket-XXXX raised and escalated to the responsible ISP/team.
Current status: Under Investigation.
Next action: Follow up for the next update.
~~~

The second format provides enough context for another engineer to understand the incident.

## 17. Monitoring Log Template

Use this reusable structure for learning:

~~~text
Date:
Time:
Device/Service:
Interface:
Alert:
Severity:
Status:

Verification:
- 

Troubleshooting:
- 

Action Taken:
- 

Ticket/Reference:
- 

ISP/Team Update:
- 

ETA/ETR:
- 

Restoration:
- 

Current Status:
- 

Next Action:
- 
~~~

## 18. Incident Timeline Template

For more detailed incidents:

~~~text
[HH:MM] Alert detected
[HH:MM] Alert verified
[HH:MM] Initial troubleshooting completed
[HH:MM] Ticket raised
[HH:MM] ISP/team contacted
[HH:MM] Update received
[HH:MM] Restoration reported
[HH:MM] Restoration verified
[HH:MM] Monitoring stable
[HH:MM] Incident closed
~~~

## Important NOC Practices

- Record events as they happen whenever possible.
- Use accurate timestamps.
- Document facts, not assumptions.
- Record every important follow-up.
- Keep ticket references consistent.
- Record ETA/ETR exactly as provided.
- Document restoration verification.
- Make handover notes actionable.
- Use historical logs to identify recurring issues.
- Never expose confidential production information.

## Confidentiality Guidelines

Never upload:

- Customer names
- Real production IP addresses
- Circuit IDs
- Ticket IDs or numbers
- Phone numbers
- Email addresses
- Credentials or passwords
- Monitoring screenshots containing real data
- Internal topology
- Firewall screenshots
- Proprietary configurations
- Company-confidential information

Use sanitized placeholders:

~~~text
Customer-Site-A
Device-A
Interface-X
X.X.X.X
Generic-ISP
Ticket-XXXX
ISP-Ticket-XXXX
~~~

## Key Takeaways

- Monitoring logs provide an operational history of network events.
- Accurate timestamps make incident timelines easier to understand.
- Clear documentation improves troubleshooting and handover.
- ISP follow-up logs prevent missed updates.
- Restoration should include verification details.
- Recurring incidents can be identified through historical records.
- Good documentation should be factual, concise, and actionable.

## Related Topics

- 05-Basic-Monitoring-Workflow.md
- 06-Alert-Verification-and-Classification.md
- 07-Monitoring-Checklist.md
- 02-Troubleshooting/
- 04-ILL/
- 05-P2P/
- 06-ISP-Coordination/
- 07-Ticketing/
- 08-RCA/

## Author

**Mohamed Ashik**

Learning focus: Network Monitoring, NOC Operations, Troubleshooting, ISP Coordination, and Network Operations.

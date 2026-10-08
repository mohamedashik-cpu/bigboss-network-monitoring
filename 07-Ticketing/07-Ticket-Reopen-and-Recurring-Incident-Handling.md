# Ticket Reopen and Recurring Incident Handling

## Overview

A ticket should not always be treated as permanently resolved just because a service was restored once.

If the same issue returns after closure, or if a ticket was closed before the problem was actually resolved, the NOC may need to reopen the ticket or create a new linked incident according to the organization's process.

This document explains generic methods for handling reopened tickets, recurring incidents, repeated alerts, and previous-ticket correlation.

> Important: This is a generic learning guide. Never publish customer information, production IP addresses, circuit IDs, internal ticket IDs, credentials, screenshots, or confidential company information.

## Objectives

- Understand when a ticket may need reopening
- Differentiate recurrence from a new incident
- Track repeated alerts
- Correlate current and previous tickets
- Document reopened incidents
- Re-escalate when required
- Track recurring problems toward RCA
- Avoid incorrect ticket closure

## 1. What Is a Reopened Ticket?

A reopened ticket is an incident that was previously closed or resolved but requires further action because the issue has returned or the original resolution was not sufficient.

Generic flow:

~~~text
Ticket Open
   ↓
Investigation
   ↓
Service Restored
   ↓
Verification
   ↓
Ticket Closed
   ↓
Issue Returns
   ↓
Reopen / New Linked Ticket
~~~

The exact action depends on the organization's ticketing process.

## 2. When May a Ticket Be Reopened?

Possible situations:

- Same issue returns shortly after closure
- Service becomes unavailable again
- Link starts flapping again
- Packet loss returns
- High latency returns
- Device becomes unreachable again
- Previous corrective action was unsuccessful
- Ticket was closed before required verification
- Customer or internal team reports the same unresolved issue

Always follow the approved reopen policy.

## 3. Reopen vs New Ticket

A recurring problem does not automatically mean the same ticket should be reopened.

### Reopen

May be appropriate when:

- The original ticket is still eligible for reopening
- The issue is directly related to the previous incident
- The ticketing process allows reopening
- The previous investigation is still relevant

### New Linked Ticket

May be appropriate when:

- The original ticket is permanently closed
- The new occurrence is treated as a separate incident
- A new SLA clock is required
- The service or impact is different
- The ticketing process requires a fresh incident

When creating a new ticket, reference the previous ticket where allowed.

## 4. Repeated Alert vs Recurring Incident

These terms should not be confused.

### Repeated Alert

The monitoring system generates the same or similar alert multiple times.

It may be caused by:

- A real recurring issue
- A flapping interface
- Monitoring noise
- Temporary instability
- Correlated alerts

### Recurring Incident

The underlying service problem occurs repeatedly and requires operational attention.

Example:

~~~text
Alert → Link Down → Restored
             ↓
        Later returns
             ↓
Alert → Link Down → Restored
~~~

Repeated incidents may indicate a deeper problem.

## 5. First Step: Verify the Current Incident

Do not immediately reopen a ticket based only on an alert.

Use the normal verification process:

~~~text
Monitoring Alert
      ↓
Check Current Status
      ↓
Verify Reachability
      ↓
Check Interface / Device
      ↓
Compare Previous Incident
      ↓
Decide Reopen / New Ticket
~~~

This reduces false escalations.

## 6. Previous Ticket Correlation

When a similar incident occurs, compare:

- Previous ticket reference
- Current ticket reference
- Incident type
- Service
- Start time
- Duration
- Symptoms
- Monitoring alerts
- Previous root cause
- Previous corrective action
- Current status

Example:

~~~text
Previous:
Ticket-XXXX
Issue: Link Flapping
Root Cause: <Confirmed cause>

Current:
Ticket-XXXX
Issue: Link Flapping
Status: Investigation

Correlation:
Same service / similar symptom
~~~

Do not claim that two incidents have the same root cause until it is confirmed.

## 7. Recurrence Tracking

A simple recurrence record:

| Occurrence | Ticket | Issue | Duration | Root Cause | Status |
|---|---|---|---|---|---|
| 1 | Ticket-XXXX | Link Flapping | <Duration> | <Cause> | Closed |
| 2 | Ticket-XXXX | Link Flapping | <Duration> | <Cause> | Closed |
| 3 | Ticket-XXXX | Link Flapping | <Duration> | Pending | Open |

This helps identify patterns.

## 8. Reopened Ticket Documentation

Example:

~~~text
Ticket: Ticket-XXXX
Previous Status: Closed
Current Status: Reopened

Issue:
Same connectivity issue observed again.

Previous Resolution:
<Service restoration action>

Current Observation:
<Confirmed current symptom>

Previous Ticket:
Ticket-XXXX

Current Action:
Issue re-verified and responsible team contacted.

Next Follow-up:
YYYY-MM-DD HH:MM
~~~

Keep the explanation factual.

## 9. Reopened Ticket and SLA

SLA handling for reopened incidents is organization-specific.

Do not assume that:

- The original SLA clock automatically continues
- A new SLA clock automatically starts
- The previous breach status carries forward

Check the applicable ticketing and SLA rules.

Document the relevant timestamps.

## 10. Re-escalation

A recurring incident may require escalation again.

Possible triggers:

- Issue returns after previous restoration
- Previous corrective action failed
- Multiple occurrences
- Business impact increases
- SLA risk
- Repeated missed ETR
- ISP cannot provide a permanent resolution
- RCA indicates an unresolved underlying problem

Generic flow:

~~~text
Issue Recurs
   ↓
Verify
   ↓
Check Previous Ticket
   ↓
Review Previous Action
   ↓
Raise / Reopen Ticket
   ↓
Inform Responsible Team
   ↓
Escalate if Required
   ↓
Track Until Stable
~~~

## 11. Recurring ISP Incident

Example:

~~~text
Service: <P2P Service>
Current Issue: Link Flapping

Previous Incident:
Ticket-XXXX

Current Incident:
Ticket-XXXX

Previous ISP Action:
<Service restoration>

Current ISP Status:
<Investigation>

Request:
Confirm whether the current incident has the same root cause and provide corrective action if required.

Next Follow-up:
YYYY-MM-DD HH:MM
~~~

Avoid blaming the ISP. Use factual language.

## 12. Temporary Restoration vs Permanent Resolution

A service may return to normal without the underlying problem being permanently fixed.

Example:

~~~text
Service Restored
      ↓
Monitoring Stable
      ↓
Issue Returns
      ↓
Recurring Incident Identified
~~~

If the problem returns, review whether the previous resolution was temporary.

## 13. Monitoring After Restoration

For recurring issues, restoration verification should include appropriate monitoring.

Possible checks:

- Device reachability
- Interface status
- Packet loss
- Latency
- Link stability
- Error counters
- Monitoring alerts

The observation period should follow the organization's process.

## 14. Recurring Flapping Incident

Generic example:

~~~text
Initial Incident:
Link went down and recovered.

Second Incident:
Same link flapped again.

NOC Action:
Verified monitoring alert and interface condition.

Correlation:
Previous incident reviewed.

Current Action:
ISP / responsible technical team contacted.

Pending:
Determine permanent cause and preventive action.
~~~

Repeated flapping should not simply be closed repeatedly without reviewing recurrence.

## 15. Recurring Packet Loss

Example:

~~~text
Occurrence 1:
Packet loss observed and service stabilized.

Occurrence 2:
Packet loss returned.

Occurrence 3:
Packet loss observed again.

NOC Action:
Compare monitoring data and previous tickets.

Investigation:
Check whether the issue is local, device-related, or provider-related.

Pending:
Identify confirmed cause and preventive action.
~~~

## 16. Recurring High Latency

Possible investigation areas:

- Local interface errors
- Device health
- Path changes
- Multiple destination comparison
- ISP network condition
- Packet loss correlation
- Monitoring history

Do not conclude the cause from latency alone.

## 17. Reopened Ticket Follow-up Template

~~~text
Ticket: Ticket-XXXX
Status: Reopened

Issue:
<Current issue>

Previous Ticket:
Ticket-XXXX

Previous Resolution:
<Confirmed previous resolution>

Current Verification:
<Current checks>

Current Status:
<Status>

ISP / Internal Reference:
<Reference>

Latest Update:
<Update>

ETR:
YYYY-MM-DD HH:MM

Next Follow-up:
YYYY-MM-DD HH:MM

Escalation:
Yes / No

Pending Action:
<Action>
~~~

## 18. Recurring Incident Tracking Template

~~~text
Recurring Incident Record

Service:
<Service>

Issue Type:
<Link Down / Flapping / Packet Loss / High Latency / Other>

Current Ticket:
Ticket-XXXX

Previous Tickets:
Ticket-XXXX
Ticket-XXXX

Occurrence Count:
<Count>

First Occurrence:
YYYY-MM-DD HH:MM

Latest Occurrence:
YYYY-MM-DD HH:MM

Previous Root Cause:
<Confirmed cause / Unknown>

Previous Corrective Action:
<Action>

Current Status:
<Status>

Current Root Cause:
<Confirmed cause / Investigation>

Preventive Action:
<Action / Pending>

RCA:
Required / Not Required / Pending

Next Review:
YYYY-MM-DD HH:MM
~~~

## 19. When to Request RCA for Recurrence

RCA may be appropriate when:

- The same issue repeatedly returns
- Previous corrective action failed
- Incident impact is significant
- The issue causes repeated SLA impact
- Management or customer process requires RCA
- ISP investigation identifies a recurring infrastructure problem

Follow the approved RCA policy.

## 20. Closure Verification

Before closing a recurring incident:

~~~text
[ ] Current issue resolved
[ ] Service verified
[ ] Relevant alerts cleared
[ ] Stability checked according to process
[ ] Current action documented
[ ] Previous incidents reviewed
[ ] RCA requirement checked
[ ] Preventive action tracked where required
[ ] Next action completed
[ ] Ticket closure criteria satisfied
~~~

Do not close an incident only because the monitoring alert temporarily cleared if the service remains unstable.

## 21. Shift Handover for Recurring Tickets

Example:

~~~text
Ticket: Ticket-XXXX
Priority: P2
Issue: Recurring Link Flapping

Previous Tickets:
Ticket-XXXX, Ticket-XXXX

Current Status:
Monitoring / ISP Investigation

Previous Action:
<Service restoration>

Current Action:
<Current action>

RCA:
Pending / Required

Latest ETR:
YYYY-MM-DD HH:MM

Next Follow-up:
YYYY-MM-DD HH:MM

Pending:
Continue ISP follow-up and monitor for recurrence.
~~~

This gives the next shift the historical context.

## 22. Common Mistakes

### Reopening Without Verification

Verify the current condition first.

### Treating Every Alert as a Recurrence

Monitoring alerts may be false or correlated.

### Ignoring Previous Tickets

Historical incidents can provide useful troubleshooting context.

### Assuming Same Root Cause

Similar symptoms do not prove the same cause.

### Repeating Temporary Fixes

Repeated restoration without root-cause investigation may allow the problem to continue.

### Losing SLA History

Record relevant timestamps and follow the approved SLA process.

### Closing Too Quickly

Verify service stability before closure where required.

### Missing RCA Tracking

Repeated incidents may require RCA or preventive action.

## 23. Reopen / Recurrence Checklist

~~~text
[ ] Current alert verified
[ ] Current service condition checked
[ ] Previous ticket searched
[ ] Similar incidents identified
[ ] Previous resolution reviewed
[ ] Reopen vs new ticket decision made
[ ] SLA handling checked
[ ] Current ticket updated
[ ] ISP / internal team informed
[ ] Escalation completed if required
[ ] ETR tracked
[ ] Next follow-up recorded
[ ] Recurrence tracked
[ ] RCA requirement checked
[ ] Restoration verified
[ ] Preventive action tracked where required
~~~

## 24. Complete Incident Example

~~~text
Initial Incident:
Link Down detected.

Ticket-XXXX created.

Investigation:
Monitoring and interface checks completed.

Action:
ISP contacted.

Restoration:
Service restored.

Verification:
Connectivity and stability verified.

Closure:
Ticket closed according to process.

Later:
Same service shows repeated link flapping.

New verification:
Current alert confirmed.

Historical review:
Previous ticket identified.

Correlation:
Same service and similar symptom.

Action:
Current incident documented and responsible team contacted.

Escalation:
Performed according to process.

RCA:
Requested because of recurrence.

Pending:
Permanent corrective / preventive action.

Final:
Service restored and stability monitored.
RCA / preventive action tracked separately if required.
~~~

## Key Takeaways

- A restored ticket is not automatically a permanently solved problem.
- Verify current conditions before reopening or escalating.
- Compare recurring incidents with previous tickets.
- Reopen vs new linked ticket depends on the organization's process.
- Do not assume recurring symptoms have the same root cause.
- Track ETR, SLA, escalation, and follow-up correctly.
- Repeated incidents may require RCA and preventive action.
- Monitor recently restored recurring services for stability.
- Document temporary restoration separately from permanent corrective action.
- Use factual, evidence-based updates.

## Related Topics

- NOC Ticketing Workflow
- Ticket Update and Closure Examples
- Ticket Priority and Severity
- Ticket SLA and Escalation Tracking
- NOC Ticket Shift Handover
- Ticket RCA Requirement and Tracking
- Link Down Troubleshooting
- Packet Loss and High Latency
- ISP Coordination Workflow

## Author

Mohamed Ashik

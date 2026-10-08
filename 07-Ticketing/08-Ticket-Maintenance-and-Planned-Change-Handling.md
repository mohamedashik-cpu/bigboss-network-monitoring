# Ticket Maintenance and Planned Change Handling

## Overview

Not every network alert represents an unexpected incident.

Planned maintenance and approved changes can intentionally affect devices, interfaces, links, or services for a defined period. NOC engineers must distinguish planned activity from an unplanned outage and monitor the environment accordingly.

This document covers generic maintenance-ticket handling, pre-checks, monitoring during a change, post-checks, and closure.

> Important: This is a generic learning guide. Never publish customer information, production IP addresses, circuit IDs, internal ticket IDs, credentials, maintenance schedules, screenshots, or confidential company information.

## Objectives

- Understand planned maintenance tickets
- Distinguish planned activity from an incident
- Perform pre-maintenance checks
- Track maintenance windows
- Monitor during planned changes
- Perform post-maintenance verification
- Handle unexpected issues during maintenance
- Document maintenance completion
- Avoid unnecessary incident escalation

## 1. What Is Planned Maintenance?

Planned maintenance is an approved activity scheduled in advance to maintain, upgrade, replace, test, or modify network infrastructure.

Examples:

- Router maintenance
- Switch maintenance
- Firewall maintenance
- ISP maintenance
- Link migration
- Hardware replacement
- Software or firmware upgrade
- Configuration change
- Network equipment testing

The exact activity should be confirmed through the approved change or maintenance process.

## 2. Maintenance vs Incident

### Planned Maintenance

The activity is:

- Approved
- Scheduled
- Documented
- Performed within an authorized window

### Incident

The service impact is unexpected or outside the approved activity.

Example:

~~~text
Approved maintenance:
01:00 - 02:00

Expected:
Temporary connectivity impact

Unexpected:
Service remains unavailable after 02:00
        ↓
Investigate / escalate as incident
~~~

A maintenance event can therefore result in a separate incident if the impact continues beyond the approved scope or window.

## 3. Maintenance Ticket Information

A maintenance record may contain:

~~~text
Maintenance / Change ID:
Activity:
Affected Service:
Affected Device:
Start Time:
End Time:
Maintenance Window:
Expected Impact:
Responsible Team:
ISP / Vendor:
Rollback Plan:
Monitoring Instructions:
Post-Check Required:
Status:
~~~

Use only information permitted by the organization's ticketing system.

## 4. Maintenance Window

The maintenance window defines when the approved activity is expected to occur.

Example:

~~~text
Start: YYYY-MM-DD HH:MM
End:   YYYY-MM-DD HH:MM
~~~

NOC should know:

- When monitoring impact may begin
- Expected duration
- When normal service should return
- When escalation is required if the activity exceeds the window

Do not invent maintenance times.

## 5. Pre-Maintenance Checklist

Before the activity starts:

~~~text
[ ] Maintenance / change approval confirmed
[ ] Maintenance window confirmed
[ ] Affected service identified
[ ] Expected impact understood
[ ] Responsible team identified
[ ] ISP / vendor involvement confirmed
[ ] Current device health checked
[ ] Interface status checked
[ ] Reachability checked
[ ] Existing alerts reviewed
[ ] Open related tickets reviewed
[ ] Monitoring requirements understood
[ ] Rollback / recovery process confirmed
~~~

The exact pre-checks depend on the change.

## 6. Baseline Checks

A baseline records the normal condition before maintenance.

Possible checks:

~~~text
Device Reachability
Interface Status
CPU / Memory
Packet Loss
Latency
Link Stability
Relevant Monitoring Alerts
Service Availability
~~~

For Cisco devices, commonly useful commands include:

~~~text
show ip interface brief
show interfaces description
show interfaces <interface>
show processes cpu
show processes memory
show logging
~~~

Use only approved commands and access methods.

## 7. Maintenance Start

When maintenance begins:

~~~text
Maintenance Status:
In Progress

Start Time:
YYYY-MM-DD HH:MM

Responsible Team:
<Approved team>

Expected Impact:
<Confirmed impact>

NOC Action:
Monitor affected services and alerts.
~~~

Record the actual start time when available.

## 8. Monitoring During Maintenance

NOC monitoring may include:

- Device reachability
- Interface status
- Link state
- Packet loss
- Latency
- Service availability
- Monitoring alerts
- Device health
- Restoration status

Do not treat every alert during an approved maintenance window as an unexpected incident.

First compare the alert with the approved maintenance scope.

## 9. Maintenance Alert Verification

When an alert appears:

~~~text
Alert Received
      ↓
Check Maintenance / Change Record
      ↓
Is the Affected Device / Service in Scope?
      ↓
Yes → Continue Planned Monitoring
No  → Investigate as Unexpected Incident
~~~

If the alert is within the approved scope, document it appropriately.

## 10. In-Scope Alert

Example:

~~~text
Alert:
Interface Down

Maintenance Status:
In Progress

Scope:
Affected interface is part of the approved activity.

Action:
Continue monitoring and record the event.
~~~

No unnecessary incident escalation should be performed if the alert is expected and properly covered by the maintenance.

## 11. Out-of-Scope Alert

Example:

~~~text
Maintenance:
Switch software upgrade

Alert:
Unrelated network device becomes unreachable.

Action:
Verify whether the alert is connected to the maintenance.

If unrelated:
Treat as a separate incident according to the incident process.
~~~

Never assume every alert during a maintenance window is caused by the maintenance.

## 12. Maintenance Overrun

If the maintenance continues beyond the approved window:

~~~text
Approved End Time:
YYYY-MM-DD HH:MM

Current Time:
YYYY-MM-DD HH:MM

Status:
Maintenance still in progress

Action:
Contact responsible team / ISP.
Request current status and revised completion time.
Escalate according to process if required.
~~~

An overrun should be documented clearly.

## 13. Unexpected Outage During Maintenance

Sometimes an approved change causes an unexpected issue.

Generic flow:

~~~text
Planned Change
      ↓
Unexpected Impact
      ↓
Verify Impact
      ↓
Inform Responsible Team
      ↓
Assess Severity
      ↓
Rollback / Recovery if Approved
      ↓
Restore Service
      ↓
Verify Stability
      ↓
Incident / Change Documentation
      ↓
RCA if Required
~~~

Follow the approved change and incident-management procedures.

## 14. Rollback

Rollback means returning the environment to the previous known-good state when the approved change cannot be completed successfully.

NOC role may include:

- Detecting unexpected impact
- Informing the responsible team
- Monitoring rollback
- Verifying service restoration
- Recording timestamps

NOC should not independently perform unauthorized rollback actions.

## 15. Post-Maintenance Checks

After the activity:

~~~text
[ ] Maintenance completed
[ ] Device reachable
[ ] Relevant interfaces up
[ ] Service reachable
[ ] Expected alerts cleared
[ ] Packet loss checked where applicable
[ ] Latency checked where applicable
[ ] Link stability checked
[ ] No unexpected alerts observed
[ ] Responsible team confirms completion
~~~

Use the appropriate checks for the affected service.

## 16. Restoration Verification

A maintenance activity should not be considered successfully completed only because the engineer says it is finished.

NOC should verify relevant monitoring indicators.

Example:

~~~text
Maintenance Completed:
YYYY-MM-DD HH:MM

NOC Verification:
YYYY-MM-DD HH:MM

Device Status:
Reachable

Interface Status:
Up

Service Status:
Available

Monitoring:
No unexpected active alerts observed.
~~~

## 17. Post-Maintenance Monitoring

Some activities require continued observation after completion.

Monitor for:

- Link flapping
- Packet loss
- High latency
- Device instability
- Repeated alerts
- Service degradation

The monitoring period should follow the organization's process.

## 18. Maintenance Completion Update

Generic ticket update:

~~~text
Maintenance activity completed.

Completion Time:
YYYY-MM-DD HH:MM

Post-checks completed.

Device / Service:
Verified reachable and operational.

Monitoring:
No unexpected active alerts observed.

Status:
Maintenance completed successfully.
~~~

Only state "successful" after appropriate verification.

## 19. Maintenance-Related Incident

If an unexpected issue remains after maintenance:

~~~text
Maintenance:
Completed

Unexpected Issue:
<Service impact>

Current Status:
<Service condition>

Verification:
<Checks performed>

Action:
Responsible technical team informed.

Incident:
Ticket-XXXX

Next Follow-up:
YYYY-MM-DD HH:MM

RCA:
Required / To be determined according to process
~~~

Keep the maintenance record and incident record linked where the system supports it.

## 20. ISP Maintenance

For ISP maintenance:

~~~text
ISP:
<Provider>

Maintenance Reference:
<Approved reference>

Service:
<Generic service>

Maintenance Window:
YYYY-MM-DD HH:MM - HH:MM

Expected Impact:
<Confirmed impact>

NOC Action:
Monitor during the window.

Post-Maintenance:
Verify reachability, stability, and service availability.
~~~

Use the ISP's approved maintenance communication.

## 21. Firewall / Network Device Maintenance

Generic example:

~~~text
Device:
Device-XXXX

Activity:
Approved software / configuration maintenance

Pre-Check:
Device reachable
Relevant interfaces operational
No unexpected critical alerts

During:
Monitor device and service status

Post-Check:
Device reachable
Interfaces operational
Services verified

Final:
Continue stability monitoring as required.
~~~

Do not publish actual device names, IP addresses, configurations, or screenshots.

## 22. Maintenance and Ticket Status

Possible generic statuses:

| Status | Meaning |
|---|---|
| Scheduled | Approved activity is planned |
| In Progress | Maintenance has started |
| Monitoring | Activity completed; post-check ongoing |
| Completed | Maintenance successfully verified |
| Overrun | Activity exceeded planned window |
| Failed | Approved activity did not complete successfully |
| Cancelled | Planned activity was cancelled |

Use the organization's actual status values where applicable.

## 23. Maintenance Handover

If maintenance remains active at shift change:

~~~text
Maintenance:
<Activity>

Status:
In Progress

Start:
YYYY-MM-DD HH:MM

Approved End:
YYYY-MM-DD HH:MM

Expected Impact:
<Impact>

Current Status:
<Status>

Responsible Team:
<Team>

Last Update:
<Update>

Next Action:
<Action>

Post-Check Required:
Yes / No
~~~

The incoming shift should know exactly what to monitor.

## 24. Maintenance Closure Checklist

~~~text
[ ] Approved activity completed
[ ] Actual completion time recorded
[ ] Device reachability verified
[ ] Interface status verified
[ ] Service availability verified
[ ] Relevant alerts reviewed
[ ] Stability checked
[ ] Unexpected issues documented
[ ] Related incident created if required
[ ] RCA requirement checked
[ ] Final ticket update added
[ ] Maintenance closed according to process
~~~

## 25. Common Mistakes

### Treating Planned Alerts as Unexpected Incidents

Always check the maintenance scope first.

### Ignoring Out-of-Scope Alerts

An unrelated alert still requires investigation.

### Closing Immediately After Change

Perform post-maintenance verification first.

### Missing Maintenance Overrun

Track the approved end time and escalate when required.

### No Baseline

Without pre-checks, it can be difficult to identify what changed.

### Unauthorized Change Action

Follow approved change-management procedures.

### Missing Handover

Active maintenance must be clearly communicated to the next shift.

### Publishing Confidential Maintenance Data

Never upload real maintenance schedules, customer details, internal references, or production information to a public repository.

## 26. Complete Maintenance Workflow

~~~text
Approved Change
      ↓
Maintenance Scheduled
      ↓
Pre-Checks
      ↓
Baseline Recorded
      ↓
Maintenance Starts
      ↓
Monitor
      ↓
Verify Alerts Against Scope
      ↓
Change Completed
      ↓
Post-Checks
      ↓
Service Verification
      ↓
Stability Monitoring
      ↓
Close Maintenance
~~~

If unexpected impact occurs:

~~~text
Unexpected Impact
      ↓
Verify
      ↓
Incident Process
      ↓
Escalate / Rollback if Required
      ↓
Restore
      ↓
Verify
      ↓
RCA if Required
~~~

## 27. Generic Maintenance Tracking Template

~~~text
MAINTENANCE / CHANGE TRACKING

Change ID:
CHANGE-XXXX

Activity:
<Maintenance activity>

Service:
<Service>

Affected Device:
Device-XXXX

Start Time:
YYYY-MM-DD HH:MM

Approved End Time:
YYYY-MM-DD HH:MM

Actual End Time:
YYYY-MM-DD HH:MM

Expected Impact:
<Impact>

Responsible Team:
<Team>

ISP / Vendor:
<Provider>

Pre-Check:
<Summary>

During Maintenance:
<Monitoring summary>

Post-Check:
<Summary>

Unexpected Issue:
Yes / No

Related Incident:
Ticket-XXXX / N/A

RCA:
Required / Not Required / Pending

Final Status:
Completed / Failed / Cancelled / Overrun

Remarks:
<Confirmed non-confidential information>
~~~

## Key Takeaways

- Planned maintenance is different from an unexpected incident.
- Always check the approved maintenance scope before escalating alerts.
- Perform baseline checks before the activity.
- Monitor affected services during the maintenance window.
- Treat out-of-scope or unexpected impact separately.
- Track maintenance overruns and revised completion times.
- Perform post-maintenance verification before closure.
- Recently changed services may require stability monitoring.
- Link related maintenance and incident records where appropriate.
- Follow approved change, rollback, escalation, and closure procedures.
- Never publish confidential production maintenance information.

## Related Topics

- NOC Ticketing Workflow
- Ticket Priority and Severity
- Ticket SLA and Escalation Tracking
- NOC Ticket Shift Handover
- Ticket RCA Requirement and Tracking
- Ticket Reopen and Recurring Incident Handling
- Monitoring and Alert Verification
- ISP Coordination Workflow

## Author

Mohamed Ashik

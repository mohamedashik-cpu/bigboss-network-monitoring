# Ticket Update and Closure Examples

## Overview

Ticket updates should provide a clear operational timeline from incident detection to closure.

This document contains generic examples for common NOC incidents. The examples are intentionally sanitized and should be adapted to the organization's actual ticketing process.

> Important: Do not copy real customer information, production IP addresses, circuit IDs, internal ticket IDs, ISP references, credentials, or confidential data into public documentation.

## 1. Link Down

### Initial Update

~~~text
YYYY-MM-DD HH:MM - Link-down alert received for the affected service.

Alert verified through monitoring. Basic reachability and interface checks completed.

Current Status: Service unavailable.
Action: ISP coordination initiated.
~~~

### ISP Ticket Update

~~~text
YYYY-MM-DD HH:MM - ISP contacted and incident reported.

ISP Ticket: ISP-Ticket-XXXX
Current Status: ISP investigation ongoing
ETR: HH:MM
Next Follow-up: HH:MM
~~~

### Follow-up

~~~text
YYYY-MM-DD HH:MM - Follow-up completed with ISP.

ISP advised that the technical team is investigating the issue.

Current Status: Service unavailable
Revised ETR: HH:MM
Next Follow-up: HH:MM
~~~

### Restoration

~~~text
YYYY-MM-DD HH:MM - ISP reported service restoration.

NOC verification initiated.
~~~

### Closure

~~~text
YYYY-MM-DD HH:MM - Service verified as reachable and monitoring status returned to normal.

Alert cleared and service remained stable during the observation period.

Incident resolved and ticket closed according to the applicable process.
~~~

---

## 2. Link Flapping

### Initial Update

~~~text
YYYY-MM-DD HH:MM - Repeated link up/down alerts observed for the affected service.

Alert history reviewed and the event was confirmed as link flapping.

Interface and monitoring checks initiated.
~~~

### Investigation Update

~~~text
YYYY-MM-DD HH:MM - Interface status and available error counters reviewed.

Flapping continues to be observed.

Further investigation and ISP coordination initiated as required.
~~~

### ISP Follow-up

~~~text
YYYY-MM-DD HH:MM - ISP contacted regarding recurring link flapping.

ISP Ticket: ISP-Ticket-XXXX
Current Status: Investigation ongoing
Next Update: HH:MM
~~~

### Closure

~~~text
YYYY-MM-DD HH:MM - Link remained stable during monitoring.

No further flapping alerts observed during the observation period.

Incident resolved and documented.
~~~

---

## 3. Packet Loss

### Initial Update

~~~text
YYYY-MM-DD HH:MM - Packet-loss alert received for the affected service.

Alert verified through monitoring.

Reachability and latency checks initiated to determine the scope of the issue.
~~~

### Investigation Update

~~~text
YYYY-MM-DD HH:MM - Packet-loss condition continues to be observed.

Relevant interface counters and monitoring data reviewed.

ISP coordination initiated for further investigation.
~~~

### ISP Update

~~~text
YYYY-MM-DD HH:MM - ISP ticket ISP-Ticket-XXXX created for packet-loss investigation.

Current Status: ISP investigation
ETR / Next Update: HH:MM
~~~

### Closure

~~~text
YYYY-MM-DD HH:MM - Packet-loss condition cleared.

Monitoring confirms normal service behavior.

Service remains stable and ticket is ready for closure according to process.
~~~

---

## 4. High Latency

### Initial Update

~~~text
YYYY-MM-DD HH:MM - High-latency alert received for the affected service.

Alert verified through monitoring.

Latency checks and reachability tests initiated.
~~~

### Investigation Update

~~~text
YYYY-MM-DD HH:MM - Elevated latency continues to be observed.

Multiple relevant destinations were checked to identify the scope of the condition.

ISP coordination initiated where applicable.
~~~

### Follow-up

~~~text
YYYY-MM-DD HH:MM - Follow-up completed with ISP.

ISP investigation is ongoing.

Current Status: Elevated latency
Next Update: HH:MM
~~~

### Closure

~~~text
YYYY-MM-DD HH:MM - Latency returned to the expected monitoring range.

No further high-latency alerts observed during the observation period.

Incident resolved.
~~~

---

## 5. Device Unreachable

### Initial Update

~~~text
YYYY-MM-DD HH:MM - Device-unreachable alert received.

Alert verified through monitoring.

Basic reachability verification initiated.
~~~

### Investigation Update

~~~text
YYYY-MM-DD HH:MM - Device remains unreachable from the monitoring system.

Relevant upstream connectivity and interface status checks initiated according to the troubleshooting process.

Escalation initiated as required.
~~~

### Restoration

~~~text
YYYY-MM-DD HH:MM - Device became reachable again.

Monitoring status returned to normal.

Device stability is being observed.
~~~

### Closure

~~~text
YYYY-MM-DD HH:MM - Device remained reachable during the observation period.

No additional unreachable alerts observed.

Incident resolved and documented.
~~~

---

## 6. Interface Down

### Initial Update

~~~text
YYYY-MM-DD HH:MM - Interface-down alert received.

Interface status verified through monitoring and authorized device checks.

Current Status: Interface unavailable.
~~~

### Investigation

~~~text
YYYY-MM-DD HH:MM - Interface condition reviewed.

Administrative and operational status checked along with relevant interface information.

Further action initiated according to the applicable troubleshooting process.
~~~

### Restoration

~~~text
YYYY-MM-DD HH:MM - Interface returned to the expected operational state.

Monitoring status verified as normal.
~~~

### Closure

~~~text
YYYY-MM-DD HH:MM - Interface remained operational during the observation period.

No additional interface-down alerts observed.

Incident resolved.
~~~

---

## 7. ISP Follow-up With No New Update

~~~text
YYYY-MM-DD HH:MM - Follow-up completed with ISP for ticket ISP-Ticket-XXXX.

No new technical update received.

Service remains in the reported state.

Revised ETR / next update requested.
Next Follow-up: HH:MM
~~~

This is better than repeatedly writing "ISP checked" because it records the actual outcome.

---

## 8. ETR Exceeded

~~~text
YYYY-MM-DD HH:MM - Previously provided ETR has been exceeded.

Service is still showing the reported issue on monitoring.

ISP contacted for the latest status and revised ETR.

Escalation requested according to the applicable process.
~~~

---

## 9. Escalation

~~~text
YYYY-MM-DD HH:MM - Incident escalated to the concerned ISP technical team because the previous restoration timeline was exceeded.

Current Status: Service unavailable
Previous ETR: HH:MM
Revised ETR: HH:MM
Next Follow-up: HH:MM
~~~

Do not write that an issue was escalated unless the escalation actually occurred.

---

## 10. ISP Reports Restoration

~~~text
YYYY-MM-DD HH:MM - ISP reported that the service has been restored.

NOC verification initiated to confirm reachability and monitoring status.
~~~

This avoids treating an ISP statement as the final verification.

---

## 11. Successful Restoration

~~~text
YYYY-MM-DD HH:MM - Service verified as reachable.

Monitoring alert cleared and relevant service indicators returned to normal.

No immediate recurrence observed.

Stability monitoring initiated.
~~~

---

## 12. Restoration Followed by Recurrence

~~~text
YYYY-MM-DD HH:MM - Service was previously restored and verified.

YYYY-MM-DD HH:MM - The same issue recurred and a new alert was received.

Previous ISP Ticket: ISP-Ticket-XXXX
Current Status: Issue recurring
Action: Incident re-escalated according to process.
~~~

Use the organization's rules to determine whether the original ticket should be reopened or a new ticket should be created.

---

## 13. False / Cleared Alert

~~~text
YYYY-MM-DD HH:MM - Monitoring alert received.

Alert reviewed and found to be cleared shortly after detection.

Current monitoring status is normal and no persistent issue was observed.

No further action required / monitoring continued according to process.
~~~

Do not label an alert as "false" without appropriate verification.

---

## 14. Maintenance-Related Alert

If an authorized maintenance activity explains an alert:

~~~text
YYYY-MM-DD HH:MM - Monitoring alert observed during the approved maintenance window.

The event is being tracked against the authorized maintenance activity.

Monitoring will continue and the service status will be verified after maintenance completion.
~~~

Never assume maintenance is authorized unless it is confirmed through the applicable process.

---

## 15. Ticket Waiting for ISP

~~~text
YYYY-MM-DD HH:MM - Required information provided to ISP.

Ticket ISP-Ticket-XXXX remains under ISP investigation.

Current Status: Waiting for ISP
Next Follow-up: HH:MM
~~~

---

## 16. Ticket Waiting for Internal Action

~~~text
YYYY-MM-DD HH:MM - External dependency has been cleared.

Internal verification / action is pending.

Current Status: Waiting for internal action
Pending Action: <Action>
Owner/Team: <Authorized team>
Next Update: HH:MM
~~~

---

## 17. Shift Handover Example

For an incident that remains open at shift change:

~~~text
Ticket: Ticket-XXXX
Service: P2P-Service-XXXX
Issue: Link Down
Start Time: YYYY-MM-DD HH:MM

Current Status:
Service unavailable / ISP investigation ongoing

Actions Completed:
- Alert verified
- Basic checks completed
- ISP contacted
- ISP ticket created

ISP Ticket:
ISP-Ticket-XXXX

Latest ISP Update:
Technical team investigating

ETR:
HH:MM

Last Follow-up:
HH:MM

Next Follow-up:
HH:MM

Escalation:
Yes / No

Pending Action:
Follow up with ISP and update ticket
~~~

The next engineer should be able to continue without repeating completed checks unnecessarily.

---

## 18. Ticket Closure Example

~~~text
YYYY-MM-DD HH:MM - Service restoration reported by ISP.

YYYY-MM-DD HH:MM - Service reachability verified from NOC monitoring.

YYYY-MM-DD HH:MM - Relevant alerts cleared and service remained stable during the observation period.

Final Status: Resolved

ISP Ticket: ISP-Ticket-XXXX
Restoration Time: YYYY-MM-DD HH:MM

Incident documentation completed and ticket closed according to process.
~~~

---

## 19. RCA Required

When an RCA is required:

~~~text
Service has been restored and verified.

RCA has been requested / received from the concerned team or ISP.

RCA Reference: RCA-XXXX
RCA Status: Pending / Received

Ticket will be closed according to the applicable process.
~~~

Do not invent an RCA cause before it is confirmed.

---

## 20. Generic Incident Timeline

A reusable incident timeline:

~~~text
[HH:MM] Alert detected
[HH:MM] Alert verified
[HH:MM] Basic checks completed
[HH:MM] Incident ticket created
[HH:MM] ISP contacted
[HH:MM] ISP ticket received
[HH:MM] ETR received
[HH:MM] Follow-up completed
[HH:MM] ETR revised / escalation performed
[HH:MM] Restoration reported
[HH:MM] Restoration verified
[HH:MM] Stability monitoring completed
[HH:MM] Ticket resolved/closed
~~~

---

## 21. Ticket Writing Style

Use:

- Short sentences
- Exact timestamps
- Objective observations
- Confirmed information
- Clear next actions
- Consistent terminology

Avoid:

- Emotional comments
- Blaming teams
- Unsupported assumptions
- Unnecessary technical detail
- Repeated identical updates
- Informal language

### Example

Instead of:

~~~text
ISP still not doing anything and link is down.
~~~

Write:

~~~text
Service remains unavailable. No new technical update was received during the latest follow-up. Revised ETR requested from ISP.
~~~

---

## 22. Final Closure Checklist

Before closure:

~~~text
[ ] Incident was verified
[ ] Ticket description is complete
[ ] Timeline is documented
[ ] Troubleshooting actions are recorded
[ ] ISP reference is recorded, if applicable
[ ] Latest ISP update is recorded
[ ] ETR history is documented
[ ] Escalation is documented, if applicable
[ ] Restoration was independently verified
[ ] Monitoring status is normal
[ ] Stability was observed according to process
[ ] RCA is recorded/requested when required
[ ] No pending action remains
[ ] Final closure note is clear
~~~

## Key Takeaways

- Every ticket update should answer "what happened next?"
- Use timestamps to create an accurate incident timeline.
- Keep updates factual and concise.
- Record ISP references and ETR changes.
- Do not claim actions that were not performed.
- Do not close a ticket only because an ISP reports restoration.
- Verify service recovery from the NOC side.
- Make handover notes actionable.
- Use confirmed information when documenting RCA.
- Good ticket notes reduce repeated troubleshooting and improve shift continuity.

## Related Topics

- NOC Ticketing Workflow
- ISP Coordination Workflow
- ISP Call and Email Communication
- Monitoring Logs and Documentation
- RCA
- Shift Handover
- NOC Glossary

## Author

Mohamed Ashik

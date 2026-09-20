# Monitoring Checklist

## Overview

A monitoring checklist helps NOC engineers perform routine monitoring activities consistently during a shift. It provides a simple sequence for checking monitoring systems, devices, interfaces, alerts, incidents, and pending follow-ups.

> **Important:** This document contains only generic and sanitized learning material. Do not store customer information, real production IP addresses, circuit IDs, ticket numbers, credentials, screenshots, or company-confidential information in this repository.

## Objectives

- Follow a consistent NOC monitoring routine
- Avoid missing active alerts or pending incidents
- Track link and device conditions
- Maintain proper ticket follow-up
- Support shift handover
- Improve monitoring discipline and documentation

## Daily Monitoring Flow

```text
Start Shift
    ↓
Check Handover
    ↓
Check Monitoring Dashboard
    ↓
Review Active Alerts
    ↓
Verify Critical Issues
    ↓
Check Device / Interface Status
    ↓
Review Open Tickets
    ↓
Follow Up with ISP / Team
    ↓
Monitor Restored Links
    ↓
Update Records
    ↓
Prepare Handover
    ↓
End Shift
```

## 1. Start-of-Shift Checklist

Before beginning regular monitoring:

- [ ] Review previous shift handover
- [ ] Identify open incidents
- [ ] Check pending ISP/team follow-ups
- [ ] Review expected maintenance or planned activities
- [ ] Open the required monitoring tools
- [ ] Confirm monitoring access is working
- [ ] Review important unresolved alerts

### Handover Information to Check

- Open link-down incidents
- P2P issues
- ILL issues
- Link-flapping incidents
- Packet-loss/high-latency issues
- Pending ISP responses
- Pending ETA/ETR
- Tickets awaiting updates
- Recently restored links requiring observation

## 2. Monitoring Dashboard Checklist

Check the monitoring dashboard for:

- [ ] Device Down alerts
- [ ] Interface Down alerts
- [ ] Link Down alerts
- [ ] Link Flapping alerts
- [ ] Packet Loss alerts
- [ ] High Latency alerts
- [ ] High Utilization alerts
- [ ] Other active critical alerts

For each important alert, check:

- Device
- Interface
- Alert type
- Start time
- Current status
- Severity
- Alert history

## 3. Alert Verification Checklist

For every significant alert:

- [ ] Confirm alert is still active
- [ ] Check whether it has already cleared
- [ ] Review alert history
- [ ] Check device reachability
- [ ] Check interface status
- [ ] Check related alerts
- [ ] Identify whether other devices are affected
- [ ] Classify the issue
- [ ] Perform approved basic troubleshooting

Use the alert verification process documented in:

```text
06-Alert-Verification-and-Classification.md
```

## 4. Device Health Checklist

For monitored devices, check the available health information relevant to the operational procedure.

Possible checks include:

- Reachability
- Interface state
- CPU utilization
- Memory utilization
- Interface errors
- Device uptime
- Recent alerts
- Environmental or hardware alerts when available

Example Cisco commands:

```text
show ip interface brief
show interfaces
show interfaces description
show logging
```

Only use commands that are authorized for the device and operational role.

## 5. Interface and Link Checklist

For important interfaces or links:

- [ ] Check Up/Down state
- [ ] Check for repeated state changes
- [ ] Review monitoring history
- [ ] Check interface errors when available
- [ ] Check packet loss
- [ ] Check latency
- [ ] Check related alerts
- [ ] Confirm whether the remote side is affected when applicable

### Link Status

```text
UP      → Normal operational state
DOWN    → Requires verification
FLAP    → Repeated state changes; investigate
ADMIN DOWN → May be intentionally disabled
```

## 6. ISP Monitoring Checklist

When monitoring ISP-connected services:

- [ ] Check active ISP alerts
- [ ] Verify link status
- [ ] Check device reachability
- [ ] Check packet loss when required
- [ ] Check latency when required
- [ ] Review recurring incidents
- [ ] Check open ISP tickets
- [ ] Follow up on pending updates
- [ ] Record ETA/ETR when provided
- [ ] Verify restoration after an ISP reports recovery

Generic ISP examples used for learning:

- Generic-ISP-A
- Generic-ISP-B
- Generic-ISP-C

Actual production provider details should not be documented in public repositories unless they are already public and appropriate for the learning context.

## 7. ILL Monitoring Checklist

For an Internet Leased Line incident:

- [ ] Confirm monitoring alert
- [ ] Verify link status
- [ ] Check device/interface status
- [ ] Check reachability
- [ ] Check packet loss or latency when relevant
- [ ] Review existing ticket
- [ ] Contact/escalate to the responsible ISP/team
- [ ] Record the latest update
- [ ] Follow up until restoration
- [ ] Verify stability after recovery

Generic reference:

```text
Service: Generic-ILL
Status: Down
Reference: ISP-Ticket-XXXX
Action: Escalated to responsible ISP/team
```

## 8. P2P Monitoring Checklist

For a Point-to-Point link issue:

- [ ] Confirm the alert
- [ ] Identify the affected endpoints
- [ ] Check reachability
- [ ] Check interface status
- [ ] Check whether one or both endpoints are affected
- [ ] Review monitoring history
- [ ] Check packet loss/latency when required
- [ ] Raise/update the appropriate ticket
- [ ] Coordinate with the responsible team/ISP
- [ ] Verify both ends after restoration

Generic reference:

```text
Endpoint-A ↔ Endpoint-B
Status: Link issue
Reference: Ticket-XXXX
```

## 9. Open Ticket Checklist

During the shift, review open incidents:

- [ ] Ticket reference available
- [ ] Current status known
- [ ] Latest update recorded
- [ ] Responsible team/ISP identified
- [ ] ETA/ETR recorded when provided
- [ ] Next follow-up time known
- [ ] Monitoring status checked
- [ ] Restoration verified when reported

Avoid leaving a ticket without a clear next action.

## 10. Follow-up Checklist

When waiting for an external team or ISP:

1. Check the last update.
2. Check whether the expected update time has passed.
3. Review the current monitoring status.
4. Contact the responsible team according to the escalation process.
5. Record the new update.
6. Continue monitoring.

Generic follow-up note:

```text
Incident: Generic-ISP Link Down
Current Status: Under Investigation
Reference: Ticket-XXXX
Last Update: Awaiting restoration update
Next Action: Follow up with responsible team
```

## 11. Restoration Checklist

When an issue is reported as restored:

- [ ] Check monitoring status
- [ ] Confirm device reachability
- [ ] Confirm interface status
- [ ] Check link stability
- [ ] Check packet loss when required
- [ ] Check latency when required
- [ ] Watch for recurrence
- [ ] Update the ticket
- [ ] Continue observation according to procedure

A status change from Down to Up is not by itself enough to assume long-term stability.

## 12. Shift Handover Checklist

Before handing over the shift:

### Open Incidents

- [ ] Incident summary
- [ ] Affected service
- [ ] Current status
- [ ] Ticket reference
- [ ] Latest ISP/team update
- [ ] Pending action
- [ ] Next follow-up
- [ ] ETA/ETR if available

### Recently Restored Incidents

- [ ] Restoration time
- [ ] Verification completed
- [ ] Current monitoring status
- [ ] Any recurrence observed

### Generic Handover

```text
Open Incident:
Generic-ISP Link Issue

Status:
Under Investigation

Reference:
Ticket-XXXX

Last Update:
Responsible team acknowledged the issue.

Pending:
Await next update.

Next Shift Action:
Continue monitoring and follow up.
```

## 13. Daily NOC Quick Checklist

Use this short checklist when a quick shift reference is needed.

### Start

- [ ] Handover checked
- [ ] Monitoring opened
- [ ] Open incidents reviewed
- [ ] Pending follow-ups identified

### Monitor

- [ ] Device alerts checked
- [ ] Interface alerts checked
- [ ] Link status checked
- [ ] Flapping checked
- [ ] Packet loss checked when required
- [ ] Latency checked when required

### Act

- [ ] Alerts verified
- [ ] Basic troubleshooting performed
- [ ] Ticket created/updated
- [ ] ISP/team contacted when required
- [ ] Follow-up completed

### Recover

- [ ] Restoration verified
- [ ] Link stability checked
- [ ] Monitoring stable

### Handover

- [ ] Open incidents documented
- [ ] Pending actions documented
- [ ] Latest updates recorded
- [ ] Next shift informed

## 14. Monitoring Documentation Format

A simple monitoring entry can use:

```text
Time:
Alert:
Device/Service:
Status:
Verification:
Action:
Ticket:
Current Update:
Next Action:
```

### Generic Example

```text
Time: HH:MM
Alert: Link Down
Device/Service: Generic-ISP
Status: Active
Verification: Device and interface checked
Action: Ticket raised and escalated
Ticket: Ticket-XXXX
Current Update: Awaiting ISP response
Next Action: Follow up and continue monitoring
```

## Important NOC Practices

- Start every shift by checking the handover.
- Verify alerts before taking escalation action.
- Keep monitoring history in mind when classifying incidents.
- Track every open incident until closure or handover.
- Record factual updates with timestamps when required.
- Verify restoration independently where possible.
- Continue monitoring recently restored links.
- Do not create duplicate tickets for the same incident without checking existing records.
- Follow the organization's escalation and severity procedures.
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

```text
Customer-Site-A
Device-A
Interface-X
X.X.X.X
Generic-ISP
Ticket-XXXX
ISP-Ticket-XXXX
```

## Key Takeaways

- A checklist helps maintain consistent NOC operations.
- Shift handover is an important part of monitoring continuity.
- Alerts should be verified before escalation.
- Open tickets require regular follow-up.
- Restoration should be verified and monitored for stability.
- Clear documentation helps the next shift continue work without losing context.
- A short checklist can reduce missed actions during busy monitoring periods.

## Related Topics

- 01-ISP-Monitoring-Overview.md
- 02-OpManager-Monitoring.md
- 03-Device-Reachability.md
- 04-Link-Status-and-Flapping.md
- 05-Basic-Monitoring-Workflow.md
- 06-Alert-Verification-and-Classification.md
- 02-Troubleshooting/
- 04-ILL/
- 05-P2P/
- 06-ISP-Coordination/
- 07-Ticketing/

## Author

**Mohamed Ashik**

Learning focus: Network Monitoring, NOC Operations, Troubleshooting, ISP Coordination, and Network Operations.

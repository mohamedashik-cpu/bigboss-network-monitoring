# Basic Monitoring Workflow

## Overview

A basic NOC monitoring workflow defines the standard process followed when a monitoring alert is detected. The goal is to verify the alert, identify the affected device or interface, perform initial troubleshooting, raise or update a ticket when required, coordinate with the responsible team or ISP, verify restoration, and close the incident with proper documentation.

> **Important:** This document uses only generic and sanitized examples. No customer information, real IP addresses, circuit IDs, ticket numbers, contact details, credentials, screenshots, or confidential production data should be stored in this repository.

## Objectives

- Understand the complete NOC monitoring workflow
- Verify alerts before escalation
- Identify the affected device, interface, or link
- Perform basic troubleshooting
- Raise and update incidents correctly
- Coordinate with internal teams or ISPs
- Verify service restoration
- Maintain proper follow-up and handover
- Document incidents in a consistent manner

## End-to-End Workflow

```text
Alert
  ↓
Verify
  ↓
Identify
  ↓
Troubleshoot
  ↓
Ticket
  ↓
Escalate
  ↓
Follow-up
  ↓
Restore
  ↓
Verify
  ↓
Monitor
  ↓
Close
```

## 1. Alert Detection

The workflow starts when a monitoring system generates an alert.

Common alerts include:

- Device Down
- Interface Down
- Link Down
- Link Flapping
- High Latency
- Packet Loss
- Device Unreachable
- Service-related alert

### Initial Questions

Before taking action, identify:

- What device is affected?
- Which interface or link is affected?
- When did the alert start?
- Is the alert still active?
- Is the issue affecting one device or multiple devices?

## 2. Initial Verification

Do not immediately assume that every alert represents a confirmed outage.

Perform basic verification using available monitoring and network tools.

### Generic Verification Steps

1. Open the monitoring alert.
2. Check the current status.
3. Check the alert start time.
4. Check recent monitoring history.
5. Confirm whether the alert is still active.
6. Check whether related devices are also affected.
7. Perform a basic reachability test when appropriate.

Example:

```text
Monitoring Alert:
Device-A → Interface-X → Down

Initial Check:
Alert still active → Yes
Device reachable → No
Related devices affected → Unknown
```

## 3. Identify the Issue

After verification, classify the issue.

| Condition | Possible Classification |
|---|---|
| Device unreachable | Device/Connectivity issue |
| Interface down | Interface/Link issue |
| Down → Up repeatedly | Link Flapping |
| High response time | High Latency |
| Packet loss detected | Connectivity/Performance issue |
| Multiple devices affected | Possible upstream/common-path issue |

Classification helps determine the next troubleshooting and escalation step.

## 4. Basic Troubleshooting

Perform only the troubleshooting steps that are appropriate for the issue and within the responsibilities of the NOC role.

### Common Checks

- Monitoring status
- Device reachability
- Interface status
- Interface errors
- Recent alert history
- Link state
- Related device status
- Recent restoration or repeated flapping

### Example Cisco Commands

```text
show ip interface brief
show interfaces
show interfaces description
show logging
```

Example sanitized check:

```text
Device-A# show ip interface brief
```

> Commands should be used according to the device type, access level, and approved operational procedure.

## 5. Ticket Creation or Update

If the issue requires further action, create a ticket or update an existing incident according to the organization's process.

A generic incident record may contain:

- Incident summary
- Affected service
- Generic device/interface reference
- Alert time
- Current status
- Initial troubleshooting performed
- Escalation details
- Ticket reference
- Follow-up status

### Generic Ticket Example

```text
Issue:
Generic-ISP link is down.

Detected:
Monitoring alert received.

Initial Checks:
Device reachability checked.
Interface status checked.

Action:
Issue escalated to responsible ISP/team.

Reference:
Ticket-XXXX
```

## 6. ISP or Team Escalation

When the issue is outside the NOC's immediate scope, escalate it to the appropriate team or ISP.

Common escalation situations:

- ISP link down
- P2P link issue
- ILL connectivity issue
- Persistent packet loss
- High latency
- Repeated link flapping
- Physical connectivity issue requiring field support

When escalating, provide clear and relevant information.

### Generic Escalation Information

```text
Service: Generic-ISP
Location: Customer-Site-A
Issue: Link Down
Detected Time: HH:MM
Current Status: Down
Initial Checks: Reachability and interface status checked
Reference: ISP-Ticket-XXXX
```

Never include confidential production information in public learning documentation.

## 7. Follow-up

Escalation does not mean the incident is complete.

Continue monitoring the incident until:

- The responsible team acknowledges the issue
- An update or ETA/ETR is received when applicable
- Restoration activity is completed
- Monitoring status returns to normal
- Final verification is completed

### Follow-up Checklist

- [ ] Ticket/reference available
- [ ] Issue acknowledged
- [ ] Latest update recorded
- [ ] ETA/ETR recorded when provided
- [ ] Monitoring status checked
- [ ] Restoration confirmed

## 8. Restoration Verification

When the ISP or responsible team reports that the issue is resolved, verify it independently using available monitoring tools.

Check:

- Device status
- Interface status
- Link status
- Reachability
- Packet loss
- Latency
- Alert state

Do not close an incident only because an external team says the link is restored. Confirm the service condition from the monitoring side.

## 9. Post-Restoration Monitoring

After restoration, continue monitoring for a suitable period according to the operational procedure.

Look for:

- Repeated link down/up events
- Packet loss
- High latency
- Interface errors
- New alerts
- Link flapping

A link that becomes Up and immediately goes Down again should be treated as a continuing or recurring issue rather than a fully resolved incident.

## 10. Incident Closure

Once the service is stable and the required checks are complete:

1. Confirm the issue is resolved.
2. Update the ticket.
3. Record relevant actions.
4. Record the final status.
5. Add RCA information when available or required.
6. Close the incident according to the organization's procedure.

### Generic Closure Note

```text
Issue: Generic-ISP link down
Status: Restored
Verification: Device and interface status normal
Monitoring: Stable after restoration
RCA: Awaiting/Provided by responsible team
Final Action: Incident closed as per procedure
```

## 11. Shift Handover

If the incident remains open at shift end, provide a clear handover.

A handover should include:

- Issue summary
- Affected service
- Current status
- Ticket/reference
- Last update
- Pending action
- Expected next update
- Escalation status

### Generic Handover Example

```text
Incident: Generic-ISP link issue
Status: Under investigation
Reference: Ticket-XXXX
Last Update: ISP team acknowledged the issue
Pending: Next status update
Action for Next Shift: Continue monitoring and follow up
```

## Generic Incident Workflow Example

### Scenario

A monitoring system reports that a generic ISP interface is down.

### Workflow

```text
1. Alert received
        ↓
2. Check monitoring status
        ↓
3. Confirm alert is still active
        ↓
4. Check device reachability
        ↓
5. Check interface status
        ↓
6. Classify as link/interface issue
        ↓
7. Perform basic troubleshooting
        ↓
8. Raise/update ticket
        ↓
9. Escalate to ISP/team
        ↓
10. Follow up for status/ETA
        ↓
11. ISP/team reports restoration
        ↓
12. Verify device/interface/reachability
        ↓
13. Continue monitoring
        ↓
14. Update and close ticket
```

## Practical NOC Checklist

### Alert

- [ ] Alert identified
- [ ] Start time checked
- [ ] Current status confirmed

### Verification

- [ ] Device checked
- [ ] Interface checked
- [ ] Reachability checked
- [ ] Related alerts checked

### Troubleshooting

- [ ] Basic checks completed
- [ ] Issue classified
- [ ] Appropriate commands/checks performed

### Ticketing

- [ ] Ticket created or updated
- [ ] Actions documented
- [ ] Reference recorded

### Escalation

- [ ] Responsible team/ISP contacted
- [ ] Issue acknowledged
- [ ] ETA/ETR recorded when applicable

### Restoration

- [ ] Service restored
- [ ] Device/interface verified
- [ ] Monitoring stable
- [ ] No immediate recurrence

### Closure

- [ ] Ticket updated
- [ ] Final status recorded
- [ ] RCA recorded when available
- [ ] Incident closed or handed over

## Important NOC Practices

- Always verify an alert before escalation.
- Use monitoring history to understand recurring issues.
- Keep incident updates short, factual, and time-based.
- Follow the approved escalation process.
- Continue follow-up until resolution is verified.
- Independently verify restoration where possible.
- Maintain clear shift handovers.
- Never expose confidential production information.
- Do not copy real customer or company data into public repositories.

## Confidentiality Guidelines

This repository is for learning and portfolio documentation.

Never upload:

- Customer names
- Real customer IP addresses
- Private/internal IP details from production
- Circuit IDs
- Ticket IDs or numbers
- Phone numbers
- Email addresses
- Credentials or passwords
- Monitoring screenshots containing real data
- Internal network diagrams
- Firewall screenshots
- Proprietary configurations
- Company-confidential information

Use sanitized placeholders such as:

```text
Customer-Site-A
Device-A
Interface-X
X.X.X.X
10.x.x.x
Generic-ISP
Ticket-XXXX
ISP-Ticket-XXXX
```

## Key Takeaways

- NOC monitoring is a continuous process, not just alert checking.
- Every alert should be verified before escalation.
- Basic troubleshooting helps identify the likely issue domain.
- Ticketing provides traceability and accountability.
- ISP/team coordination requires clear and concise updates.
- Restoration must be verified from the monitoring side.
- Stable monitoring after recovery helps detect recurring issues.
- Proper handover prevents incidents from being lost between shifts.
- Good documentation improves operational consistency.

## Related Topics

- `01-ISP-Monitoring-Overview.md`
- `02-OpManager-Monitoring.md`
- `03-Device-Reachability.md`
- `04-Link-Status-and-Flapping.md`
- `02-Troubleshooting/`
- `04-ILL/`
- `05-P2P/`
- `06-ISP-Coordination/`
- `07-Ticketing/`
- `08-RCA/`

## Author

**Mohamed Ashik**

Learning focus: Network Monitoring, NOC Operations, Troubleshooting, ISP Coordination, and Network Operations.

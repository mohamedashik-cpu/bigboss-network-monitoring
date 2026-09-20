# Alert Verification and Classification

## Overview

Alert verification is one of the first responsibilities in NOC monitoring. A monitoring alert should be checked and classified before taking further action. Correct classification helps reduce unnecessary escalations and ensures that the appropriate troubleshooting process is followed.

> **Important:** This document contains only generic and sanitized learning examples. Do not store customer information, real production IP addresses, circuit IDs, ticket numbers, credentials, monitoring screenshots, or company-confidential information in this repository.

## Objectives

- Understand how to verify monitoring alerts
- Differentiate active and cleared alerts
- Identify common alert types
- Classify alerts before troubleshooting
- Reduce unnecessary escalation
- Decide the appropriate next action
- Document alert verification clearly

## Alert Verification Flow

```text
Alert Received
      ↓
Check Alert Details
      ↓
Is Alert Still Active?
      ↓
   ┌──┴──┐
   │     │
  Yes    No
   │     │
   ↓     ↓
Verify   Review
Impact   History
   │     │
   └──┬──┘
      ↓
Classify Alert
      ↓
Basic Troubleshooting
      ↓
Ticket / Escalation if Required
```

## 1. What Is a Monitoring Alert?

A monitoring alert is an automated notification generated when a monitored device, interface, link, or service crosses a configured condition or threshold.

Common examples:

- Device Down
- Interface Down
- Link Down
- Link Flapping
- Packet Loss
- High Latency
- High Utilization
- Device Unreachable
- Service-related alert

The alert itself is an indication that requires verification. It is not always proof of a confirmed outage.

## 2. Check Alert Details

When an alert is received, first collect the basic information available in the monitoring system.

Check:

- Device name
- Interface name or identifier
- Alert type
- Alert start time
- Current status
- Alert severity
- Last known status
- Monitoring history
- Related alerts

### Generic Example

```text
Device: Device-A
Interface: Interface-X
Alert: Link Down
Start Time: HH:MM
Status: Active
Severity: High
```

## 3. Active vs Cleared Alerts

### Active Alert

An active alert means the monitored condition is currently detected.

Example:

```text
Device-A
Interface-X
Status: Down
Alert: Active
```

Further verification is required.

### Cleared Alert

A cleared alert means the monitored condition has returned to normal.

Example:

```text
Device-A
Interface-X
Status: Up
Alert: Cleared
```

Even when an alert clears quickly, review the event history if the incident is important or recurring.

## 4. Common Alert Classifications

| Alert Type | What It Indicates | Initial Action |
|---|---|---|
| Device Down | Device may be unreachable | Check reachability and related devices |
| Interface Down | Interface is not operational | Check interface status and link condition |
| Link Down | Connectivity path may be unavailable | Verify monitoring and device status |
| Link Flapping | Link repeatedly changes state | Check history and interface statistics |
| Packet Loss | Packets are not reaching the destination consistently | Perform reachability and packet-loss checks |
| High Latency | Response time is higher than expected | Check latency history and path conditions |
| High Utilization | Resource or link usage is high | Check interface/resource statistics |
| Device Unreachable | Monitoring cannot reach the device | Check reachability and upstream connectivity |

## 5. Device Down Alert

A Device Down alert may indicate:

- Device failure
- Power issue
- Connectivity issue
- Upstream network issue
- Monitoring communication issue
- Planned maintenance

### Verification

1. Check whether the alert is still active.
2. Check device reachability.
3. Check related devices.
4. Review recent monitoring history.
5. If authorized, check available device information.
6. Escalate according to the operational procedure.

## 6. Interface Down Alert

An interface-down alert should be checked against the device and interface state.

Example command:

```text
show ip interface brief
```

Generic output:

```text
Interface              IP-Address      Status                Protocol
GigabitEthernet0/0     X.X.X.X         up                    up
GigabitEthernet0/1     X.X.X.X         down                  down
```

The exact reason for an interface-down condition requires further investigation.

Possible causes include:

- Physical link issue
- Remote-side issue
- Administrative shutdown
- Device-side problem
- Configuration issue

## 7. Link Flapping Alert

Link flapping occurs when an interface repeatedly changes between Up and Down states.

Example:

```text
10:01  → Down
10:03  → Up
10:05  → Down
10:07  → Up
```

### Initial Checks

- Review monitoring history
- Check interface status
- Check interface statistics
- Check logs when authorized
- Check whether the remote side is also affected
- Monitor for recurrence

Repeated flapping should not be treated as a normal stable condition simply because the interface is currently Up.

## 8. Packet Loss Alert

Packet loss means some packets are not reaching the destination successfully.

Basic checks may include:

```text
ping X.X.X.X
```

For learning documentation, always use a sanitized address such as:

```text
ping X.X.X.X
```

Possible causes can include:

- Link congestion
- Physical connectivity issue
- Interface errors
- Routing/path problems
- Upstream ISP issue
- Device resource conditions

Packet loss should be verified over an appropriate observation period rather than relying on a single test.

## 9. High Latency Alert

High latency means response time is above the expected threshold.

Basic checks:

- Compare current latency with historical values
- Check packet loss
- Check whether multiple destinations are affected
- Check the path when appropriate
- Check for related alerts
- Escalate according to the approved process

High latency and packet loss may occur together, but they should still be verified separately.

## 10. False or Non-Persistent Alerts

A monitoring alert may clear shortly after it is generated.

Possible reasons include:

- Temporary connectivity interruption
- Short-duration link flap
- Monitoring communication delay
- Device response delay
- Transient network condition

### Recommended Action

1. Check the alert history.
2. Check the duration.
3. Check whether the same alert occurred repeatedly.
4. Check related alerts.
5. Record the observation if required.
6. Escalate if the pattern indicates a recurring issue.

## 11. Correlated Alerts

Multiple alerts may be related to the same underlying incident.

Example:

```text
Device-A Down
      ↓
Interface-X Down
      ↓
Several downstream devices Unreachable
```

Instead of treating every alert as a separate incident, identify whether they share a common dependency.

Possible common causes include:

- Upstream link failure
- Core device issue
- Power failure
- Common ISP path issue
- Maintenance activity

Correlation helps avoid duplicate ticket creation.

## 12. Alert Severity

Severity depends on the organization's monitoring and incident-management process.

A generic classification may consider:

- Number of affected services
- Number of affected sites
- Business impact
- Duration
- Service criticality
- Recurrence
- Availability of redundancy

Severity should follow the organization's defined incident policy rather than personal judgment.

## 13. Alert Verification Checklist

### Alert Details

- [ ] Device identified
- [ ] Interface identified
- [ ] Alert type identified
- [ ] Start time checked
- [ ] Current status checked
- [ ] Severity checked

### Verification

- [ ] Monitoring history checked
- [ ] Device reachability checked
- [ ] Interface status checked
- [ ] Related alerts checked
- [ ] Recurrence checked

### Classification

- [ ] Device issue
- [ ] Interface issue
- [ ] Link issue
- [ ] Flapping
- [ ] Packet loss
- [ ] High latency
- [ ] Other service issue

### Action

- [ ] Basic troubleshooting completed
- [ ] Ticket created/updated if required
- [ ] Responsible team/ISP escalated if required
- [ ] Follow-up scheduled/recorded
- [ ] Restoration verified when applicable

## Generic Alert Verification Example

### Scenario

A monitoring system reports a link-down alert for a generic ISP connection.

### Verification

```text
Alert received
      ↓
Alert still active? → Yes
      ↓
Device reachable? → No
      ↓
Interface status checked
      ↓
Related device alerts checked
      ↓
Issue classified as connectivity/link issue
      ↓
Basic troubleshooting performed
      ↓
Ticket raised/updated
      ↓
ISP/team escalation
      ↓
Follow-up
```

## Example of a Cleared Alert

### Scenario

A link-down alert appears and clears after a short period.

### Action

```text
Alert received
      ↓
Alert clears
      ↓
Check event duration
      ↓
Review monitoring history
      ↓
Check recurrence
      ↓
No repeated issue observed
      ↓
Record observation if required
```

If the same alert repeats multiple times, treat it as a potential recurring or flapping condition and investigate further.

## Documentation Example

A concise NOC update can be structured as:

```text
Alert: Generic-ISP Link Down
Status: Active
Detected: HH:MM
Verification: Device and interface checked
Classification: Connectivity/Link issue
Action: Ticket-XXXX raised and escalated
Next Step: Follow up for restoration/update
```

## Important NOC Practices

- Verify alerts before escalation.
- Do not assume every alert is a confirmed outage.
- Check both current state and historical behavior.
- Look for correlated alerts.
- Avoid duplicate tickets for the same underlying incident.
- Use approved commands and procedures.
- Record factual observations.
- Continue monitoring after a temporary recovery.
- Follow the organization's severity and escalation policy.
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

- An alert is an indication that must be verified.
- Active and cleared alerts require different follow-up approaches.
- Correct classification helps determine the next troubleshooting step.
- Historical monitoring data is important for identifying recurring issues.
- Correlated alerts can indicate a common underlying problem.
- Restoration should be verified rather than assumed.
- Clear documentation improves NOC communication and incident tracking.

## Related Topics

- 01-ISP-Monitoring-Overview.md
- 02-OpManager-Monitoring.md
- 03-Device-Reachability.md
- 04-Link-Status-and-Flapping.md
- 05-Basic-Monitoring-Workflow.md
- 02-Troubleshooting/
- 07-Ticketing/
- 08-RCA/

## Author

**Mohamed Ashik**

Learning focus: Network Monitoring, NOC Operations, Troubleshooting, ISP Coordination, and Network Operations.

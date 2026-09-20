# Link Status and Flapping

## Overview

Link status monitoring is a basic NOC activity used to identify whether a network interface or monitored connection is operating normally, unavailable, or repeatedly changing state.

Common conditions include **Up**, **Down**, and **Flapping**. Correctly identifying the condition helps determine the next verification, troubleshooting, escalation, and follow-up steps.

> **Note:** This document contains generic learning material only. No customer names, real IP addresses, circuit IDs, ticket IDs, screenshots, credentials, or company-confidential information are included.

## Objectives

- Understand common link states.
- Differentiate Link Down and Link Flapping.
- Understand Down-to-Up recovery events.
- Perform basic link-status verification.
- Follow a generic escalation and restoration workflow.

## Common Link States

| State | General Meaning |
|---|---|
| Up | Link/interface is currently operational |
| Down | Link/interface is currently unavailable |
| Flapping | Link repeatedly changes between Up and Down |
| Admin Down | Interface has been administratively disabled |

These states are observations. The actual root cause requires further investigation.

## Link Up

A link is considered Up when the monitoring system and relevant device/interface checks indicate that connectivity is operational.

Basic verification may include:

- Monitoring status is Up.
- Device is reachable.
- Relevant interface is Up.
- Basic connectivity is successful.
- No continuing related alerts are present.

## Link Down

A Link Down condition means the monitored connection or interface is currently unavailable.

Possible areas for investigation include:

- Interface state
- Device reachability
- Physical connectivity
- ISP/service condition
- Power-related condition
- Upstream network path
- Configuration or administrative state

These are investigation areas, not automatic root-cause conclusions.

## Link Flapping

Link Flapping occurs when a link repeatedly changes between Up and Down states within a period of time.

Example:

```text
10:01  Link Down
10:02  Link Up
10:04  Link Down
10:05  Link Up
10:08  Link Down
```

Repeated state changes may indicate an unstable condition and should be investigated according to the organization's troubleshooting procedure.

## Link Down vs Link Flapping

| Condition | Main Observation | Typical Focus |
|---|---|---|
| Link Down | Link remains Down | Availability and cause investigation |
| Link Flapping | Link repeatedly changes state | Stability and repeated-event investigation |
| Down → Up | Link recovered | Restoration verification and stability monitoring |

## Basic Link Verification Workflow

```text
Alert Received
      |
      v
Check Current Status
      |
      v
Verify Device Reachability
      |
      v
Check Interface Status
      |
      v
Identify Link Condition
      |
      +---------------------------+
      |                           |
      v                           v
Link Up / Recovered          Link Down / Flapping
      |                           |
      v                           v
Observe Stability            Troubleshoot / Escalate
      |                           |
      +------------+--------------+
                   v
             Update / Follow-up
                   |
                   v
            Verify Final Status
```

## Link Down Verification

### Step 1 — Confirm the Alert

Check whether the monitoring system still shows the link as Down.

### Step 2 — Check Device Reachability

Verify whether the associated network device is reachable.

### Step 3 — Check Interface Status

For Cisco devices, a common initial command is:

```text
show ip interface brief
```

This can help identify whether the relevant interface is Up, Down, or administratively Down.

### Step 4 — Perform Appropriate Connectivity Checks

Where authorized, use approved connectivity tests.

Example:

```text
ping <sanitized-destination>
```

### Step 5 — Determine Escalation

If the issue is confirmed and requires another team or ISP, follow the organization's approved ticketing and escalation procedure.

### Step 6 — Follow Up

Track the incident until an update or restoration is received.

### Step 7 — Verify Restoration

After the link returns Up:

- Confirm the monitoring status.
- Check device/interface status.
- Perform basic connectivity verification.
- Observe the link for stability.
- Update the relevant incident/ticket.

## Down → Up Immediately

Sometimes a link may go Down and return Up shortly afterward.

Example:

```text
Link Down
   ↓
Link Up within a short interval
```

This should not automatically be treated as a fully resolved issue.

### Recommended Checks

1. Confirm the alert duration.
2. Check whether the event repeated.
3. Review the monitoring history if available.
4. Verify current interface status.
5. Check for packet loss or other related symptoms where applicable.
6. Continue monitoring for stability.
7. Escalate if repeated or persistent.

## Link Flapping Verification

When repeated Up/Down events are observed:

1. Confirm the pattern in the monitoring system.
2. Record the generic event timing.
3. Check the current interface state.
4. Review available interface/error information.
5. Determine whether the issue is still active.
6. Check for related device or upstream alerts.
7. Escalate when required.
8. Continue monitoring after recovery.
9. Document confirmed observations.

## Interface Verification Commands

For Cisco devices, commonly useful verification commands include:

```text
show ip interface brief
show interfaces
show interfaces description
```

These commands provide different levels of interface information.

`show ip interface brief` is useful for a quick status overview.

`show interfaces` provides more detailed interface information, including counters and errors where supported.

`show interfaces description` helps provide a concise interface description and status view.

Use commands according to the issue and only on systems where you are authorized to perform CLI checks.

## Generic Incident Example — Link Down

### Scenario

A monitoring alert indicates that a monitored link is Down.

### Verification

- Alert is confirmed.
- Current link state is checked.
- Device reachability is verified.
- Interface status is checked.
- Appropriate connectivity testing is performed.

### Action

If the condition is confirmed:

- Incident/ticket is raised or updated.
- Responsible team or ISP is contacted when required.
- Follow-up is tracked.

### Restoration

The link returns to Up.

### Final Verification

- Monitoring status is Up.
- Interface status is verified.
- Connectivity is checked.
- Link stability is observed.
- Incident/ticket is updated.

## Generic Incident Example — Link Flapping

### Scenario

A monitored interface repeatedly changes between Up and Down.

### Action

- Confirm the repeated events.
- Review available interface information.
- Check whether the condition continues.
- Escalate according to the approved procedure.
- Continue monitoring after recovery.

### Important

Do not document a suspected physical, ISP, power, or configuration problem as the confirmed RCA unless evidence or the responsible technical team confirms it.

## Monitoring History

Historical monitoring information can help identify whether an event is isolated or recurring.

Useful observations may include:

- Event start time
- Event end time
- Number of state changes
- Duration
- Repeated occurrence
- Related alerts

Use only sanitized information in public learning documentation.

## Generic Incident Note

```text
Time:
Alert Type:
Service/Link:
Initial Status:
Verification:
Action Taken:
Escalation:
Restoration Time:
Final Status:
Follow-up:
```

## Important NOC Practices

- Verify the current link state before taking action.
- Distinguish a persistent Down condition from Flapping.
- Treat short Down-to-Up events as events that may still require observation.
- Check device and interface status together when relevant.
- Do not assume the root cause from the monitoring state.
- Follow the approved ticketing and escalation process.
- Verify restoration independently where possible.
- Continue monitoring after recovery when required.

## Confidentiality Guidelines

Never publish:

- Real customer IP addresses
- Customer names
- Circuit IDs
- Ticket numbers
- Device hostnames containing customer information
- Monitoring screenshots
- Internal topology
- Credentials
- Contact details
- Company-confidential information

Use sanitized values such as:

```text
Customer-Site-A
Link-A
Interface-X
X.X.X.X
Ticket-XXXX
Generic-ISP
```

## Key Takeaways

- Link status is a fundamental NOC monitoring indicator.
- Link Down means the monitored connection is currently unavailable.
- Link Flapping indicates repeated state changes and requires stability investigation.
- A Down-to-Up event should be verified and observed before closure.
- Monitoring data should be combined with device and interface checks.
- Confirmed findings should be separated from assumptions.
- Proper escalation, follow-up, and restoration verification are important parts of incident handling.

## Related Topics

- `01-ISP-Monitoring-Overview.md`
- `02-OpManager-Monitoring.md`
- `03-Device-Reachability.md`
- `05-Basic-Monitoring-Workflow.md`
- `04-ILL`
- `05-P2P`
- `07-Ticketing`
- `08-RCA`

## Author

**Mohamed Ashik**

Personal learning documentation based on practical NOC/network monitoring exposure.
# ILL Monitoring and Troubleshooting Overview

## Overview

ILL stands for **Internet Leased Line**. In NOC operations, ILL monitoring involves checking the availability and performance of a dedicated Internet service, verifying alerts, troubleshooting link conditions, coordinating with the ISP, and tracking restoration.

This document provides a generic learning reference based on common NOC workflows. No customer names, circuit IDs, production IP addresses, ticket numbers, or confidential company information are included.

## Objectives

- Understand the basic ILL monitoring workflow
- Verify ILL link-down and performance alerts
- Check device and interface status
- Perform basic connectivity verification
- Coordinate with the ISP when required
- Track ticket status and ETR
- Verify restoration and stability
- Maintain accurate incident documentation

## Common ILL Monitoring Checks

A generic ILL monitoring checklist may include:

- Link availability
- Device reachability
- Interface status
- Packet loss
- Latency
- Link flapping
- Monitoring alerts
- ISP ticket status
- Restoration status
- Post-restoration stability

## Basic ILL Workflow

```text
Monitor ILL
    |
    v
Alert Detected
    |
    v
Verify Alert
    |
    v
Check Device Reachability
    |
    v
Check Interface / Link Status
    |
    +---- Link Healthy ----> Continue Monitoring
    |
    +---- Link Down/Degraded
             |
             v
       Basic Troubleshooting
             |
             v
       Raise / Update Ticket
             |
             v
       ISP Coordination
             |
             v
       Track Status / ETR
             |
             v
       Restoration
             |
             v
       Verify Link
             |
             v
       Monitor Stability
```

## 1. Verify the Monitoring Alert

When an ILL alert is received:

1. Identify the affected generic site/device/link from the approved monitoring system.
2. Check alert timestamp.
3. Confirm whether the alert is still active.
4. Check whether it is a link-down, flapping, packet-loss, or latency alert.
5. Check for related alerts on the same device or site.

Do not immediately assume that an alert is an ISP failure.

## 2. Check Device Reachability

Use the approved monitoring tools and, where authorized, basic connectivity testing.

Example:

```text
ping X.X.X.X
```

Possible observations:

- Device reachable
- Device unreachable
- Intermittent response
- Packet loss

Ping results should be correlated with interface status and monitoring data.

## 3. Check Interface Status

For Cisco devices:

```text
show ip interface brief
```

Then, when required:

```text
show interfaces <interface>
show interfaces description
```

Review:

- Interface state
- Line protocol
- Errors
- CRC
- Drops
- Resets
- Speed/duplex where relevant

## 4. Identify the ILL Condition

### ILL Link Down

The monitored ILL service or associated interface is unavailable.

Basic flow:

```text
Alert
 -> Verify
 -> Device Check
 -> Interface Check
 -> Troubleshoot
 -> ISP Escalation
 -> Restoration
 -> Verify
```

### ILL Link Flapping

The link repeatedly changes between up and down states.

Check:

- Monitoring history
- Interface logs
- Interface resets
- Error counters
- Physical/link indicators where available

### ILL Packet Loss

Check:

- Packet-loss percentage
- Test duration
- Monitoring history
- Interface errors
- Multiple destinations where appropriate

### ILL High Latency

Check:

- Current latency
- Historical latency
- Packet loss
- Interface health
- Network path where authorized

## 5. Basic Cisco Checks

Common read-only commands include:

```text
show ip interface brief
show interfaces <interface>
show interfaces description
show interfaces counters errors
show logging
```

Command availability varies by platform.

Use only the commands relevant to the incident.

## 6. ISP Escalation

If the issue requires ISP investigation, follow the organization's approved escalation process.

Provide relevant information such as:

- Service type: ILL
- Issue type
- Issue start time
- Current link status
- Device/interface observations
- Packet-loss or latency results where relevant
- Troubleshooting already completed
- Monitoring evidence available internally

Request:

- ISP ticket/reference
- Current status
- Troubleshooting progress
- ETR when available
- Next update time

Do not publish real ISP ticket numbers or customer information in this repository.

## 7. ISP Follow-Up

During follow-up:

1. Check the current ticket status.
2. Confirm whether ISP troubleshooting is in progress.
3. Record the latest update internally.
4. Record ETR if provided.
5. Schedule or remember the next follow-up according to the approved process.
6. Escalate through the defined contact path if the issue remains unresolved.

Use factual and timestamped updates.

## 8. Restoration Verification

When the ISP reports restoration:

1. Check the monitoring alert.
2. Confirm device reachability.
3. Check interface status.
4. Verify packet loss if relevant.
5. Verify latency if relevant.
6. Confirm the alert has cleared.
7. Continue monitoring for stability.
8. Update the ticket.

Do not close the incident only because the ISP reports restoration.

## 9. Generic ILL Link-Down Example

**Scenario:** A generic ILL service generates a link-down alert.

### Detection

Monitoring reports an active ILL link-down alert.

### Verification

Check:

```text
Device reachability
Interface status
Monitoring alert state
Related alerts
```

### CLI Checks

```text
show ip interface brief
show interfaces <interface>
show interfaces description
```

### Escalation

If the issue requires ISP support:

- Raise/update the approved ISP ticket.
- Provide the verified symptoms.
- Record the ISP reference internally.
- Track status and ETR.

### Restoration

After the ISP reports recovery:

- Verify interface state.
- Verify reachability.
- Check monitoring.
- Check stability.
- Update the incident.

## 10. Generic ILL Performance Example

**Scenario:** Monitoring reports packet loss on an ILL link.

Check:

```text
Current packet loss
Historical packet loss
Device reachability
Interface errors
Interface resets
Latency
```

If the issue persists, collect the relevant evidence and follow the approved escalation process.

Avoid assuming that packet loss automatically means an ISP fault.

## 11. ILL Incident Documentation

A useful internal incident record can contain:

| Field | Example |
|---|---|
| Service | ILL |
| Issue | Link Down |
| Detection Time | YYYY-MM-DD HH:MM |
| Current Status | Investigating |
| Verification | Device/interface checked |
| Action | ISP escalation |
| ISP Status | Investigation in progress |
| ETR | As provided by ISP |
| Restoration | YYYY-MM-DD HH:MM |
| Verification | Monitoring + interface checked |

All examples are generic.

## 12. ILL Monitoring Checklist

### Alert

- [ ] Alert received
- [ ] Alert timestamp checked
- [ ] Alert type identified
- [ ] Alert still active/cleared status verified

### Device

- [ ] Device reachability checked
- [ ] Interface status checked
- [ ] Interface details checked
- [ ] Relevant errors checked

### Service

- [ ] Packet loss checked where relevant
- [ ] Latency checked where relevant
- [ ] Flapping history checked where relevant

### ISP

- [ ] ISP escalation completed when required
- [ ] Ticket/reference recorded internally
- [ ] Current status recorded
- [ ] ETR recorded when provided
- [ ] Follow-up completed

### Restoration

- [ ] Monitoring alert cleared
- [ ] Interface restored
- [ ] Reachability verified
- [ ] Performance checked
- [ ] Stability monitored
- [ ] Ticket updated

## Important NOC Practices

- Verify before escalating.
- Use timestamps for all major events.
- Separate link-down, packet-loss, latency, and flapping symptoms.
- Do not assume the ISP is responsible without evidence.
- Keep ISP communication factual and concise.
- Track ETR and follow-up times.
- Verify restoration from the monitoring/device side.
- Protect customer and circuit information.

## Confidentiality

Never publish:

- Customer names
- Real customer/production IP addresses
- ILL circuit IDs
- ISP ticket numbers
- Phone numbers
- Email addresses
- Credentials
- Monitoring screenshots containing real data
- Internal topology
- Device configurations
- Proprietary ISP information
- Company-confidential information

Use placeholders:

```text
Customer-Site-A
ILL-Circuit-XXXX
Device-A
Interface-X
X.X.X.X
Generic-ISP
ISP-Ticket-XXXX
```

## Key Takeaways

- ILL monitoring starts with alert verification.
- Device and interface checks help establish the current condition.
- Performance symptoms should be verified with monitoring and testing.
- ISP escalation should contain clear evidence.
- ETR and follow-up status should be tracked.
- Restoration must be verified before incident closure.
- Production and customer information must remain confidential.

## Related Topics

- Link Down Troubleshooting
- Packet Loss and High Latency Troubleshooting
- Link Status and Flapping
- ISP Coordination
- Ticketing
- RCA
- Monitoring Logs and Documentation

## Author

Mohamed Ashik

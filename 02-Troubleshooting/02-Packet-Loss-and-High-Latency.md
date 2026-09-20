# Packet Loss and High Latency Troubleshooting

## Overview

Packet loss and high latency can affect network performance and may be caused by congestion, physical link problems, interface errors, routing/path issues, or problems outside the local network.

In NOC operations, the objective is to verify the symptom, collect evidence, identify the affected path or device, escalate when required, and confirm recovery.

This document uses only generic examples and sanitized values.

## Objectives

- Identify packet loss and high latency symptoms
- Verify whether the issue is persistent or temporary
- Compare monitoring results with basic connectivity tests
- Check device and interface health
- Collect useful evidence for escalation
- Coordinate with the ISP when required
- Verify service stability after recovery

## Basic Troubleshooting Flow

```
Alert / User Report
        |
        v
Verify Packet Loss / Latency
        |
        v
Check Device Reachability
        |
        v
Compare Multiple Tests
        |
        v
Check Interface Statistics
        |
        v
Identify Possible Network Segment
        |
        +---- Local Issue ----> Internal Troubleshooting
        |
        +---- External/ISP ----> ISP Escalation
        |
        v
Monitor / Follow Up
        |
        v
Verify Recovery
        |
        v
Document / Update Ticket
```

## 1. Understand the Symptoms

### Packet Loss

Packet loss occurs when packets sent across a network path do not reach the destination successfully.

Possible symptoms:

- Intermittent connectivity
- Slow application response
- Voice/video quality issues
- Repeated monitoring alerts
- Ping requests timing out

### High Latency

Latency is the time taken for traffic to travel between endpoints.

Possible symptoms:

- Slow response
- Increased application delay
- High ping response times
- Performance degradation

Packet loss and latency can occur together, but they are not the same condition.

## 2. Verify from Monitoring

Check the monitoring platform for:

- Current packet-loss percentage
- Current latency
- Alert start time
- Alert duration
- Whether the alert is active or cleared
- Historical pattern
- Whether nearby devices or links show similar symptoms

Do not treat a single temporary spike as confirmed persistent degradation without further verification.

## 3. Basic Ping Test

Use a permitted test target:

```text
ping X.X.X.X
```

For a Windows endpoint, a generic example is:

```text
ping -n 20 X.X.X.X
```

Observe:

- Packets sent
- Packets received
- Packets lost
- Minimum response time
- Maximum response time
- Average response time

Example interpretation:

```text
0% loss       -> No packet loss observed during the test
Some loss     -> Possible intermittent packet loss
High loss     -> Significant connectivity problem may exist
High latency  -> Possible path, congestion, or network performance issue
```

Ping results are only one piece of evidence and should be correlated with monitoring and interface information.

## 4. Check Device Reachability

First determine whether the device itself is reachable.

Possible cases:

### Case A: Device Reachable + High Latency

The device responds, but response time is higher than expected.

Next checks:

- Repeat the test
- Compare with monitoring history
- Check interface statistics
- Check whether multiple destinations are affected
- Check for congestion or path-related symptoms

### Case B: Device Reachable + Packet Loss

The device responds intermittently.

Next checks:

- Repeat the test
- Check loss percentage
- Check interface errors
- Check link stability
- Review monitoring history

### Case C: Device Unreachable

The issue may be broader than packet loss alone.

Check:

- Device status
- Interface status
- Upstream connectivity
- Monitoring alerts
- Other affected devices

## 5. Check Cisco Interface Statistics

Use:

```text
show ip interface brief
```

Then inspect the affected interface:

```text
show interfaces <interface>
```

Look for:

- Input errors
- CRC errors
- Output errors
- Interface resets
- Drops
- Packet counters
- Speed
- Duplex
- Interface status
- Line protocol status

Example:

```text
show interfaces GigabitEthernet0/1
```

Increasing error or drop counters can provide evidence of an interface or link problem, but the exact root cause must be confirmed.

## 6. Check Interface Description

Use:

```text
show interfaces description
```

This can help identify the role of the interface and support correlation with the affected service or link.

Only use authorized production information. Do not copy real customer or internal descriptions into a public repository.

## 7. Compare Multiple Destinations

A useful troubleshooting technique is to compare connectivity to more than one permitted destination.

Generic example:

```text
Local Gateway      -> Test result
Upstream Device    -> Test result
Remote Endpoint    -> Test result
```

Possible interpretation:

- Loss only to one destination → destination/path-specific issue may exist
- Loss to multiple destinations → broader path or local issue may exist
- High latency to all destinations → local link, congestion, or upstream path may require investigation

These are troubleshooting indicators, not automatic root-cause conclusions.

## 8. Check for Link Flapping

Packet loss can sometimes occur when an interface is unstable.

Review monitoring history and interface information for:

- Repeated up/down events
- Interface resets
- Increasing error counters
- Repeated alerts

Useful commands:

```text
show interfaces <interface>
show interfaces description
show logging
```

Use `show logging` only when authorized and supported by the device/environment.

## 9. Local vs ISP Investigation

### Possible Local Indicators

- Interface errors
- Local device instability
- Local congestion
- Physical connectivity issue
- Multiple local interfaces affected

### Possible ISP/External Indicators

- Local device and interface appear healthy
- Packet loss occurs beyond the local segment
- External circuit shows degradation
- ISP-side investigation is required

The actual cause should be established from collected evidence and the approved troubleshooting/escalation process.

## 10. ISP Escalation

When ISP involvement is required, provide useful information through the approved ticketing process:

- Service/link type
- Issue start time
- Packet-loss observation
- Latency observation
- Test results
- Interface status
- Relevant error observations
- Monitoring history
- Previous troubleshooting performed

Request status and ETR when applicable.

Never publish real circuit IDs, ticket numbers, customer details, or contact information in this repository.

## 11. Restoration Verification

After the issue is reported as resolved:

1. Check monitoring status.
2. Repeat the connectivity test.
3. Confirm packet loss has returned to an acceptable level.
4. Check latency.
5. Check interface status and relevant counters.
6. Continue monitoring for stability.
7. Update the incident/ticket.

Do not close an incident based only on an external restoration message.

## 12. Generic Incident Example

**Scenario:** Monitoring reports high packet loss on a generic WAN connection.

**Step 1:** Verify the alert and timestamp.

**Step 2:** Check whether the issue is still active.

**Step 3:** Perform an authorized ping test.

**Step 4:** Record packet loss and response times.

**Step 5:** Check device reachability.

**Step 6:** Check:

```text
show ip interface brief
show interfaces <interface>
show interfaces description
```

**Step 7:** Review monitoring history for recurring patterns.

**Step 8:** Determine whether internal troubleshooting or ISP escalation is required.

**Step 9:** Update the ticket with evidence and follow-up information.

**Step 10:** After recovery, repeat the tests and monitor stability.

## Troubleshooting Checklist

- [ ] Alert verified
- [ ] Start time recorded
- [ ] Packet loss checked
- [ ] Latency checked
- [ ] Device reachability verified
- [ ] Connectivity test repeated
- [ ] Interface status checked
- [ ] Interface errors checked
- [ ] Monitoring history reviewed
- [ ] Multiple destinations compared where appropriate
- [ ] Local vs external issue considered
- [ ] Ticket updated
- [ ] ISP escalation completed when required
- [ ] ETR/ETA recorded when provided
- [ ] Recovery verified
- [ ] Stability monitored

## Important NOC Practices

- Verify symptoms before escalation.
- Record exact timestamps.
- Compare current results with historical monitoring data.
- Do not assume packet loss always means an ISP fault.
- Do not assume high latency always means congestion.
- Use multiple sources of evidence.
- Keep ticket updates factual and concise.
- Verify recovery before closure.
- Protect customer and production information.

## Confidentiality

Do not upload:

- Customer names
- Real production IP addresses
- Circuit IDs
- Ticket IDs/numbers
- Phone numbers
- Email addresses
- Credentials or passwords
- Monitoring screenshots containing real data
- Internal topology
- Firewall screenshots
- Proprietary configurations
- Company-confidential information

Use placeholders such as:

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

- Packet loss and latency must be verified before escalation.
- Ping tests provide useful evidence but should not be used alone.
- Interface statistics can help identify errors or instability.
- Comparing multiple destinations can help narrow the affected network segment.
- ISP escalation should include clear technical evidence.
- Recovery should be verified through monitoring and testing.
- Accurate documentation improves troubleshooting and handover quality.

## Related Topics

- Link Down Troubleshooting
- Link Status and Flapping
- Basic Monitoring Workflow
- Alert Verification and Classification
- Monitoring Logs and Documentation
- ISP Coordination
- Ticketing
- RCA

## Author

Mohamed Ashik

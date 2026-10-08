# P2P Monitoring and Troubleshooting

## Overview

A Point-to-Point (P2P) link provides a dedicated connection between two network locations or endpoints. In NOC operations, P2P links are monitored for availability, stability, packet loss, latency, and recurring connectivity issues.

This document describes a generic P2P monitoring and troubleshooting workflow based on practical NOC operations.

> Important: All examples are generic and sanitized. No customer information, circuit IDs, production IP addresses, ticket numbers, or confidential company data are included.

## Objectives

- Understand basic P2P link monitoring
- Identify P2P availability issues
- Verify link-down and flapping alerts
- Check packet loss and latency
- Perform basic device/interface verification
- Coordinate with the ISP when required
- Track incidents and restoration
- Verify service stability after recovery

## What is a P2P Link?

A **Point-to-Point (P2P)** link is a dedicated network connection between two endpoints.

~~~text
Endpoint-A
    |
    |  P2P Link
    |
Endpoint-B
~~~

Depending on the network design, the endpoints may be routers, switches, firewalls, or other network devices.

## P2P Monitoring Parameters

| Parameter | Purpose |
|---|---|
| Link Status | Check whether the link is operational |
| Reachability | Verify endpoint connectivity |
| Packet Loss | Identify dropped packets |
| Latency | Identify increased response time |
| Flapping | Detect repeated link state changes |
| Interface Errors | Identify possible physical/link problems |
| Alert Status | Track active and cleared events |
| Stability | Confirm service remains healthy after recovery |

## Common P2P Issues

### 1. Link Down

The P2P connection is unavailable or an interface is operationally down.

Possible areas to investigate:

- Local interface
- Remote endpoint
- Physical connectivity
- ISP/service path
- Device health
- Power or hardware condition

### 2. Link Flapping

The link repeatedly changes between up and down.

Possible indicators:

- Repeated monitoring alerts
- Interface state changes
- Physical instability
- Interface errors
- ISP/service instability

### 3. Packet Loss

Packets are being dropped between the monitored endpoints.

Possible causes include:

- Interface errors
- Congestion
- Physical problems
- Device issues
- ISP/service-path issues

### 4. High Latency

Traffic is reaching the destination, but response time is higher than expected.

Possible areas to investigate:

- Link utilization
- Congestion
- Interface errors
- Routing path
- ISP/service path
- Remote endpoint condition

## P2P Monitoring Workflow

~~~text
Monitor
   |
   v
Alert Detected
   |
   v
Verify Alert
   |
   v
Identify P2P Endpoint / Link
   |
   v
Perform Basic Checks
   |
   +---- Local Issue ----> Troubleshoot / Escalate Internally
   |
   +---- ISP Suspected --> Raise ISP Ticket
                              |
                              v
                         Follow Up / ETR
                              |
                              v
                         Restoration
                              |
                              v
                       Verify Stability
                              |
                              v
                           Close
~~~

## 1. Verify the Alert

Before taking action:

- Check the monitoring dashboard.
- Confirm the alert is active.
- Check whether the alert is cleared.
- Identify the affected P2P service.
- Note the detection time.
- Check for related alerts.

Avoid treating a single transient alert as a confirmed long-duration outage without verification.

## 2. Identify the Affected Link

Use approved internal records to identify:

- P2P service
- Local endpoint
- Remote endpoint
- Associated interface
- Service provider
- Monitoring object

For public documentation, use placeholders such as:

~~~text
P2P-Service-A
Endpoint-A
Endpoint-B
Interface-X
Generic-ISP
~~~

## 3. Basic Device Verification

For Cisco devices, commonly used commands include:

~~~text
show ip interface brief
show interfaces <interface>
show interfaces description
show logging
show interfaces counters errors
~~~

These commands can help determine:

- Interface state
- Protocol state
- Errors
- Drops
- Interface resets
- Recent state changes
- Relevant log messages

## 4. Reachability Verification

A basic ping test can help confirm connectivity.

Example:

~~~text
ping X.X.X.X
~~~

Possible outcomes:

### Successful

~~~text
Endpoint is reachable
~~~

Continue checking whether the service is stable and whether the original alert has cleared.

### Failed

~~~text
Endpoint is not reachable
~~~

Continue with interface, device, path, and ISP investigation according to the network procedure.

> Ping alone does not prove that the complete service is healthy. It should be combined with monitoring and interface verification.

## 5. Link Flapping Verification

For suspected P2P flapping:

1. Check monitoring alert history.
2. Check interface state.
3. Review interface counters.
4. Check device logs.
5. Identify repeated up/down events.
6. Record the relevant timestamps.
7. Correlate with ISP/service events where applicable.

Generic example:

~~~text
10:10 - Link Down
10:12 - Link Up
10:18 - Link Down
10:20 - Link Up
10:27 - Link Down
~~~

Repeated state changes indicate instability and require further investigation rather than immediate closure.

## 6. Packet Loss Verification

When packet loss is reported:

- Verify the alert.
- Test reachability.
- Check whether loss is continuous or intermittent.
- Compare multiple destinations when appropriate.
- Check interface errors and drops.
- Check for link flapping.
- Check monitoring history.
- Determine whether the issue appears local or service-provider related.

Generic observation:

~~~text
Packet Loss: Observed
Interface Errors: No abnormal errors observed
Flapping: Not observed
Further Investigation: Required
~~~

## 7. High Latency Verification

When latency increases:

1. Confirm the monitoring alert.
2. Check current latency.
3. Compare with normal observations.
4. Check packet loss.
5. Check interface errors.
6. Check utilization where available.
7. Check for routing or path changes.
8. Escalate to the ISP if the evidence indicates a service-path issue.

## 8. Local vs ISP Investigation

A NOC should avoid immediately blaming the ISP.

### Possible Local Indicators

- Local interface administratively down
- Local interface errors
- Device issue
- Local physical connectivity problem
- Local configuration issue
- Device resource problem

### Possible ISP / Service Indicators

- Local interface appears healthy
- Endpoint remains unreachable
- Service alert continues
- Multiple checks indicate the local device is operational
- ISP-side investigation is required

These are indicators, not definitive proof. Follow the organization's troubleshooting and escalation procedure.

## 9. ISP Ticket Raising

If the issue requires ISP assistance, provide:

- Service type: P2P
- Issue type
- Detection time
- Affected service reference
- Relevant endpoint/interface information
- Basic verification completed
- Monitoring observation
- Request for investigation
- Request for ISP ticket/reference
- Request for ETR

Generic format:

~~~text
Service Type: P2P
Issue: Link Down
Detection Time: YYYY-MM-DD HH:MM
Status: Down
Verification: Basic device/interface checks completed
Request: Please investigate and provide ticket reference and ETR.
~~~

Do not publish real service identifiers or ticket numbers in this repository.

## 10. ISP Follow-up

After raising the ticket:

- Record the ISP reference in the approved internal system.
- Track the latest ISP status.
- Request ETR when applicable.
- Follow the approved follow-up interval.
- Escalate if the expected restoration timeline is missed.
- Record each important update with a timestamp.

Generic note:

~~~text
Time: HH:MM
ISP Status: Investigation in progress
ETR: Pending
Next Action: Follow up as per escalation process
~~~

## 11. Restoration Verification

An ISP may report that the P2P service has been restored.

Do not close the incident immediately.

Verify:

- Monitoring alert cleared
- Endpoint reachable
- Interface operational
- Packet loss normal
- Latency within expected range
- No repeated flapping
- Service remains stable

Generic verification:

~~~text
Monitoring: Normal
Reachability: Successful
Interface: Up / Up
Packet Loss: No abnormal loss observed
Latency: Within expected observation
Stability: Monitoring continued
~~~

## 12. Post-Restoration Monitoring

After recovery:

- Continue monitoring the P2P link.
- Watch for repeated up/down events.
- Check for packet loss.
- Check latency where relevant.
- Verify related alerts remain clear.
- Record restoration time.
- Complete the approved ticket closure process.

A link that returns briefly and fails again should be treated as an ongoing incident.

## 13. Generic P2P Incident Example

**Scenario:** P2P link-down alert.

~~~text
09:00 - Monitoring detects P2P link-down alert
09:05 - Alert verified
09:10 - Endpoint and interface checks completed
09:15 - Local checks do not identify an immediate fault
09:20 - ISP ticket raised
09:25 - ISP reference received
10:00 - ISP follow-up completed
10:05 - ETR received
11:00 - Follow-up completed
11:30 - ISP reports restoration
11:35 - NOC verifies connectivity
11:50 - Stability monitoring completed
12:00 - Incident updated / closure process started
~~~

Times are illustrative only.

## P2P Monitoring Checklist

### Alert Verification

- [ ] Alert confirmed
- [ ] Detection time recorded
- [ ] Affected P2P service identified
- [ ] Related alerts checked
- [ ] Alert history reviewed

### Technical Verification

- [ ] Endpoint reachability checked
- [ ] Interface status checked
- [ ] Interface counters checked
- [ ] Device logs checked
- [ ] Packet loss checked where relevant
- [ ] Latency checked where relevant
- [ ] Flapping checked

### ISP Coordination

- [ ] ISP requirement identified
- [ ] Ticket raised
- [ ] ISP reference recorded
- [ ] ETR requested
- [ ] Follow-up completed
- [ ] Escalation performed if required

### Restoration

- [ ] Monitoring alert cleared
- [ ] Endpoint reachable
- [ ] Interface operational
- [ ] Packet loss normal
- [ ] Latency normal where applicable
- [ ] Stability observed
- [ ] Ticket updated

## Practical NOC Notes

- Verify before escalating.
- Record exact timestamps.
- Do not assume every P2P issue is an ISP issue.
- Use monitoring data together with device-level checks.
- Treat flapping as instability, not a normal restoration.
- ETR is an estimate, not proof of recovery.
- Verify the service independently after ISP restoration.
- Maintain a clear incident timeline for shift handover.

## Confidentiality

Never publish:

- Customer names
- Real P2P circuit IDs
- Production IP addresses
- ISP ticket numbers
- Internal ticket numbers
- Phone numbers
- Email addresses
- Credentials
- Monitoring screenshots containing real data
- Internal topology
- ISP confidential information
- Company-confidential information

Use placeholders:

~~~text
Customer-Site-A
P2P-Service-XXXX
Ticket-XXXX
ISP-Ticket-XXXX
Generic-ISP
Endpoint-A
Endpoint-B
Interface-X
X.X.X.X
~~~

## Key Takeaways

- P2P monitoring focuses on availability, reachability, stability, packet loss, and latency.
- Alert verification should happen before escalation.
- Cisco interface and log checks provide useful local evidence.
- ISP tickets should contain concise and relevant technical information.
- ETR and follow-up status should be tracked until restoration.
- Restoration must be verified from the NOC side.
- Continued monitoring is important after recovery.

## Related Topics

- ILL Monitoring and Troubleshooting
- ILL Ticket and ISP Follow-up Workflow
- ISP Coordination
- Ticketing
- Monitoring Logs and Documentation
- RCA

## Author

Mohamed Ashik

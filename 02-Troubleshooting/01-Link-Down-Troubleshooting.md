# Link Down Troubleshooting

## Overview

A link-down incident means a monitored network link, interface, or circuit is currently unavailable. In NOC operations, the first priority is to verify the alert, identify the affected layer or device, perform basic troubleshooting, raise or update the ticket, coordinate with the ISP when required, and confirm restoration.

This document describes a generic troubleshooting approach without using real customer, circuit, IP, ticket, or internal company information.

## Objectives

- Verify whether the link-down alert is genuine
- Identify the affected device or interface
- Check device and interface reachability
- Perform basic Cisco troubleshooting
- Determine whether ISP escalation is required
- Document actions and ticket updates
- Verify service restoration

## Basic Troubleshooting Flow

```
Link Down Alert
      |
      v
Verify Alert
      |
      v
Check Device Reachability
      |
      v
Check Interface Status
      |
      v
Check Interface Details / Errors
      |
      v
Identify Possible Cause
      |
      +---- Local Issue ----> Troubleshoot / Escalate Internally
      |
      +---- ISP/Link Issue --> Raise / Update ISP Ticket
      |
      v
Follow Up / Track ETA or ETR
      |
      v
Verify Restoration
      |
      v
Continue Monitoring
      |
      v
Close / Update Ticket
```

## 1. Verify the Alert

Before escalating a link-down alert, verify:

- Device name
- Interface or link name
- Alert timestamp
- Current alert status
- Whether the alert is still active
- Whether the alert cleared automatically
- Whether other interfaces or devices at the same site are affected

Do not immediately assume that every alert represents a confirmed outage.

## 2. Check Device Reachability

Use monitoring tools first and then perform basic connectivity checks when access is available.

Example:

```bash
ping X.X.X.X
```

Possible observations:

- Ping successful → device may still be reachable
- Ping unsuccessful → device or path may be unreachable
- Intermittent replies → possible packet loss or instability

Ping alone does not prove that a specific interface or service is healthy.

## 3. Check Interface Status

On Cisco devices:

```text
show ip interface brief
```

Example sanitized output:

```text
Interface              IP-Address      OK? Method Status                Protocol
GigabitEthernet0/0     X.X.X.X         YES manual up                    up
GigabitEthernet0/1     unassigned      YES unset   down                  down
```

The important fields are:

- Status
- Protocol
- IP address
- Interface name

A common condition is:

```text
Status: down
Protocol: down
```

This can indicate a physical/link-level problem, but the exact cause must be verified.

## 4. Check Interface Details

Use:

```text
show interfaces <interface>
```

Example:

```text
show interfaces GigabitEthernet0/1
```

Look for:

- Interface status
- Line protocol status
- Input errors
- Output errors
- CRC errors
- Interface resets
- Packet counters
- Speed
- Duplex
- Last input/output information

These details help determine whether the issue may be related to physical connectivity, errors, or interface instability.

## 5. Check Interface Description

Use:

```text
show interfaces description
```

This can help identify the purpose of an interface and whether it is associated with a WAN, LAN, uplink, or other connection.

Use only authorized information from the production environment. Never publish real internal descriptions or customer details in a public learning repository.

## 6. Check for Local vs ISP Issue

### Possible Local-Side Indicators

- Device is down
- Interface is administratively down
- Physical connection problem
- Local interface errors
- Power-related issue
- Configuration-related issue
- Multiple local interfaces affected

### Possible ISP/External-Link Indicators

- Local device is reachable but WAN link remains down
- Interface is up/down or repeatedly flapping
- External circuit is unavailable
- ISP-side confirmation is required
- Multiple monitoring checks indicate the same circuit is affected

These are indicators, not automatic conclusions. The actual cause should be confirmed through available evidence and coordination.

## 7. Ticket Raising / Updating

If the issue requires external coordination, create or update the appropriate ticket using the organization's approved process.

A generic ticket update can include:

- Incident type: Link Down
- Affected service: Generic WAN/Internet Link
- Detection time
- Current status
- Verification performed
- Troubleshooting performed
- ISP/vendor escalation status
- ETA/ETR, if provided
- Next follow-up time

Never place real ticket numbers, customer names, circuit IDs, contact numbers, or internal IP addresses in this public repository.

## 8. ISP Follow-Up

During follow-up, confirm:

- Ticket/reference number through the approved internal system
- Current issue status
- Troubleshooting status
- Estimated restoration time (ETR), if available
- Next update time
- Whether ISP requires any additional information

Document each important update with a timestamp in the internal ticketing system.

## 9. Restoration Verification

When the ISP or internal team reports restoration:

1. Check the monitoring alert.
2. Confirm the interface status.
3. Check device reachability.
4. Verify packet loss/latency where applicable.
5. Confirm that the service remains stable.
6. Continue monitoring for recurrence.
7. Update the ticket with the restoration details.

Do not close an incident only because an external party says the link is restored. Verify from the monitoring or device side whenever possible.

## 10. Link Down vs Link Flapping

### Link Down

The interface or monitored circuit remains unavailable.

Typical flow:

```
Alert -> Verify -> Troubleshoot -> Escalate -> Restore -> Verify
```

### Link Flapping

The link repeatedly changes between up and down states.

Typical flow:

```
Alert -> Verify History -> Check Interface -> Check Errors
       -> Identify Pattern -> Escalate if Required
       -> Monitor Stability
```

For flapping incidents, historical alerts and interface counters can provide useful evidence.

## 11. Generic Incident Example

**Scenario:** A generic WAN interface generates a link-down alert.

**Step 1:** Verify the alert in the monitoring platform.

**Step 2:** Check whether the alert is still active.

**Step 3:** Check device reachability.

**Step 4:** Run:

```text
show ip interface brief
show interfaces <interface>
show interfaces description
```

**Step 5:** Identify whether the issue appears local or requires external/ISP coordination.

**Step 6:** Raise or update the appropriate ticket.

**Step 7:** Follow up for status and ETR when applicable.

**Step 8:** After restoration, verify reachability and interface status.

**Step 9:** Continue monitoring for stability.

## Troubleshooting Checklist

- [ ] Alert verified
- [ ] Alert timestamp recorded
- [ ] Device reachability checked
- [ ] Interface status checked
- [ ] Interface details checked
- [ ] Interface errors checked
- [ ] Local issue considered
- [ ] ISP involvement identified
- [ ] Ticket raised/updated
- [ ] Follow-up completed
- [ ] ETR/ETA recorded when provided
- [ ] Restoration verified
- [ ] Link stability monitored
- [ ] Ticket/documentation updated

## Important NOC Practices

- Verify before escalating.
- Record timestamps accurately.
- Use clear and factual ticket updates.
- Do not assume the root cause without evidence.
- Follow the approved escalation process.
- Confirm restoration from the monitoring/device side.
- Maintain proper shift handover information.
- Protect production and customer information.

## Confidentiality

Do not upload the following to a public repository:

- Customer names
- Real customer or production IP addresses
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

- A link-down alert must be verified before escalation.
- Device reachability and interface status are separate checks.
- Cisco interface commands help identify the current condition.
- Ticket updates should contain clear troubleshooting evidence.
- ISP coordination should include status and restoration tracking.
- Restoration must be verified before closure.
- Documentation should remain generic and free of confidential production data.

## Related Topics

- Basic Monitoring Workflow
- Alert Verification and Classification
- Monitoring Checklist
- Monitoring Logs and Documentation
- Link Status and Flapping
- Cisco Troubleshooting Commands
- ISP Coordination
- Ticketing

## Author

Mohamed Ashik

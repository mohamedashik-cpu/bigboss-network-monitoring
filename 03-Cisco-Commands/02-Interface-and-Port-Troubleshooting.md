# Interface and Port Troubleshooting Commands

## Overview

Interface and port checks are common tasks in NOC operations. When a link is down, flapping, showing errors, or behaving unexpectedly, Cisco interface commands can help identify the current operational state and collect troubleshooting evidence.

This document focuses on read-only troubleshooting commands and generic examples. Actual production changes must follow the organization's approved procedures.

## Objectives

- Check interface and port status
- Identify administrative and operational states
- Review interface errors and counters
- Check speed and duplex
- Review interface descriptions
- Identify link instability
- Collect evidence for ticketing and escalation
- Verify interface recovery

## Basic Interface Troubleshooting Flow

```text
Interface Alert
      |
      v
show ip interface brief
      |
      v
show interfaces description
      |
      v
show interfaces <interface>
      |
      v
Check Errors / Counters
      |
      v
Check Logs
      |
      v
Identify Possible Cause
      |
      +---- Local Issue
      |
      +---- Remote / ISP / Uplink Issue
      |
      v
Escalate / Follow Approved Procedure
      |
      v
Verify Recovery
```

## 1. Quick Interface Status

Use:

```text
show ip interface brief
```

This provides a quick summary of:

- Interface name
- IP address
- Status
- Protocol

Example:

```text
Interface              IP-Address      OK? Method Status                Protocol
GigabitEthernet0/0     X.X.X.X         YES manual up                    up
GigabitEthernet0/1     unassigned      YES unset   down                  down
GigabitEthernet0/2     unassigned      YES unset   administratively down down
```

### Common States

**up/up**

The interface and line protocol are operational.

**down/down**

The interface is not operational and the line protocol is also down. Physical connectivity or another lower-layer issue may need investigation.

**administratively down/down**

The interface has been administratively disabled.

Do not change the interface state without authorization.

## 2. Check Interface Description

Use:

```text
show interfaces description
```

This helps correlate the interface with its general role.

Example:

```text
Interface      Status       Protocol Description
Gi0/0          up           up       WAN
Gi0/1          up           up       LAN
Gi0/2          down         down     Uplink
```

Use only generic descriptions in public documentation.

## 3. Detailed Interface Information

Use:

```text
show interfaces <interface>
```

Example:

```text
show interfaces GigabitEthernet0/1
```

Review:

- Interface status
- Line protocol
- Hardware information
- MTU
- Bandwidth
- Input/output packets
- Input errors
- CRC errors
- Output errors
- Drops
- Interface resets
- Speed
- Duplex
- Last input/output information

## 4. Check Interface Errors

Use:

```text
show interfaces <interface>
```

Look for:

- Input errors
- CRC
- Frame errors
- Overruns
- Ignored packets
- Output errors
- Collisions where applicable
- Interface resets

Errors should be interpreted together with traffic levels, interface type, device platform, and monitoring history.

## 5. Check Error Counters

On supported Cisco platforms:

```text
show interfaces counters errors
```

This can provide a quick overview of interface-related error counters.

Command output and availability vary by platform.

## 6. Check Speed and Duplex

The detailed interface output can show:

```text
Speed
Duplex
```

Example:

```text
show interfaces GigabitEthernet0/1
```

Speed/duplex problems can affect performance and may contribute to errors or poor connectivity.

Do not manually change speed or duplex settings unless the organization's approved troubleshooting procedure requires it.

## 7. Check Interface Resets

The detailed interface output can contain reset information.

Example:

```text
show interfaces GigabitEthernet0/1
```

Frequent resets can be a useful indicator when investigating:

- Link instability
- Device/interface problems
- Physical connectivity issues
- Repeated link transitions

Correlate reset information with monitoring history and logs.

## 8. Check Interface Flapping

For a suspected flapping interface, check:

```text
show interfaces <interface>
show logging
```

Look for:

- Repeated state changes
- Interface resets
- Error counters
- Timestamps in logs

Example troubleshooting pattern:

```text
Interface Down
     |
Interface Up
     |
Interface Down
     |
Interface Up
```

Repeated transitions should be investigated rather than treated as a normal stable state.

## 9. Check Interface Logs

Use:

```text
show logging
```

Logs may show interface state changes or related system events.

Example generic event pattern:

```text
Interface changed state to down
Interface changed state to up
```

Do not copy real production logs into a public repository.

## 10. Switch Port Checks

For a switch port, useful commands may include:

```text
show interfaces status
show interfaces description
show interfaces <interface>
```

These can help identify:

- Port status
- VLAN information where displayed
- Speed
- Duplex
- Interface type
- Errors
- Port description

Exact output varies by switch model and software version.

## 11. MAC Address Check

When investigating a switch port and authorized access is available:

```text
show mac address-table interface <interface>
```

Example:

```text
show mac address-table interface GigabitEthernet0/1
```

This can help identify whether the switch has learned MAC addresses on that port.

Do not publish real MAC addresses from production devices.

## 12. Neighbor Verification

For CDP-enabled environments:

```text
show cdp neighbors
```

For detailed information:

```text
show cdp neighbors detail
```

For LLDP:

```text
show lldp neighbors
```

These commands can help identify connected network devices.

Use caution when documenting neighbor information because it may expose production topology.

## 13. Generic Link-Down Investigation

**Scenario:** Monitoring reports that a generic interface is down.

### Step 1 — Check summary

```text
show ip interface brief
```

### Step 2 — Check description

```text
show interfaces description
```

### Step 3 — Check detailed status

```text
show interfaces <interface>
```

### Step 4 — Check errors

Review:

- Input errors
- CRC
- Output errors
- Drops
- Resets

### Step 5 — Check logs

```text
show logging
```

### Step 6 — Determine next action

Based on the evidence, follow the approved internal troubleshooting or escalation process.

### Step 7 — Verify recovery

After restoration, confirm:

- Interface is up
- Protocol is up
- Errors are not continuously increasing
- Monitoring alert is cleared
- Service remains stable

## 14. Administrative Down vs Operational Down

| State | Meaning |
|---|---|
| up/up | Interface and protocol are operational |
| down/down | Interface and protocol are down |
| administratively down/down | Interface has been disabled by configuration |

The exact cause of a down state should be verified using the available evidence.

## 15. Read-Only Command Set

For routine investigation, the following commands are useful:

```text
show ip interface brief
show interfaces description
show interfaces <interface>
show interfaces counters errors
show interfaces status
show logging
show mac address-table interface <interface>
show cdp neighbors
show lldp neighbors
```

These are primarily information-gathering commands. Command availability depends on the Cisco platform.

## Ticket Documentation

When recording an interface issue, include:

- Detection time
- Device/interface reference through the approved internal system
- Current interface state
- Relevant command observations
- Error observations
- Monitoring status
- Troubleshooting performed
- Escalation status
- Restoration time
- Verification results

Keep the information factual and timestamped.

## Restoration Verification

After an interface is reported as restored:

1. Run `show ip interface brief`.
2. Confirm expected interface state.
3. Check relevant interface details.
4. Review monitoring status.
5. Check for recurring errors or flapping.
6. Verify the associated service where authorized.
7. Continue monitoring.
8. Update the ticket.

## Troubleshooting Checklist

- [ ] Interface alert verified
- [ ] Interface status checked
- [ ] Interface description checked
- [ ] Detailed interface output checked
- [ ] Error counters reviewed
- [ ] Speed/duplex reviewed where relevant
- [ ] Interface resets reviewed
- [ ] Logs checked
- [ ] Neighbor information checked where appropriate
- [ ] Local vs external issue considered
- [ ] Ticket updated
- [ ] Escalation completed when required
- [ ] Interface recovery verified
- [ ] Monitoring stability confirmed

## Important NOC Practices

- Prefer read-only commands for routine investigation.
- Do not issue configuration changes without authorization.
- Do not assume an interface error automatically identifies the root cause.
- Correlate CLI output with monitoring history.
- Record timestamps and observations clearly.
- Protect production topology and MAC information.
- Verify recovery before closing an incident.

## Confidentiality

Never publish:

- Customer names
- Production IP addresses
- Production MAC addresses
- Circuit IDs
- Ticket IDs/numbers
- Device credentials
- Passwords or secrets
- Production logs
- Internal topology
- Real interface descriptions
- Monitoring screenshots containing real data
- Proprietary configurations
- Company-confidential information

Use placeholders:

```text
Device-A
Interface-X
X.X.X.X
AA:BB:CC:DD:EE:FF
Generic-Site
Ticket-XXXX
```

## Key Takeaways

- `show ip interface brief` is a useful first-level interface check.
- `show interfaces <interface>` provides detailed operational information.
- Error counters and resets can provide useful troubleshooting evidence.
- Logs help correlate interface state changes with time.
- Switch port checks can include status, MAC learning, and neighbor information.
- Read-only investigation should come before configuration changes.
- Production information must remain confidential.

## Related Topics

- Cisco Device Health Check
- Link Down Troubleshooting
- Link Status and Flapping
- Packet Loss and High Latency Troubleshooting
- Monitoring Checklist
- ISP Coordination
- Ticketing
- RCA

## Author

Mohamed Ashik

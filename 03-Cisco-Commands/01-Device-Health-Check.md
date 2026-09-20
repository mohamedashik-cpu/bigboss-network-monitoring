# Cisco Device Health Check Commands

## Overview

Cisco device health checks are commonly performed in NOC operations to understand the current condition of routers and switches.

The purpose of a health check is to collect operational information such as device uptime, CPU and memory usage, interface status, errors, and hardware/environmental information where supported.

This document contains generic commands and sanitized examples. Always use commands according to the device model, IOS/IOS-XE version, access level, and organization-approved procedures.

## Objectives

- Check basic device health
- Verify device uptime
- Review CPU and memory utilization
- Check interface status and errors
- Review device logs
- Check hardware and environmental status
- Identify useful commands for routine NOC monitoring
- Document observations without exposing confidential information

## Basic Health Check Flow

```text
Device Reachability
       |
       v
System Information
       |
       v
Uptime
       |
       v
CPU / Memory
       |
       v
Interface Status
       |
       v
Interface Errors
       |
       v
Logs / Events
       |
       v
Hardware / Environment
       |
       v
Document Findings
```

## 1. Check Device Reachability

Before collecting information, verify that the device is reachable through the approved management method.

Example:

```text
ping X.X.X.X
```

A successful ping only confirms ICMP reachability. It does not prove that every service or interface on the device is healthy.

## 2. Check Device Information

Use:

```text
show version
```

Useful information may include:

- Cisco platform/model
- IOS or IOS-XE version
- System uptime
- Configuration register
- Hardware information

Avoid publishing real serial numbers, license information, internal hostnames, or other sensitive device details.

## 3. Check System Uptime

Uptime is normally visible in:

```text
show version
```

A recent uptime may indicate:

- Device reboot
- Power interruption
- Software reload
- Maintenance activity
- Unexpected restart

Uptime alone does not identify the cause of a reboot. Check logs and approved maintenance records when investigation is required.

## 4. Check CPU Utilization

A commonly used command is:

```text
show processes cpu
```

On supported platforms, you may also use:

```text
show processes cpu sorted
```

Look for:

- Current CPU utilization
- CPU utilization over time
- Processes consuming significant CPU

A temporary CPU spike is different from sustained high CPU utilization. Correlate with monitoring history and the time of the incident.

## 5. Check Memory Utilization

Use:

```text
show processes memory
```

On supported platforms, another useful command may be:

```text
show memory statistics
```

Check for:

- Available memory
- Used memory
- Processes consuming memory
- Unusual memory behavior

Exact command output varies by Cisco platform and software version.

## 6. Check Interface Status

Use:

```text
show ip interface brief
```

This provides a quick view of:

- Interface
- IP address
- Status
- Protocol

Example sanitized output:

```text
Interface              IP-Address      OK? Method Status                Protocol
GigabitEthernet0/0     X.X.X.X         YES manual up                    up
GigabitEthernet0/1     unassigned      YES unset   administratively down down
```

For NOC monitoring, pay attention to unexpected changes in status.

## 7. Check Interface Descriptions

Use:

```text
show interfaces description
```

This helps identify the purpose of interfaces and their current status.

Example:

```text
Interface      Status       Protocol Description
Gi0/0          up           up       WAN
Gi0/1          up           up       LAN
```

Descriptions shown here are generic examples only.

## 8. Check Detailed Interface Health

Use:

```text
show interfaces <interface>
```

Example:

```text
show interfaces GigabitEthernet0/0
```

Review:

- Interface status
- Line protocol
- Input packets
- Output packets
- Input errors
- Output errors
- CRC errors
- Drops
- Interface resets
- Speed
- Duplex
- Last input/output information

Increasing errors or resets may require deeper investigation.

## 9. Check Interface Counters

Interface counters can help identify traffic or error conditions.

Use:

```text
show interfaces counters errors
```

Command availability can vary by platform.

Look for:

- CRC errors
- Input errors
- Output errors
- Other interface-specific errors

Do not conclude root cause from a single counter without correlation.

## 10. Check Logs

Use:

```text
show logging
```

Logs may provide information about:

- Interface state changes
- Device events
- Authentication events
- System messages
- Previous errors

For a specific interface, search the available logs using the approved method.

Do not copy production logs into a public repository because they may contain internal addresses, hostnames, usernames, or other sensitive information.

## 11. Check Hardware / Environment

Depending on the Cisco platform, useful commands may include:

```text
show environment
show environment all
```

These can provide information about supported environmental conditions such as:

- Temperature
- Power supplies
- Fans
- Hardware sensors

Command availability varies by device model and software version.

## 12. Check Neighbor Information

For network topology or connected-device verification, authorized users may use:

```text
show cdp neighbors
```

For detailed information:

```text
show cdp neighbors detail
```

For LLDP-enabled environments:

```text
show lldp neighbors
```

These commands can reveal neighboring device information. Do not publish real production topology or neighbor details.

## 13. Check Configuration Carefully

A configuration review may use:

```text
show running-config
```

This command can contain sensitive information.

For a public learning repository, **do not copy production running configurations**.

Use sanitized examples or lab configurations instead.

## Quick Health Check Command Set

A generic routine checklist can start with:

```text
show version
show processes cpu
show processes memory
show ip interface brief
show interfaces description
show interfaces <interface>
show logging
show environment
show cdp neighbors
show lldp neighbors
```

Not every command is required for every incident. Select commands based on the monitoring alert and troubleshooting objective.

## Example NOC Health Check

**Scenario:** Monitoring reports an unusual condition on a generic router.

### Step 1 — Reachability

```text
ping X.X.X.X
```

### Step 2 — System Information

```text
show version
```

Check uptime and software information.

### Step 3 — CPU and Memory

```text
show processes cpu
show processes memory
```

### Step 4 — Interface Status

```text
show ip interface brief
show interfaces description
```

### Step 5 — Detailed Interface Check

```text
show interfaces <interface>
```

### Step 6 — Logs

```text
show logging
```

### Step 7 — Environmental Check

```text
show environment
```

### Step 8 — Document Findings

Record:

- Time of check
- Device role/name using approved internal systems
- Commands used
- Important observations
- Current status
- Further action required

## Command Selection by Situation

| Situation | Useful Commands |
|---|---|
| Device uptime | `show version` |
| CPU concern | `show processes cpu` |
| Memory concern | `show processes memory` |
| Interface status | `show ip interface brief` |
| Interface purpose/status | `show interfaces description` |
| Interface errors | `show interfaces <interface>` |
| Error counters | `show interfaces counters errors` |
| System events | `show logging` |
| Environment | `show environment` |
| CDP neighbors | `show cdp neighbors` |
| LLDP neighbors | `show lldp neighbors` |

## Important NOC Practices

- Use read-only show commands for routine checks whenever possible.
- Do not make configuration changes without authorization.
- Match commands to the device model and software version.
- Record timestamps for important observations.
- Compare current values with monitoring history where possible.
- Do not assume a high CPU or memory value is the root cause without evidence.
- Protect production configuration and logs.
- Escalate when the issue requires higher-level access or investigation.

## Confidentiality

Never publish:

- Production running configurations
- Real IP addresses
- Customer names
- Circuit IDs
- Ticket IDs/numbers
- Device credentials
- Passwords or secrets
- Serial numbers when sensitive
- Internal topology
- Production logs
- Monitoring screenshots
- Firewall configurations
- Company-confidential information

Use placeholders:

```text
Device-A
Interface-X
X.X.X.X
Generic-Site
Ticket-XXXX
```

## Key Takeaways

- Cisco health checks provide a structured view of device condition.
- Start with reachability and system information.
- Check CPU, memory, interfaces, errors, logs, and environment as required.
- Command availability varies by platform and software version.
- Health-check observations should be correlated with monitoring alerts.
- Use read-only commands for routine investigation.
- Never expose production configuration or confidential information.

## Related Topics

- Link Down Troubleshooting
- Packet Loss and High Latency Troubleshooting
- Device Reachability
- Link Status and Flapping
- Monitoring Checklist
- Ticketing
- RCA

## Author

Mohamed Ashik

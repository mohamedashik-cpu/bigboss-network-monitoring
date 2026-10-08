# RCA Overview and Workflow

Root Cause Analysis (RCA) is a structured process used to identify the actual reason behind a network or service incident and prevent the same issue from recurring.

This document focuses on practical NOC usage of RCA after incidents such as link down, link flapping, packet loss, high latency, device failure, or repeated connectivity issues.

> **Important:** This is a generic learning document. Do not store customer details, internal IP addresses, circuit IDs, ticket IDs, credentials, screenshots, or other confidential production information in this repository.

## 1. What is RCA?

**RCA = Root Cause Analysis**

RCA answers three important questions:

1. **What happened?**
2. **Why did it happen?**
3. **What can be done to prevent it from happening again?**

A ticket records and tracks the incident. An RCA focuses on understanding the underlying cause and prevention.

### Simple Example

**Symptom:** A network link went down.

**Resolution:** The ISP restored the link.

**Root Cause:** The ISP confirmed a physical fiber issue.

The restoration solves the immediate problem, while the RCA documents the confirmed cause and the actions needed to reduce recurrence.

## 2. When is RCA Required?

RCA may be required when an incident is:

- Major or business-impacting
- Repeated or recurring
- Related to a prolonged outage
- Caused by equipment or configuration failure
- Related to an ISP or third-party failure
- Associated with an SLA or service-impact concern
- Specifically requested by the customer, management, ISP, or internal team

Not every minor alert requires a detailed RCA.

## 3. Symptom vs Root Cause vs Resolution

| Term | Meaning | Example |
|---|---|---|
| Symptom | What was observed | Link Down |
| Root Cause | Why the incident happened | Confirmed fiber fault |
| Resolution | What restored the service | ISP repaired the fiber |

**Important:** Do not write an assumption as the root cause. If the cause is not confirmed, document it as unconfirmed.

## 4. RCA Workflow

**Incident → Collect Evidence → Build Timeline → Identify Cause → Confirm Root Cause → Define Corrective Action → Define Preventive Action → Document → Track**

### Step 1 — Identify the Incident

Record:

- Incident type
- Start time
- Detection time
- Affected service/link/device
- Impact
- Restoration time

Example:

```text
Incident: Network Link Down
Detection: 10:15
Restoration: 11:05
Impact: Connectivity unavailable
```

Use generic information in public documentation.

### Step 2 — Collect Evidence

Possible evidence sources:

- Monitoring alerts
- Device/interface status
- Ping results
- Interface statistics
- System logs
- Device health information
- ISP updates
- Ticket updates
- Maintenance/change information
- Restoration confirmation

Example Cisco checks:

```text
show ip interface brief
show interfaces <interface>
show logging
show interfaces counters errors
```

### Step 3 — Build the Incident Timeline

| Time | Event |
|---|---|
| 10:15 | Monitoring alert received |
| 10:18 | Alert verified |
| 10:22 | Local device/interface checks completed |
| 10:25 | ISP contacted |
| 10:30 | ISP ticket/reference received |
| 10:50 | ISP provided investigation update |
| 11:05 | Service restored |
| 11:10 | Restoration verified |
| 11:30 | Link monitored for stability |

Actual timestamps should come from reliable records.

### Step 4 — Identify the Root Cause

Common categories include:

**Physical**
- Fiber/cable fault
- Power failure
- Hardware failure
- Physical port problem

**Network**
- Interface failure
- Packet loss
- Routing issue
- Network device failure

**Configuration**
- Incorrect configuration
- Incorrect routing
- ACL-related issue
- Configuration change

**ISP / Third Party**
- ISP circuit failure
- Provider-side equipment issue
- Provider maintenance
- Last-mile problem

**Environmental**
- Power fluctuation
- Temperature-related device issue
- Other infrastructure conditions

Do not select a category only because it is likely. Use available evidence.

### Step 5 — Confirm the Root Cause

Use evidence such as:

- Device logs
- Monitoring history
- Interface statistics
- Change records
- ISP confirmation
- Maintenance records
- Engineering confirmation

If the cause is still unknown:

> **Root Cause:** Under investigation / not confirmed.

This is better than recording an incorrect root cause.

### Step 6 — Define Corrective Action

A **corrective action** addresses the identified issue.

Examples:

- Replace faulty hardware
- Repair damaged fiber
- Correct configuration
- Replace defective interface/module
- Fix routing configuration
- Resolve the provider-side fault

### Step 7 — Define Preventive Action

A **preventive action** reduces the chance of recurrence.

Examples:

- Improve monitoring
- Add redundancy
- Review configuration
- Schedule preventive maintenance
- Improve escalation procedures
- Replace unreliable equipment
- Track recurring incidents
- Review ISP performance

## 5. RCA Completion Checklist

- [ ] Incident is clearly described
- [ ] Impact is documented
- [ ] Timeline is complete
- [ ] Relevant evidence is collected
- [ ] Root cause is evidence-based
- [ ] Assumptions are clearly identified
- [ ] Corrective action is documented
- [ ] Preventive action is documented
- [ ] Restoration was verified
- [ ] Required owners/actions are identified
- [ ] Confidential information is removed

## 6. Generic RCA Format

```text
RCA Title:
Incident Type:
Incident Date:
Impact:
Detection Time:
Restoration Time:

Incident Summary:
[Brief description]

Timeline:
[Important events in chronological order]

Evidence:
[Monitoring / device / ISP / change evidence]

Root Cause:
[Confirmed cause or "Not confirmed"]

Corrective Action:
[Action taken to resolve the issue]

Preventive Action:
[Action to reduce recurrence]

Final Status:
[Closed / Monitoring / Pending Action]

Lessons Learned:
[What can be improved]
```

## 7. Practical NOC Example

### Incident

A monitored network link became unavailable.

### Investigation

1. Monitoring generated a link-down alert.
2. The alert was verified.
3. Device and interface status were checked.
4. Basic connectivity tests were performed.
5. No confirmed local configuration issue was identified.
6. The ISP was contacted.
7. The ISP investigated the circuit.
8. The service was restored.
9. Connectivity was verified after restoration.
10. The ISP later confirmed the underlying cause.

### RCA Summary

```text
Symptom:
Link Down

Resolution:
Service restored after ISP intervention.

Root Cause:
Use the confirmed ISP/device finding here.

Corrective Action:
Repair or correct the identified fault.

Preventive Action:
Monitor the link for recurrence and implement the recommended preventive measure.
```

This example intentionally avoids real company or customer information.

## 8. RCA and NOC Operations

A good RCA can help the NOC:

- Identify recurring problems
- Improve troubleshooting
- Reduce repeat incidents
- Improve escalation quality
- Improve monitoring
- Identify weak points
- Support management reporting
- Improve coordination with ISPs

## Key Takeaways

- RCA means **Root Cause Analysis**.
- A symptom is not the same as a root cause.
- Resolution is not automatically the root cause.
- Use evidence before confirming a cause.
- Never convert assumptions into confirmed facts.
- Corrective action fixes the current problem.
- Preventive action reduces future recurrence.
- Keep the RCA timeline clear and factual.
- If the cause is unknown, document it as unconfirmed.
- Never upload confidential production information to a public GitHub repository.

## Related Topics

- [NOC Ticketing Workflow](../07-Ticketing/01-NOC-Ticketing-Workflow.md)
- [Ticket RCA Requirement and Tracking](../07-Ticketing/06-Ticket-RCA-Requirement-and-Tracking.md)
- [Link Down Troubleshooting](../02-Troubleshooting/01-Link-Down-Troubleshooting.md)
- [ISP Coordination Workflow](../06-ISP-Coordination/01-ISP-Coordination-Workflow.md)

## Author

**Mohamed Ashik**

Network Monitoring | NOC | Networking | Cloud Security Learning

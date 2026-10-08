# Ticket Priority and Severity

## Overview

Ticket priority and severity help a NOC team decide how urgently an incident should be handled.

The exact definitions, SLA targets, and escalation rules vary between organizations. Always follow the organization's approved incident-management process.

> Important: The examples in this document are generic learning examples. Do not publish real customer details, production IP addresses, circuit IDs, ticket IDs, SLA values, or confidential information.

## Objectives

- Understand priority and severity
- Differentiate impact from urgency
- Identify factors that influence priority
- Understand generic P1/P2/P3/P4 handling
- Recognize when escalation may be required
- Document priority changes correctly

## Priority vs Severity

These terms are related but not always identical.

### Severity

Severity generally describes **how serious the technical or business impact is**.

Examples:

- Complete service outage
- Partial service degradation
- Packet loss
- High latency
- Single-user connectivity issue

### Priority

Priority generally describes **how urgently the incident should be handled**.

Priority can depend on:

- Business impact
- Service criticality
- Number of affected users/services
- Duration
- Availability of redundancy
- Security or operational risk
- Organization-defined SLA

A technically simple issue can still have high priority if the business impact is significant.

## Impact vs Urgency

### Impact

Impact answers:

> How many users, services, locations, or business functions are affected?

### Urgency

Urgency answers:

> How quickly does the issue need attention?

A useful conceptual model:

~~~text
Impact + Urgency + Service Criticality
                ↓
        Priority Decision
~~~

The final priority should follow the organization's process rather than personal judgment.

## Generic Priority Levels

| Priority | General Meaning | Example |
|---|---|---|
| P1 | Critical | Major service outage / critical business impact |
| P2 | High | Important service unavailable or significant impact |
| P3 | Medium | Limited impact or degraded service |
| P4 | Low | Minor issue, request, or informational task |

These are generic examples. Actual definitions may differ.

## P1 - Critical

A P1 incident usually involves severe business or service impact.

Possible examples:

- Major network outage
- Critical site connectivity unavailable
- Multiple important services affected
- No effective redundancy for a critical service
- Major infrastructure failure

Typical NOC approach:

~~~text
Detect
  ↓
Verify immediately
  ↓
Notify / escalate according to process
  ↓
Create or update incident
  ↓
Coordinate continuously
  ↓
Track updates and restoration
  ↓
Verify recovery
  ↓
RCA / post-incident process
~~~

For P1 incidents, follow the organization's emergency escalation process immediately.

## P2 - High

P2 commonly represents significant impact that requires prompt attention.

Possible examples:

- Important P2P service down
- Important ILL service unavailable
- Significant packet loss affecting a service
- Repeated link flapping affecting connectivity
- High-impact connectivity degradation

Generic handling:

- Verify quickly
- Create/update ticket
- Coordinate with the responsible team or ISP
- Track ETR
- Follow up according to the defined interval
- Escalate when required
- Verify restoration

## P3 - Medium

P3 generally represents moderate or limited impact.

Possible examples:

- Limited service degradation
- Intermittent connectivity affecting a smaller scope
- Non-critical link issue with redundancy available
- Persistent but lower-impact latency issue

Generic handling:

- Verify the issue
- Document findings
- Assign the appropriate team
- Track progress
- Follow the organization's SLA and escalation rules

## P4 - Low

P4 generally represents low-impact incidents, requests, or informational work.

Examples:

- Minor issue
- Information request
- Non-urgent monitoring observation
- Documentation-related task

P4 does not mean that the ticket can be ignored. It should still be tracked according to the applicable process.

## Factors Used to Determine Priority

### 1. Business Impact

Ask:

- Is a critical business function affected?
- Is the service completely unavailable?
- Is only a small portion of users affected?

### 2. Number of Affected Services

One service and multiple services may require different priorities.

### 3. Service Criticality

A critical production service may require faster response than a non-critical service.

### 4. Redundancy

If a backup path is working, the business impact may be lower than a complete loss of connectivity.

Do not automatically reduce priority just because redundancy exists. Follow the organization's rules.

### 5. Duration

A short transient event may have a different priority from a persistent outage.

### 6. Recurrence

Repeated incidents may require increased attention or a separate problem-management process.

### 7. Security or Operational Risk

Certain events may require urgent escalation even when user impact appears limited.

## Example Decision Scenarios

### Scenario 1 - Critical Site Completely Offline

~~~text
Impact: Entire critical site
Service: Network connectivity
Redundancy: Unavailable
Urgency: Immediate
Generic Priority: P1
~~~

The exact priority must be confirmed using the organization's incident matrix.

### Scenario 2 - Important Service Down With Significant Impact

~~~text
Impact: Important service
Service: P2P connectivity
Redundancy: Not available
Urgency: High
Generic Priority: P2
~~~

### Scenario 3 - Packet Loss With Limited Impact

~~~text
Impact: Limited
Service: Connectivity degraded
Urgency: Moderate
Generic Priority: P3
~~~

### Scenario 4 - Minor Non-Urgent Request

~~~text
Impact: Low
Urgency: Low
Generic Priority: P4
~~~

## Priority Is Not Based Only on the Technical Symptom

The same symptom can have different priorities.

Example:

~~~text
Link Down
~~~

Scenario A:
- Critical service
- No backup
- Many users affected

Possible priority: High/Critical

Scenario B:
- Non-critical service
- Backup path active
- No noticeable business impact

Possible priority: Lower

Therefore:

~~~text
Same Technical Symptom
        +
Different Business Impact
        =
Different Priority
~~~

## Severity and Priority Example

| Situation | Severity | Possible Priority |
|---|---|---|
| Major outage | Critical | P1 |
| Important service unavailable | High | P2 |
| Limited packet loss | Medium | P3 |
| Minor informational issue | Low | P4 |

These mappings are illustrative, not universal.

## SLA Awareness

SLA = **Service Level Agreement**.

An SLA may define targets such as:

- Response time
- Acknowledgement time
- Update frequency
- Restoration target
- Escalation timeline
- Resolution or closure requirements

Do not invent SLA values in a ticket.

If the SLA is defined internally, follow the approved SLA documentation.

## ETR and Priority

Priority and ETR are related but not the same.

Example:

~~~text
Priority: P2
Issue: Link Down
ETR: HH:MM
~~~

ETR tells us the expected restoration time.

Priority tells us how urgently the incident should be handled.

A missed ETR may trigger escalation according to the applicable process.

## Priority Escalation

Priority may need to change when impact increases.

Example:

~~~text
P3
 ↓
Impact increases
 ↓
P2
 ↓
Further major impact
 ↓
P1
~~~

Any priority change should be based on the organization's incident matrix and should be documented.

Example ticket update:

~~~text
YYYY-MM-DD HH:MM - Incident impact increased due to additional affected services.

Priority reviewed and escalated from P3 to P2 according to the applicable incident-management process.

Reason: <Confirmed impact>
~~~

## Priority Reduction

Priority can sometimes be reduced when the impact is reduced.

Example:

~~~text
YYYY-MM-DD HH:MM - Backup connectivity restored and business impact reduced.

Priority reviewed according to the applicable incident-management process.

Current Priority: P3
Reason: <Confirmed reduced impact>
~~~

Do not reduce priority simply because the incident has been open for a long time.

## Escalation Types

### Functional Escalation

The incident is moved to a team with the required technical expertise.

Examples:

- Network team
- ISP technical team
- Firewall team
- Infrastructure team

### Hierarchical Escalation

The incident is escalated to the appropriate management or escalation level because of:

- High business impact
- SLA risk
- Extended outage
- Missed ETR
- Major operational impact

### ISP Escalation

For provider-related incidents, escalation may occur through the ISP's defined support hierarchy.

Always follow the approved escalation matrix.

## When to Escalate

Escalation may be required when:

- Critical impact is confirmed
- SLA risk exists
- Previous ETR is exceeded
- Service remains unavailable
- The issue is recurring
- Required technical expertise is unavailable
- Business impact increases
- The defined escalation threshold is reached

Do not escalate based only on frustration or assumptions.

## Ticket Documentation

Whenever priority changes, record:

~~~text
Time:
Previous Priority:
New Priority:
Reason:
Confirmed Impact:
Action Taken:
Escalated To:
Next Update:
~~~

Example:

~~~text
Time: YYYY-MM-DD HH:MM
Previous Priority: P3
New Priority: P2
Reason: Additional service impact confirmed
Confirmed Impact: Multiple services affected
Action Taken: Escalation initiated
Escalated To: Network/ISP Technical Team
Next Update: HH:MM
~~~

## Priority Review Checklist

Before assigning or changing priority:

~~~text
[ ] Business impact identified
[ ] Number of affected services identified
[ ] Service criticality checked
[ ] Redundancy status checked
[ ] Duration considered
[ ] Recurrence considered
[ ] Applicable SLA checked
[ ] Organization's priority matrix checked
[ ] Priority documented
[ ] Required escalation completed
~~~

## Common Mistakes

### Choosing Priority Based Only on the Alert

An alert does not automatically determine business priority.

### Assuming Every Link Down Is P1

Link Down is a symptom. Determine the actual impact.

### Ignoring Redundancy

A backup path can change the operational impact, but only according to the approved process.

### Changing Priority Without Documentation

Always record why a priority changed.

### Confusing ETR With Priority

ETR is an expected restoration time. Priority describes urgency/impact handling.

### Inventing SLA Values

Use only approved SLA information.

### Escalating Without Evidence

Record the confirmed reason for escalation.

## Generic Priority Template

~~~text
Ticket: Ticket-XXXX
Issue: <Issue>
Service: <Service>

Impact:
<Who/what is affected>

Urgency:
<Why immediate or normal action is required>

Service Criticality:
<Critical / Important / Normal>

Redundancy:
<Available / Unavailable / Unknown>

Current Priority:
P1 / P2 / P3 / P4

Reason:
<Confirmed reason>

SLA:
<Reference approved SLA only>

ETR:
HH:MM

Escalation:
<Yes / No>

Next Update:
HH:MM
~~~

## Key Takeaways

- Severity describes the seriousness of the impact; priority determines how urgently the incident should be handled.
- Business impact matters as much as the technical symptom.
- The same network issue can have different priorities in different environments.
- P1/P2/P3/P4 definitions are organization-specific.
- Always use the approved priority matrix and SLA.
- Track ETR separately from priority.
- Document every priority change and escalation.
- Never assign or change priority based only on assumptions.
- Clear priority decisions help the NOC focus attention where it matters most.

## Related Topics

- NOC Ticketing Workflow
- Ticket Update and Closure Examples
- ISP Coordination Workflow
- ISP Call and Email Communication
- RCA
- Monitoring Logs and Documentation
- NOC Glossary

## Author

Mohamed Ashik

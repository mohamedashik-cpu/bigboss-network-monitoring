# ISP Coordination Workflow

## Overview

ISP coordination is a core NOC activity used when a network service requires investigation, restoration, status updates, or escalation from an Internet Service Provider.

A good ISP coordination process should be clear, professional, evidence-based, and properly documented.

This document covers a generic ISP coordination workflow applicable to services such as ILL, P2P, and other ISP-supported connectivity.

> Important: All examples are generic and sanitized. Do not publish customer details, real circuit IDs, production IP addresses, ticket numbers, contact details, or company-confidential information.

## Objectives

- Understand when ISP coordination is required
- Prepare technical information before contacting the ISP
- Choose the appropriate communication channel
- Raise clear incidents
- Follow up effectively
- Track ETA and ETR
- Escalate delayed incidents
- Document ISP responses
- Verify restoration
- Maintain proper shift handover

## When to Contact the ISP

ISP coordination may be required when:

- A service remains down after basic local checks.
- A service is repeatedly flapping.
- Packet loss appears to be service-path related.
- Latency is abnormally high and local checks do not identify the cause.
- The ISP needs to investigate its network or last-mile/service path.
- A circuit requires planned maintenance information.
- An existing ISP incident needs status or ETR.
- A previous ETR has been missed.
- A recurring issue requires further ISP investigation.

Do not contact the ISP without first performing the checks required by the organization's procedure.

## ISP Coordination Workflow

~~~text
Issue / Requirement
        |
        v
Verify Internally
        |
        v
Collect Relevant Details
        |
        v
Choose Communication Channel
        |
        v
Contact / Raise Ticket
        |
        v
Record ISP Reference
        |
        v
Track Status + ETA/ETR
        |
        +---- Resolved ----> Verify Internally
        |
        +---- Not Resolved -> Follow Up
                                  |
                                  v
                              Escalate
                                  |
                                  v
                              Restore
                                  |
                                  v
                              Close
~~~

## 1. Verify Internally Before Contacting ISP

Before contacting the ISP, collect enough evidence to explain the issue.

Typical checks may include:

- Monitoring alert status
- Detection time
- Device reachability
- Interface status
- Interface errors
- Packet loss
- Latency
- Link flapping
- Relevant device logs
- Related alerts
- Previous incident history

The exact checks depend on the issue and the organization's SOP.

## 2. Information to Prepare

Before making a call or raising a ticket, prepare:

| Information | Example |
|---|---|
| Service Type | ILL / P2P |
| Issue | Link Down |
| Detection Time | YYYY-MM-DD HH:MM |
| Current Status | Down |
| Service Reference | Service-XXXX |
| Endpoint | Endpoint-A |
| Interface | Interface-X |
| Verification | Basic checks completed |
| Observation | Link remains down |
| Request | Investigation required |
| ISP Reference | To be provided |
| ETA / ETR | To be provided |

Only authorized real identifiers should be used in production communication.

## 3. Choosing the Communication Channel

Use the channel defined by the ISP and organization.

### Email

Useful when:

- A written record is required.
- Technical details need to be shared.
- Ticket history needs to be maintained.
- Multiple teams need visibility.

### Support Call

Useful when:

- Immediate assistance is required.
- A critical service is down.
- A ticket needs urgent attention.
- Email response is delayed.

### ISP Portal

Useful when:

- The ISP requires portal-based incident creation.
- Ticket status needs to be tracked online.
- Updates and attachments must be recorded through the portal.

Use the organization's approved channel and escalation procedure.

## 4. Initial ISP Communication

The first communication should clearly state:

1. Who you are / NOC team identification.
2. Service type.
3. Issue.
4. Detection time.
5. Important technical observations.
6. Checks already completed.
7. Required action.
8. Request for ticket/reference.
9. Request for ETA/ETR where applicable.

Avoid unnecessary explanations or assumptions.

## 5. Generic Initial Call Script

~~~text
Hello, this is the NOC team.

We are observing an issue with a P2P service.

The link has been down since approximately YYYY-MM-DD HH:MM.
We have completed the basic device and interface checks, and the issue is still present.

Could you please check the service and raise an incident if required?

Please provide the ISP ticket/reference number and the latest ETR.
~~~

For an ILL incident, replace the service type with ILL and provide the relevant approved service reference.

## 6. If the ISP Asks for More Details

Provide only the information required through the approved communication channel.

Useful information may include:

- Detection time
- Service type
- Service reference
- Endpoint information
- Interface status
- Ping/reachability result
- Packet-loss observation
- Latency observation
- Monitoring status
- Troubleshooting already completed

Do not provide credentials, passwords, or unrelated confidential information.

## 7. Recording the ISP Ticket

Once the ISP creates the incident, record:

~~~text
Service: P2P-Service-XXXX
Issue: Link Down
ISP: Generic-ISP
ISP Ticket: ISP-Ticket-XXXX
Status: Open / Investigation
ETR: Pending
Last Update: YYYY-MM-DD HH:MM
Next Follow-up: YYYY-MM-DD HH:MM
~~~

Use the organization's approved incident management system for real data.

## 8. Follow-up Process

ISP follow-up should be consistent rather than random.

During each follow-up:

1. Confirm the ISP ticket reference.
2. State that the issue is still being monitored.
3. Ask for the latest status.
4. Ask whether a fault has been identified.
5. Ask for current ETA/ETR.
6. Ask for the next expected update.
7. Record the response.

Generic follow-up:

~~~text
Hello Team,

This is a follow-up regarding ISP ticket ISP-Ticket-XXXX.

The service is still showing the reported issue on our monitoring.

Could you please provide the latest investigation status and current ETR?

Regards,
NOC Team
~~~

## 9. ETA vs ETR

### ETA - Estimated Time of Arrival

Generally refers to the expected arrival or availability of a person, team, resource, or action.

Example:

~~~text
Field engineer ETA: 15:30
~~~

### ETR - Estimated Time of Restoration

Refers to the estimated time by which the affected service is expected to be restored.

Example:

~~~text
ETR: 16:00
~~~

Always use the terminology according to the organization's communication process.

## 10. Tracking ETR

When an ETR is received:

- Record the ETR.
- Continue monitoring the service.
- Follow up before or around the expected restoration point according to the SOP.
- If the ETR is missed, request an updated status and revised ETR.
- Escalate if the approved threshold is reached.

Example:

~~~text
ETR Received: 16:00
16:00 - Service still down
16:05 - ISP follow-up
16:10 - Revised ETR requested
16:15 - Escalation initiated if required
~~~

## 11. Escalation

Escalation should follow the organization's defined hierarchy.

Possible escalation conditions:

- Critical service remains down.
- ETR has been missed.
- ISP response is delayed.
- Repeated follow-ups produce no progress.
- The incident has significant operational impact.
- The issue is recurring.
- The ISP investigation requires a higher support level.

Generic escalation flow:

~~~text
NOC
 |
 v
ISP Support
 |
 v
ISP Technical Team
 |
 v
ISP Escalation Team
 |
 v
Higher Support / Management
~~~

The actual escalation path depends on the ISP and service agreement.

## 12. Escalation Communication

Keep escalation messages factual.

Example:

~~~text
Hello Team,

The affected service is still down and the previously provided ETR has been exceeded.

ISP Ticket: ISP-Ticket-XXXX
Issue Start: YYYY-MM-DD HH:MM
Previous ETR: YYYY-MM-DD HH:MM
Current Status: Service still unavailable

Please escalate the incident to the concerned technical team and provide the revised ETR.

Regards,
NOC Team
~~~

Do not use aggressive or unclear language.

## 13. ISP Response Documentation

Record important ISP responses such as:

- Ticket created
- Engineer assigned
- Fault identified
- Field visit required
- Remote troubleshooting in progress
- Maintenance activity identified
- ETR provided
- ETR revised
- Service restored
- RCA pending

Example:

| Time | ISP Update | NOC Action |
|---|---|---|
| HH:MM | Ticket created | Reference recorded |
| HH:MM | Investigation started | Monitoring continued |
| HH:MM | ETR provided | ETR tracked |
| HH:MM | ETR revised | Follow-up scheduled |
| HH:MM | Service restored | NOC verification |
| HH:MM | Final update | Incident closure |

## 14. Restoration Verification

An ISP saying “service restored” is not by itself enough to close the incident.

Verify:

- Monitoring alert cleared
- Endpoint reachable
- Interface operational
- Packet loss normal where applicable
- Latency normal where applicable
- No repeated flapping
- Service remains stable

Generic verification:

~~~text
ISP Status: Restored
Monitoring: Normal
Reachability: Successful
Interface: Up / Up
Packet Loss: No abnormal loss observed
Latency: Within expected observation
Stability: Monitoring continued
~~~

## 15. Post-Restoration Monitoring

After restoration:

- Continue monitoring.
- Check for recurring alerts.
- Watch for flapping.
- Check packet loss where relevant.
- Check latency where relevant.
- Record the restoration time.
- Update the internal incident.
- Confirm whether RCA is required.

A short period of stability monitoring can help identify an immediate recurrence.

## 16. Shift Handover

If an ISP incident remains open at shift change, the handover should include:

- Service type
- Issue
- Detection time
- Current status
- ISP name/reference
- Latest ISP update
- ETR
- Last follow-up
- Next follow-up
- Escalation status
- Actions already completed

Generic handover:

~~~text
Service: P2P-Service-XXXX
Issue: Link Down
ISP Ticket: ISP-Ticket-XXXX
Status: ISP Investigation
ETR: YYYY-MM-DD HH:MM
Last Follow-up: YYYY-MM-DD HH:MM
Next Action: Follow up at agreed time
Escalation: In progress
Monitoring: Service still down
~~~

## 17. Common ISP Coordination Mistakes

### Contacting ISP Without Verification

**Problem:** The NOC cannot provide useful technical information.

**Better approach:** Perform the required local checks first.

### Not Recording Ticket Reference

**Problem:** Future follow-ups become difficult.

**Better approach:** Record the ISP reference immediately.

### Missing ETR

**Problem:** There is no clear restoration expectation.

**Better approach:** Request and record ETR whenever applicable.

### Not Tracking Follow-up

**Problem:** Open incidents may be forgotten during shift changes.

**Better approach:** Record last and next follow-up times.

### Closing Without NOC Verification

**Problem:** A service may appear restored temporarily.

**Better approach:** Verify monitoring, connectivity, interface status, and stability.

### Over-sharing Confidential Information

**Problem:** Sensitive company or customer data can be exposed.

**Better approach:** Share only the information required through approved channels.

## 18. Professional Communication Principles

When speaking or writing to an ISP:

- Be polite.
- Be concise.
- State facts clearly.
- Use exact timestamps.
- Avoid assumptions.
- Ask direct questions.
- Repeat important references when necessary.
- Record the response.
- Confirm the next action.
- Maintain professional language.

Useful phrases:

- “Could you please confirm the current status?”
- “Could you please provide the latest ETR?”
- “Has the fault been identified?”
- “Could you please confirm the next update time?”
- “The service is still showing down on our monitoring.”
- “The previous ETR has been exceeded. Could you please provide a revised ETR?”
- “Please escalate this to the concerned technical team.”

## 19. Generic ISP Coordination Checklist

### Before Contacting ISP

- [ ] Alert verified
- [ ] Issue identified
- [ ] Detection time recorded
- [ ] Basic troubleshooting completed
- [ ] Relevant technical details collected
- [ ] Appropriate communication channel selected

### During Initial Contact

- [ ] Service type stated
- [ ] Issue clearly explained
- [ ] Detection time provided
- [ ] Relevant checks explained
- [ ] ISP ticket/reference requested
- [ ] ETA/ETR requested

### During Follow-up

- [ ] ISP reference confirmed
- [ ] Current status checked
- [ ] Fault/update requested
- [ ] ETR checked
- [ ] Next update time confirmed
- [ ] Response documented

### During Escalation

- [ ] Previous ETR recorded
- [ ] Current status confirmed
- [ ] Impact understood
- [ ] Escalation path followed
- [ ] Revised ETR requested
- [ ] Escalation documented

### After Restoration

- [ ] ISP restoration confirmed
- [ ] Monitoring checked
- [ ] Reachability verified
- [ ] Interface verified
- [ ] Performance checked where relevant
- [ ] Stability monitored
- [ ] Internal incident updated
- [ ] RCA requirement checked

## 20. Confidentiality

Never publish:

- Customer names
- Real circuit IDs
- Production IP addresses
- ISP ticket numbers
- Internal ticket numbers
- Phone numbers
- Email addresses
- Credentials
- Monitoring screenshots containing real data
- Internal escalation contacts
- Contract or SLA details unless approved
- Company-confidential information

Use placeholders:

~~~text
Customer-Site-A
Service-XXXX
Ticket-XXXX
ISP-Ticket-XXXX
Generic-ISP
Endpoint-A
Interface-X
X.X.X.X
~~~

## Key Takeaways

- Verify the issue before contacting the ISP.
- Prepare concise technical evidence.
- Use the correct communication channel.
- Always record the ISP ticket/reference.
- Track status, ETA/ETR, and follow-up times.
- Escalate missed ETRs according to the approved process.
- Document important ISP responses.
- Verify restoration independently from the NOC side.
- Maintain proper shift handover.
- Protect customer, ISP, and company-confidential information.

## Related Topics

- ILL Monitoring and Troubleshooting
- ILL Ticket and ISP Follow-up Workflow
- P2P Monitoring and Troubleshooting
- P2P Ticket and ISP Follow-up
- Ticketing
- RCA
- Monitoring Logs and Documentation
- Shift Handover

## Author

Mohamed Ashik

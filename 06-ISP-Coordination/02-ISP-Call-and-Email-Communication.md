# ISP Call and Email Communication

## Overview

Clear communication is an important part of NOC operations. ISP calls and emails should communicate the issue quickly, provide the required technical information, and make the next action clear.

This document provides generic communication templates for common ISP coordination scenarios.

> Important: All examples are sanitized learning templates. Replace placeholders only inside approved company communication channels.

## Objectives

- Communicate ISP incidents clearly
- Improve confidence during technical calls
- Use short and professional sentences
- Ask for ticket references and ETR
- Handle follow-up calls
- Escalate missed ETRs
- Confirm restoration
- Document ISP responses

## Basic Communication Structure

A useful ISP communication can follow:

~~~text
Introduction
    ↓
Service Identification
    ↓
Issue
    ↓
Detection Time
    ↓
Verification Performed
    ↓
Request
    ↓
Ticket Reference
    ↓
ETA / ETR
    ↓
Next Follow-up
~~~

## 1. Basic ISP Call Opening

Use a simple opening:

~~~text
Hello, this is the NOC team.

We are calling regarding a network service issue.

Could you please assist us with the affected service?
~~~

If the ISP asks for more information, provide the approved service reference and issue details.

## 2. Link Down Call

~~~text
Hello, this is the NOC team.

We are observing a link-down issue for the affected service.

The issue started at approximately YYYY-MM-DD HH:MM.

We have completed the basic device and interface checks, and the service is still showing down on our monitoring.

Could you please investigate the issue and provide the ticket reference and ETR?
~~~

## 3. P2P Link Down Call

~~~text
Hello, this is the NOC team.

We are observing a P2P link-down issue.

The link has been down since approximately YYYY-MM-DD HH:MM.

Basic endpoint and interface checks have been completed from our side.

Could you please check the service and provide the ISP ticket number and current ETR?
~~~

## 4. ILL Link Down Call

~~~text
Hello, this is the NOC team.

We are observing an ILL link-down issue.

The issue started at approximately YYYY-MM-DD HH:MM.

We have completed the basic checks from our side, and the link is still showing down.

Could you please investigate and provide the ticket reference and ETR?
~~~

## 5. Asking for Ticket Reference

If the ISP has accepted the incident:

~~~text
Could you please provide the ISP ticket or reference number for this incident?
~~~

If the reference is difficult to understand:

~~~text
Could you please repeat the ticket number once?
~~~

For confirmation:

~~~text
Let me confirm the ticket number: ISP-Ticket-XXXX. Is that correct?
~~~

## 6. Asking for Current Status

During follow-up:

~~~text
Could you please confirm the current status of the ticket?
~~~

Alternative:

~~~text
Could you please provide the latest update on this incident?
~~~

If the ISP says the team is investigating:

~~~text
Understood. Could you please let us know if any fault has been identified?
~~~

## 7. Asking for ETR

~~~text
Could you please provide the current ETR for restoration?
~~~

If there is no ETR:

~~~text
Understood. Could you please provide the expected time for the next update?
~~~

This avoids repeatedly asking for an ETR when the ISP has not yet established one.

## 8. Previous ETR Has Passed

Stay professional:

~~~text
The previous ETR has been exceeded, and the service is still showing down on our monitoring.

Could you please provide the latest status and a revised ETR?
~~~

## 9. Escalation Call

~~~text
The service is still down and the previous ETR has been exceeded.

Could you please escalate this incident to the concerned technical team and provide the revised ETR?
~~~

If the issue is critical according to the organization's process:

~~~text
This service is currently unavailable and requires urgent attention.

Could you please escalate the incident and confirm the next update time?
~~~

Use urgency appropriate to the actual business impact. Do not exaggerate severity.

## 10. ISP Says "We Are Checking"

A professional response:

~~~text
Understood. Could you please confirm when we can expect the next update?
~~~

If an ETR is available:

~~~text
Thank you. Could you please also confirm the current ETR?
~~~

## 11. ISP Asks You to Reboot / Perform a Check

Confirm the requested action:

~~~text
Sure. We will perform the requested check and update you with the result.
~~~

After completing it:

~~~text
The requested check has been completed. The service is still showing the same issue.

Could you please proceed with further investigation?
~~~

Do not perform configuration changes or disruptive actions unless authorized.

## 12. ISP Says Service Is Restored

Do not immediately say the ticket can be closed.

Respond:

~~~text
Thank you for the update.

We will verify the service from our monitoring side and confirm the status.
~~~

After successful verification:

~~~text
The service is reachable and the monitoring status is normal.

We will continue monitoring for stability and proceed according to the closure process.
~~~

## 13. ISP Says "No Issue Found"

Respond with evidence:

~~~text
Understood.

The service is still showing the reported issue on our monitoring, and the basic checks from our side have been completed.

Could you please investigate further and confirm the next action?
~~~

Avoid arguing with the ISP. Keep the conversation evidence-based.

## 14. ISP Requests Technical Information

Provide only authorized information.

Example:

~~~text
The service type is P2P.
The issue started at YYYY-MM-DD HH:MM.
The interface is currently showing the reported state.
Basic reachability and interface checks have been completed.
~~~

Do not share passwords, credentials, or unrelated confidential information.

## 15. Call Ending

Before ending the call, confirm the important details:

~~~text
Before we close the call, could you please confirm the ticket number, current status, and next update time?
~~~

Then repeat:

~~~text
Thank you. I have noted the ticket number and next follow-up time.
~~~

## 16. Short Emergency Call Version

When time is limited:

~~~text
Hello, this is the NOC team.

We have a P2P/ILL link-down issue since YYYY-MM-DD HH:MM.

Basic checks are completed and the service is still down.

Please investigate and provide the ticket number and ETR.
~~~

## 17. ISP Email - Initial Incident

~~~text
Subject: P2P Link Down - Investigation Required

Hello Team,

We are observing a P2P link-down issue for the affected service.

Service Type: P2P
Issue: Link Down
Issue Start Time: YYYY-MM-DD HH:MM
Current Status: Down
Verification: Basic endpoint and interface checks completed

Please investigate the issue and provide the ISP ticket/reference number along with the current status and ETR.

Regards,
NOC Team
~~~

## 18. ISP Email - ILL Incident

~~~text
Subject: ILL Link Down - Investigation Required

Hello Team,

We are observing an ILL link-down issue for the affected service.

Service Type: ILL
Issue: Link Down
Issue Start Time: YYYY-MM-DD HH:MM
Current Status: Down
Verification: Basic device and interface checks completed

Please investigate and provide the ISP ticket/reference number and ETR.

Regards,
NOC Team
~~~

## 19. ISP Email - Follow-up

~~~text
Subject: Follow-up - ISP Ticket ISP-Ticket-XXXX

Hello Team,

This is a follow-up regarding ISP ticket ISP-Ticket-XXXX.

The service is still showing the reported issue on our monitoring.

Could you please provide the latest investigation status and current ETR?

Regards,
NOC Team
~~~

## 20. ISP Email - Missed ETR

~~~text
Subject: ETR Exceeded - ISP Ticket ISP-Ticket-XXXX

Hello Team,

The previously provided ETR for ISP ticket ISP-Ticket-XXXX has been exceeded, and the service is still showing down on our monitoring.

Previous ETR: YYYY-MM-DD HH:MM
Current Status: Service still unavailable

Please provide the latest status and revised ETR. Kindly escalate the incident to the concerned technical team if required.

Regards,
NOC Team
~~~

## 21. ISP Email - Escalation

~~~text
Subject: Escalation Required - ISP Ticket ISP-Ticket-XXXX

Hello Team,

The affected service remains unavailable and the expected restoration timeline has been exceeded.

ISP Ticket: ISP-Ticket-XXXX
Issue Start Time: YYYY-MM-DD HH:MM
Previous ETR: YYYY-MM-DD HH:MM
Current Status: Service still unavailable

Please escalate this incident to the concerned technical team and provide the revised ETR and next update time.

Regards,
NOC Team
~~~

## 22. ISP Email - Restoration Verification

~~~text
Subject: Service Restoration - ISP Ticket ISP-Ticket-XXXX

Hello Team,

We have received the restoration update for ISP ticket ISP-Ticket-XXXX.

Our monitoring indicates that the service is currently reachable and the alert has cleared.

We will continue monitoring the service for stability and proceed with the closure process as applicable.

Regards,
NOC Team
~~~

## 23. ISP Email - Additional Information

~~~text
Subject: Additional Information - ISP Ticket ISP-Ticket-XXXX

Hello Team,

Please find the requested information below:

Service Type: P2P / ILL
Issue: Link Down / Flapping / Packet Loss / High Latency
Issue Start Time: YYYY-MM-DD HH:MM
Current Status: <Status>
Verification Completed: <Checks performed>

Please continue the investigation and provide the latest status and ETR.

Regards,
NOC Team
~~~

## 24. Communication When English Confidence Is Low

Do not try to use complicated English.

Use short sentences:

~~~text
The link is down.
The issue started at 10:30.
We completed the basic checks.
The link is still down.
Please check the issue.
Please provide the ticket number.
Please provide the ETR.
The previous ETR has passed.
Please provide a revised ETR.
The service is restored.
We are verifying from our side.
~~~

Clear English is more important than complex English in a NOC call.

## 25. Important Call Phrases

| Situation | Phrase |
|---|---|
| Ask status | “Could you please confirm the current status?” |
| Ask ticket | “Could you please provide the ticket number?” |
| Ask ETR | “Could you please provide the current ETR?” |
| Ask fault | “Has the fault been identified?” |
| Ask update time | “When can we expect the next update?” |
| ETR missed | “The previous ETR has been exceeded.” |
| Request escalation | “Could you please escalate this incident?” |
| Confirm number | “Let me confirm the ticket number.” |
| Need repetition | “Could you please repeat that once?” |
| Need spelling | “Could you please spell that?” |
| Restoration | “We will verify from our monitoring side.” |

## 26. Call Documentation Template

Immediately after a call, record:

~~~text
Date:
Time:
ISP:
Service:
Issue:
ISP Ticket:
Person/Team Contacted:
Current Status:
ETR:
Next Follow-up:
Escalation:
Remarks:
~~~

Example:

~~~text
Date: YYYY-MM-DD
Time: HH:MM
ISP: Generic-ISP
Service: P2P-Service-XXXX
Issue: Link Down
ISP Ticket: ISP-Ticket-XXXX
Person/Team Contacted: ISP Support
Current Status: Investigation
ETR: HH:MM
Next Follow-up: HH:MM
Escalation: No
Remarks: ISP technical team investigating
~~~

## 27. Communication Mistakes to Avoid

### Speaking Too Fast

Speak slowly enough for the ISP engineer to understand.

### Using Long Explanations

Start with the issue and important facts. Provide additional details only when requested.

### Guessing Technical Information

If you do not know something:

~~~text
Let me verify that information and get back to you.
~~~

### Forgetting the Ticket Number

Repeat and record the ticket number before ending the call.

### Not Asking for the Next Action

Always know what happens next:

~~~text
Could you please confirm the next update time?
~~~

### Closing Without Verification

Never confirm complete recovery only because the ISP says it is restored.

## 28. Confidentiality

Never publish:

- Customer names
- Real service/circuit IDs
- Production IP addresses
- ISP ticket numbers
- Internal ticket numbers
- Phone numbers
- Email addresses
- Credentials
- Monitoring screenshots containing real data
- Internal escalation contacts
- Company-confidential information

Use placeholders:

~~~text
Customer-Site-A
P2P-Service-XXXX
ILL-Service-XXXX
Ticket-XXXX
ISP-Ticket-XXXX
Generic-ISP
X.X.X.X
~~~

## Key Takeaways

- Keep ISP communication short and factual.
- State the issue, time, checks, and required action clearly.
- Always obtain and record the ISP ticket reference.
- Track ETR and the next follow-up time.
- Use simple English during calls.
- Ask the ISP to repeat or spell information when necessary.
- Document every important communication.
- Verify restoration from the NOC side.
- Never share confidential production information in public documentation.

## Related Topics

- ISP Coordination Workflow
- P2P Monitoring and Troubleshooting
- P2P Ticket and ISP Follow-up
- ILL Monitoring and Troubleshooting
- Ticketing
- Email Templates
- Monitoring Logs and Documentation
- Shift Handover

## Author

Mohamed Ashik

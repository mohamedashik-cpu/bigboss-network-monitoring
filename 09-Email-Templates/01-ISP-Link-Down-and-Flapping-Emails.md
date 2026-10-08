# ISP Email Templates — Link Down and Link Flapping

This guide contains reusable email formats for the two common ISP coordination scenarios handled in NOC operations:

1. Link Down
2. Link Flapping

Use the appropriate template and replace the placeholders with verified incident details before sending. Follow the company's approved communication process.

> **Confidentiality:** This is a public learning repository. Never commit real circuit IDs, customer details, internal IP addresses, ticket/reference numbers, monitoring screenshots, or other company-confidential information. Use actual operational details only in the approved work email or ticketing system.

---

## 1. Generic Link Down Email

**Subject:** [P2P/ILL] [Bandwidth] Mbps Link Down — Request for Immediate Resolution

Dear [ISP] Team,

This is to inform you that our [P2P/ILL] [Bandwidth] Mbps [Fiber Link] at [Location] is currently **Down**.

Request you to kindly check and resolve the issue on a priority basis.

**Circuit ID:** [Circuit ID]

Kindly investigate the issue and restore the link at the earliest. Please share the ticket/reference number and expected time of restoration (ETR).

Regards,  
Mohamed Ashik

---

## 2. Generic Link Flapping Email

**Subject:** [P2P/ILL] [Bandwidth] Mbps Link Flapping — Request for Immediate Resolution

Dear [ISP] Team,

This is to inform you that our [P2P/ILL] [Bandwidth] Mbps [Fiber Link] at [Location] is experiencing **Link Flapping**.

Request you to kindly investigate the issue and resolve it on a priority basis.

**Circuit ID:** [Circuit ID]

Kindly check the link stability and take the necessary action to prevent further flapping. Please share the ticket/reference number and expected time of restoration (ETR).

Regards,  
Mohamed Ashik

---

## 3. Link Details Reference

Use this table only to select the correct generic link category and bandwidth. Confirm the actual circuit and location in the approved internal system before sending an email.

| ISP | Link Type | Bandwidth |
|---|---|---|
| Jio | P2P | 150 Mbps |
| Jio | ILL | 150 Mbps |
| Jio | ILL | 50 Mbps |
| TCL (Tata) | P2P | 150 Mbps |
| Pulse | P2P | 100 Mbps |
| ACT | ILL | 100 Mbps |

---

## 4. Filling the Template

Replace each placeholder with verified information:

- **[ISP]:** Correct provider name, such as Jio, TCL (Tata), Pulse, or ACT.
- **[P2P/ILL]:** Correct link type.
- **[Bandwidth]:** Correct circuit bandwidth.
- **[Fiber Link]:** Keep this wording only if it accurately describes the circuit.
- **[Location]:** The approved site/location name.
- **[Circuit ID]:** Exact circuit ID from the approved internal source.

Before sending, double-check that the link type, bandwidth, location, and circuit ID all refer to the same circuit.

## 5. Down vs Flapping

| Issue | Wording to Use | Meaning |
|---|---|---|
| Link Down | “is currently Down” | The link is unavailable at the time of verification |
| Link Flapping | “is experiencing Link Flapping” | The link repeatedly changes between up and down |

Do not describe a link as Down or Flapping without checking the current monitoring status and available event history.

## 6. Before Sending Checklist

- [ ] Confirm the alert and current link status
- [ ] Confirm ISP and P2P/ILL type
- [ ] Confirm bandwidth and location
- [ ] Verify the circuit ID in the approved internal system
- [ ] Use the correct Down or Flapping template
- [ ] Ask for the ISP ticket/reference number
- [ ] Request an ETR when appropriate
- [ ] Follow the organization's escalation process
- [ ] Check recipients and email wording
- [ ] Keep confidential details out of public documentation

## Key Takeaways

- Use one of the two templates according to the verified issue.
- Replace all placeholders before sending.
- Request the ISP reference number and ETR when appropriate.
- Keep the email clear, factual, and professional.
- Never store real circuit IDs or customer/production details in this public repository.

---

## Author

**Mohamed Ashik**

Network Monitoring | NOC | ISP Coordination | Networking | Cloud Security Learning

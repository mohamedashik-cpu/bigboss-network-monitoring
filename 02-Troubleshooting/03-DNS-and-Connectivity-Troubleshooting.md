# DNS and Connectivity Troubleshooting

## Overview

Connectivity problems do not always indicate a complete network outage. A user or service may be reachable by IP address while hostname resolution fails, or the local device may have a gateway or DNS configuration problem.

In NOC operations, the goal is to identify whether the issue is related to local connectivity, gateway reachability, DNS resolution, or the upstream network path.

This document uses only generic and sanitized examples.

## Objectives

- Differentiate basic connectivity issues from DNS issues
- Verify local IP configuration
- Check default gateway reachability
- Test connectivity using an IP address
- Test hostname resolution
- Use basic Windows network troubleshooting commands
- Identify when escalation is required
- Document and verify recovery

## Basic Troubleshooting Flow

```
Connectivity Issue
       |
       v
Check Local IP Configuration
       |
       v
Check Default Gateway
       |
       v
Ping Known IP Address
       |
       +---- IP Works ----> Test Hostname / DNS
       |
       +---- IP Fails -----> Check Local / Upstream Connectivity
       |
       v
Run DNS Checks
       |
       v
Check Network Path
       |
       v
Identify Scope
       |
       +---- Local Issue
       |
       +---- DNS Issue
       |
       +---- Upstream / ISP Issue
       |
       v
Escalate / Troubleshoot
       |
       v
Verify Recovery
```

## 1. Check Local IP Configuration

On a Windows system:

```text
ipconfig
```

For detailed information:

```text
ipconfig /all
```

Check:

- IPv4 address
- Subnet mask
- Default gateway
- DNS servers
- DHCP status where applicable

A missing or incorrect default gateway can prevent communication outside the local network.

## 2. Check Default Gateway

Use:

```text
ping <default-gateway>
```

Generic example:

```text
ping 10.x.x.1
```

Possible results:

- Gateway responds → local connectivity may be working
- Gateway does not respond → investigate local network connectivity
- Intermittent replies → possible instability or packet loss

A failed gateway ping does not always prove the gateway is down because ICMP may be filtered.

## 3. Test Connectivity Using an IP Address

Test a permitted destination by IP:

```text
ping X.X.X.X
```

If the IP address responds, basic IP connectivity to that destination may be available.

If the IP does not respond, investigate:

- Local connectivity
- Default gateway
- Routing/path
- Destination availability
- ICMP filtering

## 4. Test Hostname Resolution

Use:

```text
nslookup example.com
```

The command can help determine whether a DNS server is resolving the requested hostname.

Generic successful result:

```text
Server:  DNS-Server
Address: X.X.X.X

Name:    example.com
Address: X.X.X.X
```

Possible observations:

- Hostname resolves successfully
- DNS server does not respond
- Requested name does not exist
- Response is delayed or times out

Do not copy real internal DNS server names or addresses into a public repository.

## 5. IP Ping vs Hostname Ping

A useful troubleshooting comparison is:

```text
ping X.X.X.X
ping example.com
```

### IP Works + Hostname Fails

This can indicate a DNS resolution problem.

Check:

```text
ipconfig /all
nslookup example.com
```

### IP Fails + Hostname Fails

This suggests a broader connectivity/path problem may exist, but the exact cause needs further investigation.

### Both Work

Basic connectivity and DNS resolution appear functional for the tested destination at that moment.

## 6. Check DNS Configuration

Use:

```text
ipconfig /all
```

Identify the configured DNS servers.

If the DNS configuration appears incorrect, follow the organization's approved configuration and escalation process rather than changing production settings without authorization.

## 7. Clear Local DNS Cache

When authorized for endpoint troubleshooting, Windows provides:

```text
ipconfig /flushdns
```

This clears the local DNS resolver cache.

After clearing the cache, test resolution again:

```text
nslookup example.com
```

Do not use configuration-changing commands on managed production systems unless permitted by the organization's procedures.

## 8. Check the Network Path

On Windows:

```text
tracert X.X.X.X
```

A route trace can provide information about the path toward a destination.

Possible observations:

- Path completes normally
- One or more hops do not respond
- Increased delay appears at a particular point
- Path changes between tests

A non-responsive hop does not automatically mean that hop is faulty. Some routers intentionally do not respond to traceroute probes.

## 9. Identify the Scope

Determine whether the problem affects:

### Single Device

Possible areas:

- Local IP configuration
- DNS configuration
- Network adapter
- Local connectivity

### Multiple Devices

Possible areas:

- LAN/uplink
- Gateway
- DNS service
- Shared network path
- WAN/ISP connectivity

### Multiple Sites or Links

Possible areas:

- Shared upstream service
- Common provider
- Central network service
- Monitoring/platform issue

Scope helps determine the appropriate escalation path.

## 10. Local vs DNS vs ISP Indicators

### Possible Local Connectivity Indicators

- Incorrect IP configuration
- Missing default gateway
- Gateway unreachable
- Network adapter issue
- Local link problem

### Possible DNS Indicators

- IP connectivity works
- Hostname resolution fails
- DNS server does not respond
- DNS query returns an error

### Possible Upstream / ISP Indicators

- Local gateway is reachable
- Local configuration appears correct
- External IP connectivity is affected
- Multiple destinations show similar symptoms
- ISP investigation is required

These are indicators only. Root cause should be established using available evidence.

## 11. Generic Incident Example

**Scenario:** A workstation cannot access a service by hostname.

**Step 1:** Check local IP configuration.

```text
ipconfig /all
```

**Step 2:** Ping the default gateway.

```text
ping <default-gateway>
```

**Step 3:** Test the service using its permitted IP address.

```text
ping X.X.X.X
```

**Step 4:** Test hostname resolution.

```text
nslookup example.com
```

**Step 5:** If required and authorized, clear the local DNS cache.

```text
ipconfig /flushdns
```

**Step 6:** Test the hostname again.

**Step 7:** If the issue remains, check the network path and determine the appropriate escalation.

**Step 8:** Document the tests and results in the approved ticketing system.

## 12. Ticket Documentation

A useful ticket update should contain:

- Issue start time
- Affected service/device
- Connectivity test result
- Gateway test result
- DNS test result
- Path test result when required
- Troubleshooting performed
- Current status
- Escalation status
- Next follow-up time

Keep updates factual and timestamped.

Never publish real customer information, production IPs, DNS addresses, ticket numbers, or contact details in this repository.

## Restoration Verification

After the issue is reported as resolved:

1. Verify the device has valid network configuration.
2. Test the default gateway.
3. Test the required destination by IP where appropriate.
4. Test hostname resolution.
5. Test the affected application/service if authorized.
6. Continue monitoring for recurrence.
7. Update the ticket with the verification results.

## Troubleshooting Checklist

- [ ] IP configuration checked
- [ ] Default gateway checked
- [ ] Gateway reachability tested
- [ ] IP connectivity tested
- [ ] Hostname resolution tested
- [ ] DNS configuration checked
- [ ] DNS cache considered
- [ ] Network path checked when required
- [ ] Scope of impact identified
- [ ] Local/DNS/upstream possibilities considered
- [ ] Ticket updated
- [ ] Escalation completed when required
- [ ] Recovery verified
- [ ] Stability monitored

## Important NOC Practices

- Separate DNS problems from general connectivity problems.
- Use IP and hostname tests together when appropriate.
- Do not assume a non-responsive traceroute hop is automatically faulty.
- Do not change production configuration without authorization.
- Record exact test results and timestamps.
- Escalate with evidence rather than assumptions.
- Verify service recovery before closure.
- Protect customer and internal network information.

## Confidentiality

Do not upload:

- Customer names
- Real production IP addresses
- Internal DNS addresses
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
DNS-Server
X.X.X.X
Generic-ISP
Ticket-XXXX
```

## Key Takeaways

- Connectivity and DNS are separate troubleshooting areas.
- IP testing and hostname testing can help narrow the problem.
- Default gateway checks help validate local connectivity.
- `nslookup` is useful for DNS verification.
- `tracert` can provide path information but must be interpreted carefully.
- Troubleshooting should be based on evidence and scope.
- Recovery should be verified before closing an incident.

## Related Topics

- Link Down Troubleshooting
- Packet Loss and High Latency Troubleshooting
- Basic Monitoring Workflow
- Alert Verification and Classification
- Cisco Troubleshooting Commands
- ISP Coordination
- Ticketing

## Author

Mohamed Ashik

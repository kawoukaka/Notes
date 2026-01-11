# BGP and Peering

## Core Topics
- BGP route announcements and path selection.
- Peering vs transit relationships.
- Route leaks and misconfiguration risks.

## Senior mindset
- Multi-homing improves resilience but adds complexity.
- Monitor route changes and propagation delays.
- Use RPKI and filtering to reduce hijack risks.

## Hands-on Commands and Examples
- `whois <prefix>`: identify ASN and route owners.
- `mtr -T <host>`: TCP-based path check (useful if ICMP blocked).
- `traceroute -A <host>`: show AS path where supported.

## Troubleshooting Checklist
- Confirm scope: single host, AZ, region, or global.
- Validate DNS and routing first.
- Check latency, loss, and retransmits.
- Verify firewall/security group changes.
- Correlate with recent deploys or config changes.

## Example Outputs
- `ping`: packet loss and avg latency.
- `traceroute`: hops where latency spikes.
- `ss -s`: TCP state summary with retransmits.

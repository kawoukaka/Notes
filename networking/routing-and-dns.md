# Routing and DNS

## Routing
- Static vs dynamic routing; route propagation matters in multi-region.
- BGP is the backbone of internet routing; understand failure modes.
- NAT and SNAT implications on source identity.

## DNS
- TTL settings balance freshness vs cache load.
- Split-horizon DNS for internal vs external views.
- Understand CNAME vs A/AAAA implications.

## Senior mindset
- DNS is often the hidden root cause; always check resolution paths.
- Use health-checked DNS for failover but test propagation delays.

## Hands-on Commands and Examples
- `ip route`: inspect local routing table.
- `ip rule`: check policy routing rules.
- `dig <host> +trace`: DNS resolution path and delegation.
- `dig <host> @<dns_server>`: query a specific resolver.
- `nslookup <host>`: quick DNS lookup (legacy but common).

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

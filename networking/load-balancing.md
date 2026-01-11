# Load Balancing

## Types
- L4 (transport) vs L7 (application) load balancing.
- Round-robin vs least-connections vs consistent hashing.
- Global load balancing across regions.

## Senior mindset
- Consider stateful vs stateless services when choosing strategies.
- Health checks should validate dependency chains, not just process liveness.
- Session affinity can hide scaling issues; use sparingly.

## Hands-on Commands and Examples
- `curl -I <url>`: verify headers and caching behavior.
- `curl -v <url>`: observe redirects, TLS, and response codes.
- `hey -n 1000 -c 50 <url>`: load test a service endpoint.
- `wrk -t4 -c100 -d30s <url>`: load test with latency stats.

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
